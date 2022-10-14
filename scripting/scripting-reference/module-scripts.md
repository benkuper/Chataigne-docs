# Module Scripts

Module Scripts allows you to add more complex and specific handling of values, help parsing data from network or serial streams that are following a specific API.

It's also the way to create [Custom Modules](../../modules/custom-modules/), where you can define your own values and parameters, and have scripts run the main logic.

## Module common functions

All scripts running inside a module will have a common set of functions that can be added to the script. Those functions are not needed to run the script.

| Method                                           | Description                                                                                                                                                 | Example                                                                                                                                                                                                                                                                                              |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **function moduleParameterChanged(**_param_**)** | This function will be called each time a parameter of this module has changed, meaning a parameter or trigger inside the "Parameters" panel of this module. | `function moduleParameterChanged(param){    script.log("Param changed : "+param.name); }`                                                                                                                                                                                                            |
| **function moduleValueChanged(**_param_**)**     | This function will be called each time a value of this module has changed, meaning a parameter or trigger inside the "Values" panel of this module.         | <p><code>function moduleValueChanged(value) { if(value.isParameter()) { script.log("Module value changed : "+value.name+" > "+value.get());</code> </p><p><code>}else {</code></p><p><code>script.log("Module value triggered : "+value.name);</code> </p><p><code>}</code></p><p><code>}</code></p> |

## Module-specific functions

Some modules have specific function callbacks that are useful if you want to customize the parsing of received data from this module.

{% tabs %}
{% tab title="OSC" %}
| Method                            | Description                                                                                                                                                                                                                                       | Example                                                                                                                                                                |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **oscEvent(**_address, args_**)** | <p>This function will be called each time an OSC message is received.</p><p><em><strong>address</strong></em> is the address of the OSC Message<br><em><strong>args</strong></em> is an array containing all the arguments of the OSC Message</p> | <p><code>function oscEvent(address, args) {</code><br><code>script.log("OSC Message received "+address+", "+args.length+" arguments");</code></p><p><code>}</code></p> |
{% endtab %}

{% tab title="MIDI" %}
| Method                                            | Description                                                                                                                                                    | Example                                                                                                                                                                                                                                                 |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **noteOnEvent (**_channel, pitch, velocity_**)**  | <p>This function will be called each time a noteOn event is received.</p><p>The arguments are respectively the channel, pitch and velocity of this event.</p>  | <p><code>function noteOnEvent(channel, pitch, velocity) {</code><br><code>script.log("Note on received "+channel+", "+pitch+", "+velocity);</code><br><code>}</code></p>                                                                                |
| **noteOffEvent (**_channel, pitch, velocity_**)** | <p>This function will be called each time a noteOff event is received.</p><p>The arguments are respectively the channel, pitch and velocity of this event.</p> | <p><code>function noteOffEvent(channel, pitch, velocity) {</code><br><code>script.log("Note off received "+channel+", "+pitch+", "+velocity);</code><br><code>}</code></p>                                                                              |
| **ccEvent (**_channel, number, value_**)**        | <p>This function will be called each time a noteOff event is received.</p><p>The arguments are respectively the channel, number and value of this event.</p>   | <p><code>function ccEvent(channel, number, value) {</code><br><code>script.log("ControlChange received "+channel+", "+number+", "+value);</code><br><code>}</code></p>                                                                                  |
| **sysExEvent(**_data_**)**                        | <p>This function will be called each time a sysEx event is received.</p><p>The argument is an array of bytes containing the sysEx data.</p>                    | <p><code>function sysExEvent(data) { script.log("Sysex Message received, "+data.length+" bytes :");</code><br><code>for(var i=0; i &#x3C; data.length; i++) {</code><br><code>script.log(" > "+data[i]);</code><br><code>}</code><br><code>}</code></p> |
| **channelPressureEvent (**_channel, value_**)**   | This function will be called each time a channelPressure event is received. The arguments are respectively the channel and the value of this event.            | `function channelPressureEvent(channel, value) { script.log("Channel Pressure received "+channel+", "+value); }`                                                                                                                                        |
| **afterTouchEvent (**_channel, note, value_**)**  | This function will be called each time an afterTouch event is received. The arguments are respectively the channel, the note and the value of this event.      | `function afterTouchEvent(channel, note, value) { script.log("After Touch received "+channel+", "+note+", "+value); }`                                                                                                                                  |

| M `"+value); }` |
| --------------- |
{% endtab %}

{% tab title="DMX" %}
| Method                     | Description                                                                                                                   | Example                                                                                                                                        |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **dmxEvent(**_values_**)** | This is called when a group of DMX channel values is received. _values_ is an array of values, always starting from channel 1 | <p><code>function dmxEvent(values) {</code></p><p><code>script.log("Received dmx : "+values.length+" values");</code></p><p><code>}</code></p> |
{% endtab %}

{% tab title="Serial/UDP/TCP" %}
| Method                           | Description                                                                                                                                                                                                                                                                                                                            | Example                                                                                                                        |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **dataReceived**_**(**data_**)** | <p>This function will be called each time data has been received.</p><p>If the Module's protocol is set to <em><strong>Lines,</strong></em> then the <strong>data</strong> argument will be a string containing the line, without the ending \n.</p><p>Otherwise, the data will be an array of bytes containing the received data.</p> | <p><code>function dataReceived(data) {</code></p><p><code>script.log("Received data : "+data);</code></p><p><code>}</code></p> |
{% endtab %}

{% tab title="HTTP" %}
| **dataEvent(**_data, requestURL_**)**This function will be called each time data has been received. | <p>This function will be called each time the module has got a response from a request.<br><em><strong>data</strong></em> is the content of the response</p><p><em><strong>requestURL</strong></em> is the url of the original request.</p> | <p><code>function dataEvent(data, requestURL) {</code><br><code>script.log("Data received, request URL :"+requestURL+"\nContent :\n" +data);</code><br><code>}</code></p> |
| --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
{% endtab %}

{% tab title="System" %}
| Method                                             | Description                                                                                                                                                                                                                                                                                                          | Example                                                                                                                                       |
| -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **processDataReceived(**_data, originCommand_**)** | <p>This function will be called after a call to <em><strong>launchProcess()</strong></em> with blocking set to <em>false.</em><br><em><strong>data</strong></em> contains the output of the process as a string<br><em><strong>originCommand</strong></em> contains the command that was called for this output </p> | <p><code>function processDataReceived(data, command) {</code><br><code>script.log("Data received",data,command);</code><br><code>}</code></p> |


{% endtab %}
{% endtabs %}

## Module-specific methods (the local object)

Some modules have specific methods that are useful if you want to have specific behaviors or send complex or automated data. Those methods are part of the **local** Javascript object, depending on the module it's running in.

{% tabs %}
{% tab title="OSC" %}
| Method                                               | Description                                                                                                                                                                                                                                         | Example                                                                                                                                                                                                                                                                 |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **send(**_address, arg1, arg2, arg3, ..._**)**       | This sends an OSC message to all the enabled outputs of this module. _**address**_ is the address of the message                                                                                                                                    | `local.send("myAddress", 1, .5f, "cool");`                                                                                                                                                                                                                              |
| **sendTo(**_ip, port, address, arg1, arg2, ..._**)** | Same as the **send** method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output.                                                                                                                                     | `local.sendTo("192.168.0.30", 9000, "myAddress", 1, .5f);`                                                                                                                                                                                                              |
| **match(**_address, pattern_**)**                    | Check if the specified _**address**_ matches the _**pattern**_, according to the [OSC specification](http://opensoundcontrol.org/spec-1\_0.html). Wildcards, etc are supported.                                                                     | `if (local.match(address, "/testPattern")) ...`                                                                                                                                                                                                                         |
| **register(**_pattern, callbackFunc_**)**            | Register a script function to call when a message matching _**pattern**_ is received. _**callbackFunc**_ is the name of the callback function. **\[Note]** if the module contains multiple scripts, the callback is registered for all the scripts. | <p><code>function init() {</code><br><code>local.register("/testPattern", "testPatternCallback");</code><br><code>}</code><br><code>function testPatternCallback(address, args) {</code><br><code>script.log("Received message "+address);</code><br><code>}</code></p> |
{% endtab %}

{% tab title="MIDI" %}
| Method                                         | Description                                                                                                                     | Example                              |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| **sendNoteOn(**_channel, pitch, velocity_**)** | This will send a Note On event on the module's output MIDI device.                                                              | `local.sendNoteOn (1, 12, 127);`     |
| **sendNoteOff(**_channel, pitch_**)**          | This will send a Note Off event on the module's output MIDI device.                                                             | `local.sendNoteOff (1, 12);`         |
| **sendCC(**_channel, pitch, velocity_**)**     | This will send a Control Change event on the module's output MIDI device.                                                       | `local.sendCC (3, 20, 65);`          |
| **sendSysEx(**_byte1, byte2, byte3, ..._**)**  | This will send a SysEx message on the module's output MIDI device. You can add as many arguments you want in the SysEx message. | `local.sendSysex (10, 15,20,20,0);`  |
| **sendPitchWheel(**_channel, value_**)**       | This will send a Pitch Wheel event on the module's output MIDI device.                                                          | `local.sendPitchWheel (3, 2000);`    |
| **sendChannelPressure(**_channel, value_**)**  | This will send a Channel Pressure event on the module's output MIDI device.                                                     | `local.sendChannelPressure (1, 67);` |
| **sendAfterTouch(**_channel, note, value_**)** | This will send an After Touch event on the module's output MIDI device.                                                         | `local.sendAfterTouch (3, 20, 65);`  |
{% endtab %}

{% tab title="DMX" %}
| Method                                                                                                                                | Description                                                                                                                                                                                                      | Example                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| <p><strong>send(</strong><em>startChannel, value1, value2, ..., valueN</em><strong>)</strong> </p><p>module's output MIDI device.</p> | <p><code></code></p><p>Sends DMX values starting at the <strong>startChannel.</strong> You can add as many values as you want, and you can even mix array of values with single values. Values are 0 to 255.</p> | <p></p><p><code>local.send(32, 255);</code></p> |
{% endtab %}

{% tab title="Serial/UDP/TCP/Websocket" %}
| Method                                                       | Description                                                                                                                                        | Example                                                           |
| ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **send(**_message_**)**                                      | This will send the string passed in as ASCII characters.                                                                                           | `local.send("This is my message");`                               |
| **sendBytes(**_byte1, byte2, \[bytes], ..._**)**             | This will send all the bytes passed in as they are. The bytes can be packed into arrays or just laid out one by one, or a mix of arrays and bytes. | `local.sendBytes(30,210, [255,0,0], 5);`                          |
| **sendTo(**_ip, port, message_**)**                          | **\[UDP Only]** Same as the **send** method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output.                    | `local.sendTo("192.168.1.255", 8888, "This is my message");`      |
| **sendBytesTo(**_ip, port, byte1, byte2, \[bytes], ..._**)** | **\[UDP Only]** Same as the **sendBytes** method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output.               | `local.sendBytesTo("192.168.1.255", 8888, 30,210, [255,0,0], 5);` |
{% endtab %}

{% tab title="HTTP" %}
There are 2 ways of using following methods.&#x20;

In all those methods, the _**address**_ field is appended to the modules "Base Address" parameter. The examples are considering that default base address is [https://httpbin.org/](https://httpbin.org/)

### Inline arguments

You can either pass all the arguments inline, in which case some things are not possible (putting extra headers and payload in other requests than GET for example).

| Method                                                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Example                                                                                                        |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| **sendGET(**_url, \[dataType], \[extraHeaders], \[payload]_**)** | <p>This will send an HTTP GET request. You can add parameters at the end of the <em><strong>url</strong></em> argument, just like any GET URL.</p><p>You can add optional parameters after the address (only works with GET) :</p><ul><li>dataType ( <em><strong>json</strong></em><strong> </strong> or <em><strong>raw</strong></em> ) : defines what type of data to expect for the result</li><li><p>extraHeaders : </p><p>add extra headers to the query</p></li><li>payload :</li><li>add payload to the query</li></ul> | `local.sendGET( "anything?myValue1=1&myValue2=super", "json", "Connection: keep-alive", "some payload here");` |
| **sendPOST(**_url, param1, value1, param2, value2, ..._**)**     | This will send an HTTP POST request. After specifying the _**url**_, you can add pair of values that are respectively the _**parameter name**_ and its _**value**_.                                                                                                                                                                                                                                                                                                                                                            | `local.sendPOST( "anything", "myValue1", 1, "myValue2", 2);`                                                   |
| **sendPUT(**_url, param1, value1, param2, value2, ..._**)**      | This will send an HTTP PUT request. After specifying the _**url**_, you can add pair of values that are respectively the _**parameter name**_ and its _**value**_.                                                                                                                                                                                                                                                                                                                                                             | `local.sendPUT( "anything", "myValue1", 1, "myValue2", 2);`                                                    |
| **sendPATCH(**_url, param1, value1, param2, value2, ..._**)**    | This will send an HTTP PATCH request. After specifying the _**url**_, you can add pair of values that are respectively the _**parameter name**_ and its _**value**_.                                                                                                                                                                                                                                                                                                                                                           | `local.sendPATCH( "anything", "myValue1", 1, "myValue2", 2);`                                                  |
| **sendDELETE(**_url, param1, value1, param2, value2, ..._**)**   | This will send an HTTP DELETE request. After specifying the _**url**_, you can add pair of values that are respectively the _**parameter name**_ and its _**value**_.                                                                                                                                                                                                                                                                                                                                                          | `local.sendDELETE( "anything", "myValue1", 1, "myValue2", 2)`                                                  |

### Object arguments (1.8 only)

You can pass an object containing the parameters to send the request. All properties of the "params" object are optional. When adding all, this looks like this :

```javascript
var params = {};
params.dataType = "json";
params.extraHeaders = "Content-Type: application/json";
params.arguments = ["myValue1",1,"myValue2",2];

var payload = {}; //the payload can be either a simple string or an object that will be automatically stringified
payload.super = "cool";
payload.number = 3.2;
params.payload = payload;

local.sendGET("anything", params); //the address field will be appended to the module's base address
local.sendPOST("anything", params);
local.sendPUT("anything", params);
local.sendPATCH("anything", params);
local.sendDELETE("anything", params);
```
{% endtab %}

{% tab title="System" %}
| Méthode                                                                                     | Description                                                                                                                                                                                                                                                                                                                                     | Exemple                                                |
| ------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| **launchApp(**_appPath, arguments_**)**                                                     | Launch an app file with arguments                                                                                                                                                                                                                                                                                                               | `local.launchApp("myApp.exe", "-p myOption");`         |
| <p><strong>launchCommand(</strong><em>command, silentMode</em><strong>)</strong></p><p></p> | Launch a command                                                                                                                                                                                                                                                                                                                                | `local.launchCommand("myApp.exe", true);`              |
| **launchProcess(**_command, blocking_**)**                                                  | <p>Launch a process and returns the output.<br>If <em><strong>blocking</strong></em> is false, then the process is done asynchronously and the result is returned via a call to <em>processDataReceveid(data)</em><br><em></em>If it is true, then the program blocks until the process is finished, and the result is returned immediately</p> | `var result = local.launchCommand("myApp.exe", true);` |
| **getRunningProcesses()**                                                                   | List all running processes                                                                                                                                                                                                                                                                                                                      | `var result = local.getRunningProcesses();`            |
| **isProcessRunning(**_process_**)**                                                         | Check if a process is currently running                                                                                                                                                                                                                                                                                                         | `var isRunning = local.isProcessRunning("MyApp.exe"`   |
{% endtab %}
{% endtabs %}





