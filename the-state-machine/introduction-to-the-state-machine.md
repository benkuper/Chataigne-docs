# Introduction to the State Machine

![A rather complex state machine.](../.gitbook/assets/statemachine-1.png)

The State machine will let you create your own interaction rules to do realtime control of all your system. As the name says, it's a state machine, which means you can create different states, each one being a group of rules that you can activate or deactivate as you wish. You can also create transitions between them, allowing to create evolving interactions.

When creating an interaction, you will first have to create a state that will contains the rules.

{% hint style="success" %}
**SHORTCUTS  
- Alt + drag or MMB \(middle mouse button\) :** drag the canvas to navigate in an infinite world of wonder !  
**-  Shift + mouse scroll :** Zoom in/out to see more things, or have bigger UI  
**- Ctrl + C, Ctrl + V, Ctrl + D :** Copy, paste, duplicate items \(this applies to all items in lists and views, i.e. States, Mappings, Actions, Modules, Sequences...\)
{% endhint %}

## States

States are containers that will contains different interaction rules. They can be activated and deactivate manually or automatically, and you can create transition between them.

Currently, you can 2 type of rules : [**Actions**](actions.md) **and** [**Mappings**](mappings.md)**.**

When creating an interaction, you will want either punctual control to trigger commands : these are [**Actions**](actions.md)**,** or continuous control to link input values to parameters : those are [**Mappings**](mappings.md)**.**

### Transitions and State network

Transitions have multiple use cases :

* They can act as action that will automatically transfer the activation of a state to another state. They act like an Action, and can even have consequences so you can have different behaviors when coming from one state or another. 
* They can be used to link multiple states together. This is what we call a _**State network.**_

{% hint style="info" %}
At all time, there is **only 1 active state inside a state network.** This is why creating transitions between multiple states is helpful when you want to ensure that there is only one active state at a time in a group of states.
{% endhint %}

{% hint style="success" %}
By note linking them altogether, you can have as many state networks as you want, meaning you still can have multiple active states at the same time.
{% endhint %}

