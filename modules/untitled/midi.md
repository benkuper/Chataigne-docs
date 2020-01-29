# MIDI

The MIDI Module will receive any MIDI note and CC from an input device, and allows to send Notes and CC to an output device.

![](../../.gitbook/assets/midi.png)

* **Auto-Add :** This will automatically add values when MIDI events are received. Keep it checked if you want to receive every MIDI note and controlChange and convert it to value, otherwise if you want to only receive some of them, uncheck it when you don't wan't to automatically add more values anymore. 
* **Auto Feedback :** When checked, every change of value in the Values container will be automatically sent to the MIDI Output. This is useful when you want to test out or only change those values without having to create commands to send MIDI events. 
* **Devices :** This is where you choose which device to connect to. The top line is input and the bottom one is output. You don't need to select both, only the ones that you want to use. If you only want to receive informations from a MIDI controller, then you only need to choosing the MIDI Input device. 
* **Is connected :** Whether the device is connected or not. If at least one of the devices, input or output is connected, it will be checked.

{% hint style="success" %}
If you want to send MIDI events to another software like Ableton Live, you will need a **MIDI Loopback** tool, that will create virtual MIDI devices in your computer, and that you can use to output from Chataigne and use as Input in your other software.

* On MacOS, you can use the IAC Driver for this purpose.
* On Windows, I personally recommend [**loopMIDI**](https://www.tobias-erichsen.de/software/loopmidi.html), which is free, simple, stable and allows creation of multiple devices.

You can even send MIDI events across network and OS-independant by using **Network RTP MIDI devices.**

* On MacOS, you can activate network MIDI device in the _MIDI Studio_ panel.
* On Windows, you can use [**rtpMIDI**](http://www.tobias-erichsen.de/software/rtpmidi.html), which basically replicate MacOS's Network-MIDI panel.
{% endhint %}







