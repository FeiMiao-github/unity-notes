# Basic Theory

## problem

1. A listener can tell roughly which direction is coming from and may also get some sense of its distance from its loudness and quality.
2. A fast-moving sound source will change in pitch as it moves as a result of the the Doppler effect
3. The surroundings will affect the way sound is reflected, so a voice inside will have an echo but the same voice in the open air will not.

## solution

1. To **simulate the effects of position**, Unity require sounds to originate from **Audio Sources** attached to Object. The sounds emitted are then picked up by **Audio Listener** attached to another object.

2. The relative speed of the source and listener objects can also be used to simulate the Doppler Effect for added realism.

3. Unity can’t calculate echoes purely from **scene**
    geometry but you can simulate them by adding **Audio Filters**
    to objects

# Working with Audio Assets

Unity can import audio files in **AIFF**, **WAV**, **MP3** and **Ogg** formats 

# Audio Recording

Unity can access the computer’s microphones from a script and create Audio Clips by direct recording.



# Audio Files

Since Unity5.0 audio data is separated from **AudioClips**. The **AudioClips** merely refer to the files containing the audio data and there are various combinations of options in the AudioClip importer that determine how the clips are loaded at runtime.

# Tracker Modules

Trakcer Modules are essentially just packages of audio samples that have been modeled, arranged and sequenced programatically.

Tracker Module files are similar to MIDI files in many ways. **MIDI has a disadvantage in that sounds are dependent on the sound bank available in the audio hardware, so MIDI music can sound different on different computers.**

In contrast，tracker modules include high quality PCM samples that ensure a similar experience regardless of the audio hardware in use.

> **音乐数字接口**（Musical Instrument Digital Interface，简称**MIDI**）是一个工业标准的电子[通信协议](https://zh.wikipedia.org/wiki/通訊協定)，为电子乐器等演奏设备（如[合成器](https://zh.wikipedia.org/wiki/合成器)）定义各种音符或弹奏码，容许[电子乐器](https://zh.wikipedia.org/wiki/電子樂器)、[电脑](https://zh.wikipedia.org/wiki/電腦)、[手机](https://zh.wikipedia.org/wiki/手機)或其它的[舞台](https://zh.wikipedia.org/wiki/舞台)演出配备彼此连接，调整和同步，得以即时交换演奏资料。(https://zh.wikipedia.org/wiki/MIDI)

## Supported formats

Unity supports the four most common module file formats, namely Impulse Tracker (**.it**), Scream Tracker (**.s3m**), Extended Module File Format (**.xm**), and the original Module File Format (**.mod**).

## Benefits of Using Tracker Modules

Tracker module files differ from mainstream PCM formats (**.aif**, **.wav**, **.mp3**, and **.ogg**) in that they can be **very small without a corresponding loss of sound quality**.

## Audio mixer

The Unity Audio Mixer allows you to mix various audio sources, apply effects to them, and perform mastering(母版制作).

An Audio Mixer is an asset. You can create one or more Audio Mixer and have more than one active at any time.