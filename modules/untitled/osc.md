# OSC

The OSC Module will receive any OSC message and convert them automatically into values, and allows to send OSC messages to one or more outputs

![](../../.gitbook/assets/osc.png)

## Parameters

**Auto-Add :** This will automatically add values when OSC messages are received. Keep it checked if you want to receive every OSC message and convert it to value, otherwise if you want to only receive some messages, uncheck it when you don't wan't to automatically add more values anymore  
  
**Split Arguments :** When checked, if the received OSC Message contains more than one argument, it will automatically create one value for each argument and append 0,1,2 to the value's name.  
  
**Auto Range :** When checked, it will automatically assign a range to float and integer values when receiving new OSC messages. This range will automatically adapt when receiving new values. You can change this range by right clicking on the value and choosing "Set Range..."  
  
**Auto Feedback :** When checked, every change of value in the Values container will be automatically sent to all OSC outputs. This is useful when you want to test out or only change those values without having to create commands to send OSC.  
  
**OSC Input :** OSC Input allows you to receive OSC Messages. It's good practice to disable it if your module is supposed to only send OSC Messages and not receiving it. You will see in the Module list that the "Incoming data" icon is automatically hidden when disabling the OSC Input.  


{% hint style="info" %}
Remember to have the "Auto Add" option selected if you want to automatically create values when receiving messages.
{% endhint %}

