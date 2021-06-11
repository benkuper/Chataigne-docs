# Module Scripts

Module Scripts allows you to add more complex and specific handling of values, help parsing data from network or serial streams that are following a specific API.

It's also the way to create [Custom Modules](../../modules/custom-modules/), where you can define your own values and parameters, and have scripts run the main logic.

## Module common functions

All scripts running inside a module will have a common set of functions that can be added to the script. Those functions are not needed to run the script.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>function moduleParameterChanged(</b><em>param</em><b>)</b>
      </td>
      <td style="text-align:left">This function will be called each time a parameter of this module has
        changed, meaning a parameter or trigger inside the &quot;Parameters&quot;
        panel of this module.</td>
      <td style="text-align:left"><code>function moduleParameterChanged(param){    script.log(&quot;Param changed : &quot;+param.name); }</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>function moduleValueChanged(</b><em>param</em><b>)</b>
      </td>
      <td style="text-align:left">This function will be called each time a value of this module has changed,
        meaning a parameter or trigger inside the &quot;Values&quot; panel of this
        module.</td>
      <td style="text-align:left">
        <p><code>function moduleValueChanged(value) { if(value.isParameter()) { script.log(&quot;Module value changed : &quot;+value.name+&quot; &gt; &quot;+value.get()); </code>
        </p>
        <p><code>}else {</code>
        </p>
        <p><code>script.log(&quot;Module value triggered : &quot;+value.name); </code>
        </p>
        <p><code>}</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## Module-specific functions

Some modules have specific function callbacks that are useful if you want to customize the parsing of received data from this module.

{% tabs %}
{% tab title="OSC" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>oscEvent(</b><em>address, args</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This function will be called each time an OSC message is received.</p>
        <p><em><b>address</b></em> is the address of the OSC Message
          <br /><em><b>args</b></em> is an array containing all the arguments of the OSC
          Message</p>
      </td>
      <td style="text-align:left">
        <p><code>function oscEvent(address, args) {<br />script.log(&quot;OSC Message received &quot;+address+&quot;, &quot;+args.length+&quot; arguments&quot;);</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="MIDI" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>noteOnEvent (</b><em>channel, pitch, velocity</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This function will be called each time a noteOn event is received.</p>
        <p>The arguments are respectively the channel, pitch and velocity of this
          event.</p>
      </td>
      <td style="text-align:left"><code>function noteOnEvent(channel, pitch, velocity) {<br />script.log(&quot;Note on received &quot;+channel+&quot;, &quot;+pitch+&quot;, &quot;+velocity);<br />}</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>noteOffEvent (</b><em>channel, pitch, velocity</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This function will be called each time a noteOff event is received.</p>
        <p>The arguments are respectively the channel, pitch and velocity of this
          event.</p>
      </td>
      <td style="text-align:left"><code>function noteOffEvent(channel, pitch, velocity) {<br />script.log(&quot;Note off received &quot;+channel+&quot;, &quot;+pitch+&quot;, &quot;+velocity);<br />}</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>ccEvent (</b><em>channel, number, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This function will be called each time a noteOff event is received.</p>
        <p>The arguments are respectively the channel, number and value of this event.</p>
      </td>
      <td style="text-align:left"><code>function ccEvent(channel, number, value) {<br />script.log(&quot;ControlChange received &quot;+channel+&quot;, &quot;+number+&quot;, &quot;+value);<br />}</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>sysExEvent(</b><em>data</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This function will be called each time a sysEx event is received.</p>
        <p>The argument is an array of bytes containing the sysEx data.</p>
      </td>
      <td style="text-align:left"><code>function sysExEvent(data) { script.log(&quot;Sysex Message received, &quot;+data.length+&quot; bytes :&quot;);<br />for(var i=0; i &lt; data.length; i++) {<br />script.log(&quot; &gt; &quot;+data[i]);<br />}<br />}</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>channelPressureEvent (</b><em>channel, value</em><b>)</b>
      </td>
      <td style="text-align:left">This function will be called each time a channelPressure event is received.
        The arguments are respectively the channel and the value of this event.</td>
      <td
      style="text-align:left"><code>function channelPressureEvent(channel, value) { script.log(&quot;Channel Pressure received &quot;+channel+&quot;, &quot;+value); }</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>afterTouchEvent (</b><em>channel, note, value</em><b>)</b>
      </td>
      <td style="text-align:left">This function will be called each time an afterTouch event is received.
        The arguments are respectively the channel, the note and the value of this
        event.</td>
      <td style="text-align:left"><code>function afterTouchEvent(channel, note, value) { script.log(&quot;After Touch received &quot;+channel+&quot;, &quot;+note+&quot;, &quot;+value); }</code>
      </td>
    </tr>
  </tbody>
</table>

| M `"+value); }` |
| :--- |
{% endtab %}

{% tab title="DMX" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>dmxEvent(</b><em>values</em><b>)</b>
      </td>
      <td style="text-align:left">This is called when a group of DMX channel values is received. <em>values </em>is
        an array of values, always starting from channel 1</td>
      <td style="text-align:left">
        <p><code>function dmxEvent(values) {</code>
        </p>
        <p><code>script.log(&quot;Received dmx : &quot;+values.length+&quot; values&quot;);</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="Serial/UDP/TCP" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>dataReceived</b><em><b>(</b>data</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This function will be called each time data has been received.</p>
        <p>If the Module&apos;s protocol is set to <em><b>Lines,</b></em> then the <b>data</b> argument
          will be a string containing the line, without the ending \n.</p>
        <p>Otherwise, the data will be an array of bytes containing the received
          data.</p>
      </td>
      <td style="text-align:left">
        <p><code>function dataReceived(data) {</code>
        </p>
        <p><code>script.log(&quot;Received data : &quot;+data);</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="HTTP" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>dataEvent(</b><em>data, requestURL</em><b>)</b>This function will be
        called each time data has been received.</td>
      <td style="text-align:left">
        <p>This function will be called each time the module has got a response from
          a request.
          <br /><em><b>data</b></em> is the content of the response</p>
        <p><em><b>requestURL</b></em> is the url of the original request.</p>
      </td>
      <td style="text-align:left"><code>function dataEvent(data, requestURL) {<br />script.log(&quot;Data received, request URL :&quot;+requestURL+&quot;\nContent :\n&quot; +data);<br />}</code>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}
{% endtabs %}

## Module-specific methods \(the local object\)

Some modules have specific methods that are useful if you want to have specific behaviors or send complex or automated data. Those methods are part of the **local** Javascript object, depending on the module it's running in.

{% tabs %}
{% tab title="OSC" %}
| Method | Description | Example |
| :--- | :--- | :--- |
| **send\(**_address, arg1, arg2, arg3, ..._**\)** | This sends an OSC message to all the enabled outputs of this module. _**address**_ is the address of the message | `local.send("myAddress", 1, .5f, "cool");` |
| **sendTo\(**_ip, port, address, arg1, arg2, ..._**\)** | Same as the **send** method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output. | `local.sendTo("192.168.0.30", 9000, "myAddress", 1, .5f);` |
| **match\(**_address, pattern_**\)** | Check if the specified _**address**_ matches the _**pattern**_, according to the [OSC specification](http://opensoundcontrol.org/spec-1_0). Wildcards, etc are supported. | `if (local.match(address, "/testPattern")) ...` |
| **register\(**_pattern, callbackFunc_**\)** | Register a script function to call when a message matching _**pattern**_ is received. _**callbackFunc**_ is the name of the callback function. **\[Note\]** if the module contains multiple scripts, the callback is registered for all the scripts. | `function init() {` `local.register("/testPattern", "testPatternCallback");` `}` `function testPatternCallback(address, args) {` `script.log("Received message "+address);` `}` |
{% endtab %}

{% tab title="MIDI" %}
| Method | Description | Example |
| :--- | :--- | :--- |
| **sendNoteOn\(**_channel, pitch, velocity_**\)** | This will send a Note On event on the module's output MIDI device. | `local.sendNoteOn (1, 12, 127);` |
| **sendNoteOff\(**_channel, pitch_**\)** | This will send a Note Off event on the module's output MIDI device. | `local.sendNoteOff (1, 12);` |
| **sendCC\(**_channel, pitch, velocity_**\)** | This will send a Control Change event on the module's output MIDI device. | `local.sendCC (3, 20, 65);` |
| **sendSysEx\(**_byte1, byte2, byte3, ..._**\)** | This will send a SysEx message on the module's output MIDI device. You can add as many arguments you want in the SysEx message. | `local.sendSysex (10, 15,20,20,0);` |
| **sendPitchWheel\(**_channel, value_**\)** | This will send a Pitch Wheel event on the module's output MIDI device. | `local.sendPitchWheel (3, 2000);` |
| **sendChannelPressure\(**_channel, value_**\)** | This will send a Channel Pressure event on the module's output MIDI device. | `local.sendChannelPressure (1, 67);` |
| **sendAfterTouch\(**_channel, note, value_**\)** | This will send an After Touch event on the module's output MIDI device. | `local.sendAfterTouch (3, 20, 65);` |
{% endtab %}

{% tab title="DMX" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><b>send(</b><em>startChannel, value1, value2, ..., valueN</em><b>)</b> 
        </p>
        <p>module&apos;s output MIDI device.</p>
      </td>
      <td style="text-align:left">
        <p>&lt;code&gt;&lt;/code&gt;</p>
        <p>Sends DMX values starting at the <b>startChannel.</b> You can add as many
          values as you want, and you can even mix array of values with single values.
          Values are 0 to 255.</p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p><code>local.send(32, 255);</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="Serial/UDP/TCP/Websocket" %}
| Method | Description | Example |
| :--- | :--- | :--- |
| **send\(**_message_**\)** | This will send the string passed in as ASCII characters. | `local.send("This is my message");` |
| **sendBytes\(**_byte1, byte2, \[bytes\], ..._**\)** | This will send all the bytes passed in as they are. The bytes can be packed into arrays or just laid out one by one, or a mix of arrays and bytes. | `local.sendBytes(30,210, [255,0,0], 5);` |
| **sendTo\(**_ip, port, message_**\)** | **\[UDP Only\]** Same as the **send** method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output. | `local.sendTo("192.168.1.255", 8888, "This is my message");` |
| **sendBytesTo\(**_ip, port, byte1, byte2, \[bytes\], ..._**\)** | **\[UDP Only\]** Same as the **sendBytes** method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output. | `local.sendBytesTo("192.168.1.255", 8888, 30,210, [255,0,0], 5);` |
{% endtab %}

{% tab title="HTTP" %}
There are 2 ways of using following methods. 

In all those methods, the _**address**_ field is appended to the modules "Base Address" parameter

### Inline arguments

You can either pass all the arguments inline, in which case some things are not possible \(putting extra headers and payload in other requests than GET for example\).

<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>sendGET(</b><em>url, [dataType], [extraHeaders], [payload]</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This will send an HTTP GET request. You can add parameters at the end
          of the <em><b>url</b></em> argument, just like any GET URL.</p>
        <p>You can add optional parameters after the address (only works with GET)
          :</p>
        <ul>
          <li>dataType ( <em><b>json</b></em><b> </b>or <em><b>raw </b></em>) : defines
            what type of data to expect for the result</li>
          <li>
            <p>extraHeaders :</p>
            <p>add extra headers to the query</p>
          </li>
          <li>payload :</li>
          <li>add payload to the query</li>
        </ul>
      </td>
      <td style="text-align:left"><code>local.sendGET( &quot;https://httpbin.org/anything?myValue1=1&amp;myValue2=super&quot;, &quot;json&quot;, &quot;Connection: keep-alive&quot;, &quot;some payload here&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>sendPOST(</b><em>url, param1, value1, param2, value2, ...</em><b>)</b>
      </td>
      <td style="text-align:left">This will send an HTTP POST request. After specifying the <em><b>url</b></em>,
        you can add pair of values that are respectively the <em><b>parameter name</b></em> and
        its <em><b>value</b></em>.</td>
      <td style="text-align:left"><code>local.sendPOST( &quot;https://httpbin.org/anything&quot;, &quot;myValue1&quot;, 1, &quot;myValue2&quot;, 2);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>sendPUT(</b><em>url, param1, value1, param2, value2, ...</em><b>)</b>
      </td>
      <td style="text-align:left">This will send an HTTP PUT request. After specifying the <em><b>url</b></em>,
        you can add pair of values that are respectively the <em><b>parameter name</b></em> and
        its <em><b>value</b></em>.</td>
      <td style="text-align:left"><code>local.sendPUT( &quot;https://httpbin.org/anything&quot;, &quot;myValue1&quot;, 1, &quot;myValue2&quot;, 2);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>sendPATCH(</b><em>url, param1, value1, param2, value2, ...</em><b>)</b>
      </td>
      <td style="text-align:left">This will send an HTTP PATCH request. After specifying the <em><b>url</b></em>,
        you can add pair of values that are respectively the <em><b>parameter name</b></em> and
        its <em><b>value</b></em>.</td>
      <td style="text-align:left"><code>local.sendPATCH( &quot;https://httpbin.org/anything&quot;, &quot;myValue1&quot;, 1, &quot;myValue2&quot;, 2);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>sendDELETE(</b><em>url, param1, value1, param2, value2, ...</em><b>)</b>
      </td>
      <td style="text-align:left">This will send an HTTP DELETE request. After specifying the <em><b>url</b></em>,
        you can add pair of values that are respectively the <em><b>parameter name</b></em> and
        its <em><b>value</b></em>.</td>
      <td style="text-align:left"><code>local.sendDELETE( &quot;https://httpbin.org/anything&quot;, &quot;myValue1&quot;, 1, &quot;myValue2&quot;, 2)</code>
      </td>
    </tr>
  </tbody>
</table>

### Object arguments

You can pass an object containing the parameters to send the request. This looks like this :

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
| Method | Description | Example |
| :--- | :--- | :--- |
| **launchApp\(**_appPath, arguments_**\)** | Launches an app at the provided path with the provided arguments | `local.launchApp("myApp.exe","-p myOption");` |
{% endtab %}
{% endtabs %}







