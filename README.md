# Simple speech to text

The script will 'listen' to the microphone input and output text when it thinks it hears a phrase.

Adapted from the original by Jeyson Molina.

[https://github.com/jeysonmc/python-google-speech-scripts](https://github.com/jeysonmc/python-google-speech-scripts)

This version of the script does not utilise Google speech API due to the requirement for an API key and subscription to Google Cloud services. Instead it uses the SpeechRecognition library which supports Google's speech API, along with other free ones.

For more info see: [https://pypi.org/project/SpeechRecognition/](https://pypi.org/project/SpeechRecognition/)

Tested on Linux with Python 3.5.

Note: this script does not require the conversion of wavs to flac, but if you intend to adapt it for use with Google's API, you would need to do that (i.e. using the flac package).

## Requirements

+ PyAudio==0.2.11
+ SpeechRecognition==3.8.1

## How to use

+ First check your setup and make sure the default device is the one you want to use. If not you'll either need to modify your `.asoundrc` or `asound.conf` file (see [ALSA docs](https://www.alsa-project.org/wiki/Asoundrc)) or set the `input_device_index` parameter of the audio stream. 

If you're unsure what your default device is (or are having problems playing/recording), test the devices are recognised in the interactive shell:

		import pyaudio
		p = pyaudio.PyAudio() 
		p.get_device_count()

Assuming you have a number > 0, you can check which devices are detected:

		for i in range(p.get_device_count()):
			dev = p.get_device_info_by_index(i)
			print((i,dev['name'],dev['maxInputChannels'])) 

+ Once you are satisfied the devices are recognised and working, calibrate the silence `THRESHOLD` in the script (line 17) by calling the `audio_int()` function (i.e. uncomment line 155, comment line 153).
+ Edit and plug into your project as required!
