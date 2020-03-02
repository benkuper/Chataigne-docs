# OSC

The OSC Module will receive any OSC message and convert them automatically into values, and allows to send OSC messages to one or more outputs

![](../../.gitbook/assets/osc.png)

## Parameters

* **Auto-Add :** This will automatically add values when OSC messages are received. Keep it checked if you want to receive every OSC message and convert it to value, otherwise if you want to only receive some messages, uncheck it when you don't wan't to automatically add more values anymore 
* **Split Arguments :** When checked, if the received OSC Message contains more than one argument, it will automatically create one value for each argument and append 0,1,2 to the value's name. 
* **Auto Range :** When checked, it will automatically assign a range to float and integer values when receiving new OSC messages. This range will automatically adapt when receiving new values. You can change this range by right clicking on the value and choosing "Set Range..." 
* **Auto Feedback :** When checked, every change of value in the Values container will be automatically sent to all OSC outputs. This is useful when you want to test out or only change those values without having to create commands to send OSC. 
* **OSC Input :** OSC Input allows you to receive OSC messages. It's good practice to disable it if your module is supposed to only send OSC messages and not receiving any. You will see in the Module list that the "Incoming data" icon is automatically hidden when disabling the OSC Input.
  * **Local Port :** This is the port on which your external software will send the OSC messages. 
* **OSC Outputs :** OSC Outputs allows sending OSC messages. It's good practice to disable it if your module is supposed to only receive OSC messages and not sending any. You will see in the Module list that the "Outgoing data" icon is automatically hidden when disabling the OSC Outputs. You can create as many outputs you want, each one will send the exact same messages at the same time whenever a command will be triggered.
  * **Local :** if checked, this will force this output to send to the same computer. It's handy to quickly switch between a remote computer and this computer, to test.
  * **Remote host :** This is the IP address of the computer to send messages to. You need to uncheck _Local_ if you want to specify another address.
  * **Remote port :** This is the port to send the messages to.
  * **Auto detect:** This is a handy tool to auto discover through Bonjour/Zeroconf  apps that support OSC. This may not work on every computer, especially if you don't have the Bonjour services installed. 
* **Pass-through :** This section allows you to directly transfer the incoming OSC messages to other OSC modules. This allow for fast, optimized data transfer through modules, even for messages that are not handled by Chataigne.

### Commands

![OSC Module&apos;s only command : custom message](../../.gitbook/assets/custommessage.png)

Because the OSC Module doesn't know about the target software \(it's an _open_ module\), you can and have to create your own commands.

You can then choose the OSC address, and add as many OSC arguments you want using the small green '**+**' icon on the right.

