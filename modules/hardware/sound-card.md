# Sound Card

The Sound Card module will allow you to have sound detection and playback. It has basic pitch detection and an FFT analysis module that allows to create frequency based volume detection.

{% hint style="info" %}
If you're using an audio layer in your sequences, you will need a Sound Card module to output the sound as there is no global audio settings.
{% endhint %}

{% hint style="success" %}
You can connect to multiple sound cards in the same project.
{% endhint %}

{% hint style="info" %}
For performance optimization, audio input, pitch detection and FFT analysis are disable. If you wish to do volume / pitch detection, you first have to setup Audio input. See parameters below for more informations.
{% endhint %}

![](../../.gitbook/assets/sound.png)

## Parameters

* **Input Gain :** This is the gain to apply to the input. It will affect the detected volume and the activity threshold parameter. _This will only work if an Audio input device has been selected and channels have been activated._ 
* **Activity Threshold :** This is volume threshold at which the audio processing is triggered. If the input volume is below this threshold, then its considered as no activity, so no processing will occur. You can consider it as a processing gate. 
* **Keep values :** By default, detected volume, and pitch values will be set back to zero when there is no activity. Activating this parameters allows to avoid resetting the values and staying on the last volume/pitch detected. 
* **Out volume :** This is the master volume, affecting all sound output from this module. It is a multiplier that is applied at the very end of the processing chain, meaning setting it to 0 will result in no sound. 
* **Pitch Detection Method :** This will activate pitch processing, and if there is enough activity in the microphone, it will fill the Pitch Detection section of the values.
  * **None :** This will disable pitch detection. If you don't need it, keep it that way so it's not taking CPU.
  * **MPM :** This is a simple pitch detection method that works quite well for singing, as well as monophonic instruments. If you like reading, [there you go.](http://miracle.otago.ac.nz/tartini/papers/A_Smarter_Way_to_Find_Pitch.pdf)
  * **YIN :** This is another pitch detection method, a bit more complex and more suited to polyphonic sounds or rich in harmonics. More information [here](https://www.eecs.qmul.ac.uk/~simond/pub/2014/MauchDixon-PYIN-ICASSP2014.pdf). 
* **Monitor :** The Monitor section allows you to create a direct pass-through between the input and the output. You can tweak the volume gain, and filter out which channels to output to. 
* **FFT Analysis :** This section will allow you to create custom frequency-based volume detection. To use it, you first need to enable it by clicking on the power icon next to the "FFT Analysis" label. You can then create any number of analyzers by clicking on the green "**+**" icon on the right. Each FFT analyzer also create an "Enveloppe" value in the "FFT Enveloppes" section of the Values.

![2 FFT Analyzers, one is detecting high volume within its frequency range. ](../../.gitbook/assets/fft.png)

* **FFT Parameters :**
  * **Min DB / Max DB :** This is the minimum and maximum volume to detect from. Reducing the range is a good way to filter out background noise.
  * **Analyzer Position :** This is the center frequency at which this analyzer will operate.
  * **Analyzer Size :** This is the frequency range around the center at which the analyzer will operate. Higher range means more tolerant detection, but less sensitive.
  * **Color :** The UI color of the analyer, to easily find it in the analysis window.

{% hint style="success" %}
Once you have finished your FFT setup, it's good practice to collapse the FFT panel, so less CPU is taken for drawing the FFT preview.
{% endhint %}

* **Hardware Settings :** You will find here your usual sound card settings. Again, if you want sound input, you must select a device and then select input channels to use.

