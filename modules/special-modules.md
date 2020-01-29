# Special Modules

Additionally to all the available modules, there are special modules that are already integrated into Chataigne and that you can use like any other module.

* **Sequences :** This module allows control over your [_sequences_](../the-time-machine-sequences/introduction-to-the-time-machine.md#sequence). You can for instance play, resume, stop a sequence, go to a specific cue, set a specific time, jump forward or backward in time. 
* **State Machine :** This module allows control over your [states](../the-state-machine/introduction-to-the-state-machine.md). You can for instance activate a state, trigger an [Action](../the-state-machine/actions.md), enable or disable an [Action ](../the-state-machine/actions.md)or a [Mapping](../the-state-machine/mappings.md)... 
* **Custom Variables :** This module gives you informations about the current state of your custom variables that you can use in [Conditions ](../the-state-machine/actions.md#conditions)and [Mapping inputs](../the-state-machine/mappings.md#input), and allows also control over those variables. For instance you can set a variable's value, or add +1 to a variable. 
* **Generic :** This is a very handy module that allows to control any parameter of your project, and get the value of any of those parameters as well.  It allows also to log messages into the Logger, which is very practical when testing out and debugging your project. You can insert custom script there as well, not sure if it's interesting at all but it's there.

{% hint style="warning" %}
Only use the Generic commands when no other command is suited for that. For example, you should prefer using Sequence commands over Generic "Set parameter value" command if you want to control a sequence's timeline.
{% endhint %}

