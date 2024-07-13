# ttshandler
A Python library that provides a simple and intuitive API for seamless interfacing with text-to-speech libraries like **gtts** and **pyttsx3**.

## Features
* Combines the full potential of two popular Test-to-Speech libraries: **gtts** and **pyttsx3** into a single one.
* Strict enforcement of valid values for setting the speech properties supported by the respective APIs.
* Generate an audio output file for the text-to-speech.
* Generate a visual waveform of the text-to-speech audio.

## Dependencies
Most dependencies will be automatically installed if you install ttshandler from pip using the command:    
```pip3 install ttshandler```.

Dependencies include:
* ```pyttsx3```
* ```gtts```
* ```matplotlib```
* ```numpy```
* ```pydub```

Additionally, you also need ```ffmpeg``` pre-installed on your system. While ```ffmpeg``` is not directly
required for ttshandler, it is a basic requirement for ```pydub``` to work.   

Install ```ffmpeg``` using your package manager:
* On Debian/Ubuntu based systems with ```apt``` use the command: ```sudo apt install ffmpeg```
* For Arch Linux/systems with ```pacman``` use: ```sudo pacman -S ffmpeg```
* For other systems, get it from [here](https://www.ffmpeg.org/download.html).

After installing, add ```ffmpeg``` to the system's PATH variable. This process is not required if you
installed ```ffmpeg``` using your package manager.    


## Version Requirements
### Executables
* Python >= 3.8
* ```ffmpeg``` (latest version recommended)
### Python libraries
* ```gtts``` >= 2.5.1
* ```pyttsx3``` >= 2.90
* ```matplotlib``` >= 3.6.0
* ```numpy``` >= 1.24.0
* ```pydub``` >= 0.25.1

## Example code snippets
After installing ttshandler, you may run the following example code snippets:
### Example using pyttsx3
```
>>> import ttshandler as ttsh
>>> tts = ttsh.TTSHandler(text="Hello world", api="pyttsx3")
>>> tts.generate_tts("tts_pyttsx3.wav")
>>> tts.generate_waveform("waveform_pyttsx3.png")
```
If no errors are generated, you will have two files in your current working directory that contain
the text-to-speech audio clip generated using ```pyttsx3``` and the audio waveform image, respectively.

### Example using gtts
```
>>> import ttshandler as ttsh
>>> tts2 = ttsh.TTSHandler(text="Hello world", api="gtts")    # Requires internet connection
>>> tts2.generate_tts("tts_gtts.mp3")
>>> tts2.generate_waveform("waveform_gtts.png")
```
```gtts``` requires internet connection. ttshandler will raise a ```GTTSConnectonError``` if ```gtts``` fails to connect to Google's text-to-speech API.


# Detailed documentation

## Directory structure of package ```ttshandler```
```
ttshandler/
    |
    |____    __init__.py
    |____    ttsexceptions.py
    |____    ttshandler.py
```

## Module ```__init__.py```
Imports the main module ```ttshandler.py```.

## Module ```ttsexceptions.py```
Exception that are raised from the TTSHandler class are defined here. These are:

```class UnknownAPIError(Exception)```
* Raised when the API specified while initializing TTSHandler is not one of 'pyttsx3' or 'gtts'.

```class TTSPropertyError(Exception)```
* Raised while attempting to set an invalid or unsupported property for an initialized API.

```class TTSNotGeneratedError(Exception)```
* Raised when attempting to generate a speech waveform before the TTS has been generated.

```class GTTSConnectionError(Exception)```
* Raised when ```gtts.tts.gTTSError``` is raised, which occurs mainly due to connection issues.

```class Pyttsx3InitializationError(Exception)```
* Raised when Pyttsx3 could not initialize the specified TTS engine.

```class NoFFmpegError(Exception)```
* Raised when FFmpeg is not installed, which is required for audio format conversions.

## Module ```ttshandler.py```

