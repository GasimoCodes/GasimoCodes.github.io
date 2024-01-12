---
author: "Gasimo"
title: "Tech behind Ječná Part 3: Subtitles"
date: 2023-11-20
tags: ["Nightshift", "Tech"]
thumbnail: https://img.itch.zone/aW1hZ2UvMjMzMDgxNy8xMzgyMDIzOC5wbmc=/500x/ZJw6LR.png
---

Hello everyone! Welcome to today's devtalk! In this session, we'll be delving into the fascinating realm of subtitles.

## Subtitler
![](https://img.itch.zone/aW1nLzE0MDgyODA5LnBuZw==/original/Qj9uek.png)
The entirety of my subtitle system (conveniently nicknamed "Subtitler") is [open-source and available over at my github](https://github.com/GasimoCodes/Subtitler)!

During development, I quickly realized that some in-game dialogue may be hard to hear. Implementing a subtitle system was the most obvious solution. However, as the game scaled, it turned out to be a bit more complex than I initially anticipated.


### Defining the Data
Each piece of dialogue is stored as a file, leveraging Unity's [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html). These objects are basically data containers editable from the editor and directly parse into C# classes. The file includes an array of all spoken lines for a given dialogue and its timing data. I've also incorporated additional properties, which I'll discuss in more detail later.


### Playing and Displaying the Subtitles
Playing of subtitle files is handled by the [SubtitleManager](https://github.com/GasimoCodes/Subtitler/blob/main/Assets/Gasimo/com.gasimo.subtitler/Runtime/Scripts/SubtitlerUI.cs). Once a subtitle is requested to be played, it creates a new thread and plays the SubtitleData line by line while making pauses inbetween based on the file specification. For fancier UI animations, [DOTween](https://dotween.demigiant.com/) was utilized.

```
int playSubtitle(SubtitleData sD, AudioSource aS){...}
```

### A wild problem has appeared:
#### What if player goes away mid-dialogue?
It was apparent that seeing subtitles without being able to hear them was jarring. Thus before a line is played, I check the player distance from the audioSource and calculate whether its hearable based on volume, 3D mix, range and distance from the player.

```
 // If we are (range-limited, out of range AND not a 2D source) OR IF (the audioSource is not playing AND there was an valid AudioClip)
if ((isRangeLimited && !checkAudioDistance(aS.maxDistance, aS) && aS.spatialBlend != 0) || (aS.isPlaying == false && sE.audio != null))
{
    continue;
}
```

#### The numerous problems with the in-game radio tuner
The in-game radio tuner turned out to be a wildcard. I had to implement audio volume checks to determine whether the subtitle audio was audible. Another challenge arose when the player rapidly tuned in and out between lines, causing two subtitles to play simultaneously. I resolved this by generating a unique session ID for each played subtitleData, allowing me to terminate any session mid-play.

#### Events when player hears a certain line?
In Nightshift, I've incorporated events triggered by specific subtitles. These events range from displaying achievements to inducing a blackout in the backrooms. Since SubtitleData is confined to a file, direct references to runtime objects aren't possible. To address this, I employed a clever technique: I defined a new ScriptableObject with an <UnityAction> (Basically an abstraction for EventHandler). I can reference these in both the SubtitleDatas and runtime scripts. Now, I simply check if a playing line has a ScriptableObject (UnityAction) assigned to it and invoke it.

```
    [CreateAssetMenu(fileName = "ScriptableEvent", menuName = "Gasimo/ScriptableEvent")]
    [Serializable]
    public class ScriptableEvent : ScriptableObject
    {
        public delegate void ScriptableEventHandler();
        public event ScriptableEventHandler onEventRaised;

        public void Raise()
        {
            onEventRaised.Invoke();
        }

    }
```