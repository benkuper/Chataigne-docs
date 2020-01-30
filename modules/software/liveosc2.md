# LiveOSC2

LiveOSC2 controls [Ableton Live](https://www.ableton.com/en/) 9+ through a custom control surface.

You first need to install the [LiveOSC2 ](https://github.com/stufisher/LiveOSC2)control surface and activate it in live, you can find information about how to do that [here](https://github.com/stufisher/LiveOSC2).

{% hint style="warning" %}
Ableton Live's control surface system is primarily made to control UI, which means that the rate and latency at which it can be controlled is not stable and can go up to 200ms / 5 fps.

This module is an easy way to control Live without having to always setup MIDI Mappings, but its not optimized at all.

If you wish to have real-time, precise control over Ableton Live, you will need to either using MIDI Mapping and control from a MIDI Module, or integrate a Max4Live device that will convert OSC to MIDI commands.
{% endhint %}

