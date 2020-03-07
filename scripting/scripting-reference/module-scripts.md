# Module Scripts

Module Scripts allows you to add more complex and specific handling of values, help parsing data from network or serial streams that are following a specific API.

It's also the way to create [Custom Modules](../../modules/custom-modules/), where you can define your own values and parameters, and have scripts run the main logic.

## Module common functions

All scripts running inside a module will have a common set of functions that can be added to the script. Those functions are not needed to run the script.

| Method | Description | Example |
| :--- | :--- | :--- |
| **function moduleParameterChanged\(**_param_**\)** | This function will be called each time a parameter of this module has changed, meaning a parameter or trigger inside the "Parameters" panel of this module. | `function moduleParameterChanged(param){    script.log("Param changed : "+param.name); }` _\`\`_ |
| **function moduleValueChanged\(**_param_**\)** | This function will be called each time a value of this module has changed, meaning a parameter or trigger inside the "Values" panel of this module. | `function moduleValueChanged(value) { if(value.isParameter()) { script.log("Module value changed : "+value.name+" > "+value.get()); }else { script.log("Module value triggered : "+value.name); }  }` |

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
      <td style="text-align:left"><b>noteOnEvent(</b><em>channel, pitch, velocity</em><b>)</b>
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
      <td style="text-align:left"><b>noteOffEvent(</b><em>channel, pitch, velocity</em><b>)</b>
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
      <td style="text-align:left"><b>ccEvent(</b><em>channel, number, value</em><b>)</b>
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
  </tbody>
</table>
{% endtab %}

{% tab title="DMX" %}
| Method | Description | Example |
| :--- | :--- | :--- |
| **send\(**_startChannel, value1, value2, ..., valueN_**\)** | Sends DMX values starting at the **startChannel.** You can add as many values as you want, and you can even mix array of values with single values. Values are 0 to 255. | `local.send(32, 255);`  |
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
      <td style="text-align:left"><b>dataEvent(</b><em>data, requestURL</em><b>)</b>
      </td>
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
      <td style="text-align:left"><b>send(</b><em>address, arg1, arg2, arg3, ...</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This sends an OSC message to all the enabled outputs of this module.</p>
        <p><em><b>address</b></em> is the address of the message</p>
      </td>
      <td style="text-align:left"><code>local.send(&quot;/myAddress&quot;, 1, .5f, &quot;cool&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>sendTo(</b><em>ip, port, address, arg1, arg2, arg3, ...</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This sends an OSC message to a specific <em><b>ip </b></em>and <em><b>port, </b></em>ignoring
          the module&apos;s output.</p>
        <p><em><b>address</b></em> is the address of the message</p>
      </td>
      <td style="text-align:left"><code>local.sendTo(&quot;192.168.1.255&quot;, 9000, &quot;/myAddress&quot;, 1, .5f, &quot;cool&quot;);</code>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="MIDI" %}
| Method | Description | Example |
| :--- | :--- | :--- |
| **sendNoteOn\(**_channel, pitch, velocity_**\)** | This will send a Note On event on the module's output MIDI device. | `local.sendNoteOn(1, 12, 127);` |
| **sendNoteOff\(**_channel, pitch_**\)** | This will send a Note Off event on the module's output MIDI device. | `local.sendNoteOff(1, 12);` |
| **sendCC\(**_channel, pitch, velocity_**\)** | This will send a Control Change event on the module's output MIDI device. | `local.sendCC(3, 20, 65);` |
| **sendSysEx\(**_byte1, byte2, byte3, ..._**\)** | This will send a SysEx message on the module's output MIDI device. You can add as many arguments you want in the SysEx message. |  |
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
      <td style="text-align:left"><b>send(</b><em>channel, value1, value2, ...</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This will send value to the specified DMX channel.</p>
        <p></p>
        <p>After specifying the <b>channel</b>, you can add multiple values. The channel
          will be treated as a start channel. Value1 will be sent to the start channel.
          Value2 will be sent to the channel after the start channel. Thus, the channel
          will be incremented for each value.</p>
      </td>
      <td style="text-align:left"><code>local.send(1, 255);</code>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="Serial/UDP/TCP" %}
| Method | Description | Example |
| :--- | :--- | :--- |
| **send\(**_message_**\)** | This will send the string passed in as ASCII characters. | `local.send("This is my message");` |
| **sendBytes\(**_byte1, byte2, \[bytes\], ..._**\)** | This will send all the bytes passed in as they are. The bytes can be packed into arrays or just laid out one by one, or a mix of arrays and bytes. | `local.sendBytes(30,210, [255,0,0], 5);` |
| **sendTo\(**_ip, port, message_**\)** | **\[UDP Only\]** Same as the _**send**_ method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output. | `local.sendTo("192.168.1.255", 8888, "This is my message");` |
| **sendBytesTo\(**_ip, port, byte1, byte2, \[bytes\], ..._**\)** | **\[UDP Only\]** Same as the _**sendBytes**_ method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output. | `local.sendBytesTo("192.168.1.255", 8888, 30,210, [255,0,0], 5);` |
{% endtab %}

{% tab title="HTTP" %}
| Method | Description | Example |
| :--- | :--- | :--- |
| **sendGET\(**_url_**\)** | This will send an HTTP GET request. You can add parameters at the end of the _**url**_ argument, just like any GET URL. | `local.sendGET( "https://httpbin.org/anything?myValue1=1&myValue2=super");` |
| **sendPOST\(**_url, param1, value1, param2, value2, ..._**\)** | This will send an HTTP POST request. After specifying the _**url**_, you can add pair of values that are respectively the _**parameter name**_ and its _**value**_. | `local.sendPOST( "https://httpbin.org/anything", "myValue1", 1, "myValue2", 2);` |
{% endtab %}

{% tab title="System" %}
| Method | Description | Example |
| :--- | :--- | :--- |
| **launchApp\(**_appPath, arguments_**\)** | Launches an app at the provided path with the provided arguments | `local.launchApp("myApp.exe","-p myOption");` |
{% endtab %}
{% endtabs %}

