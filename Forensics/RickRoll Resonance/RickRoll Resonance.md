# RickRoll Resonance
## Challenge Description
The challenge provides us with an audio file that uses the Waveform Audio File Format (i.e. wav file). Our hint goes as such
> I was downloading Never Gonna Give You Up, but instead, I got this bizarre audio file. At first, I thought it was corrupted, but there seems to be more to it. Something about the spectrum feels... off. Can you figure out the hidden message?

## Solution Walkthrough
As the hint suggests our flag has something to do with the spectrum of the audio file. So we'll create an audio spectogram in order to study it. We can do this using multiple online tolls. one such tool is [Audio Spectogram Creator](https://convert.ing-now.com/audio-spectrogram-creator/).

Using this and making some adjustments in the intensity or colour of the image to obtain a clearer one gives us this.

<img width="957" alt="image" src="https://github.com/user-attachments/assets/31e8c3f2-0799-4f62-ab7c-3b07bef7bbdb" />

the flag is very clearly visible in the spectogram!

## Flag
> WannaHack{y34H_17_w4s_345y_1G}
