# LiveOSC2

LiveOSC2 contrôle [Ableton Live](https://www.ableton.com/en/) 9+ grâce au "Control Surfaces"

Tu dois d'abord installer la Control Surface [LiveOSC2 ](https://github.com/stufisher/LiveOSC2)et l'activer dans Live. Tu peux trouver des infos sur comment faire ça [ici](https://github.com/stufisher/LiveOSC2).

{% hint style="warning" %}
Le système de Control Surface d'Ableton est surtout fait pour contrôler l'interface d'Ableton, ce qui veut dire que la fréquence de contrôle n'estpas stable et peut descendre à 5hz.

Ce module est une manière simple de contrôler Live sans avoir à créer de mapping MIDI, mais n'est pas optimisé !

Si tu veux un contrôle real-time et sans latence d'Ableton Live, il vaut mieux soit utiliser un module MIDI et faire un mapping MIDI dans Live, ou alors utiliser des device Max4Live qui exposent des méthodes OSC.
{% endhint %}

