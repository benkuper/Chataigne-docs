# Module Scripts

Les scripts de module vous permettent d'ajouter une gestion plus complexe et plus spécifique des valeurs, d'aider à l'analyse des données provenant de flux réseau ou série qui suivent une API spécifique.

C'est également la façon de créer des [Modules personnalisés](../../modules/custom-modules/), où vous pouvez définir vos propres valeurs et paramètres, et faire exécuter la logique principale par des scripts.

## Fonctions communes des modules

Tous les scripts fonctionnant à l'intérieur d'un module auront un ensemble commun de fonctions qui pourront être ajoutées au script. Ces fonctions ne sont pas nécessaires pour exécuter le script.

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **function moduleParameterChanged\(**_param_**\)** | Cette fonction sera appelée chaque fois qu'un paramètre de ce module aura changé, c'est-à-dire un paramètre ou un déclencheur à l'intérieur du panneau "Paramètres" de ce module. | `fonction moduleParameterChanged(param){ script.log("Param changed : "+param.name) ; }` _\`\`_ |
| **function moduleValueChanged\(**_param_**\)** | Cette fonction sera appelée à chaque fois qu'une valeur de ce module aura changé, c'est-à-dire un paramètre ou un déclencheur à l'intérieur du panneau "Valeurs" de ce module. | `fonction moduleValueChanged(value) { if(value.isParameter()) { script.log("Valeur du module changée : "+value.name+") > "+value.get()) ; }else { script.log("Valeur du module déclenchée : "+value.name) ; }  }` |

## Fonctions spécifiques aux modules

Certains modules ont des rappels de fonctions spécifiques qui sont utiles si vous souhaitez personnaliser l'analyse des données reçues de ce module.

{% tabs %}
{% tab title="OSC" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>oscEvent(</b><em>address, args</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Cette fonction sera appel&#xE9;e &#xE0; chaque fois qu&apos;un message
          du CSP sera re&#xE7;u.</p>
        <p><em><b>adresse</b></em> est l&apos;adresse du message du CSP
          <br /><em><b>args</b></em> est un tableau contenant tous les arguments de l&apos;OSC
          Message</p>
      </th>
      <th style="text-align:left">
        <p><code>fonction oscEvent(adresse, args) {<br />script.log(&quot;OSC Message re&#xE7;u &quot;+adresse+&quot; ;, &quot;+args.length+&quot; ; arguments&quot; ;);</code>
        </p>
        <p><code>}</code>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="MIDI" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>noteOnEvent (</b><em>canal, hauteur, vitesse</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Cette fonction sera appel&#xE9;e &#xE0; chaque fois qu&apos;un &#xE9;v&#xE9;nement
          noteOn sera re&#xE7;u.</p>
        <p>Les arguments sont respectivement le canal, le pas et la vitesse de cette
          event.</p>
      </th>
      <th style="text-align:left"><code>function noteOnEvent(channel, pitch, velocity) {<br />script.log(&quot;Note on received &quot;+channel+&quot; ;, &quot;+pitch+&quot; ;, &quot;+velocity);<br />}</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left"><b>noteOffEvent (</b><em>canal, hauteur, vitesse</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Cette fonction sera appel&#xE9;e &#xE0; chaque fois qu&apos;un &#xE9;v&#xE9;nement
          noteOff sera re&#xE7;u.</p>
        <p>Les arguments sont respectivement le canal, le pas et la vitesse de cette
          event.</p>
      </th>
      <th style="text-align:left"><code>function noteOffEvent(channel, pitch, velocity) {<br />script.log(&quot;Note off received &quot;+channel+&quot; ;, &quot;+pitch+&quot; ;, &quot;+velocity);<br />}</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left"><b>ccEvent (</b><em>canal, nombre, valeur</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Cette fonction sera appel&#xE9;e &#xE0; chaque fois qu&apos;un &#xE9;v&#xE9;nement
          noteOff sera re&#xE7;u.</p>
        <p>Les arguments sont respectivement le canal, le nombre et la valeur de
          cet &#xE9;v&#xE9;nement.</p>
      </th>
      <th style="text-align:left"><code>fonction ccEvent(channel, number, value) {<br />script.log(&quot;ControlChange re&#xE7;u &quot;+channel+&quot; ;, &quot;+number+&quot; ;, &quot;+value);<br />}</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left"><b>sysExEvent(</b><em>data</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Cette fonction sera appel&#xE9;e &#xE0; chaque fois qu&apos;un &#xE9;v&#xE9;nement
          sysEx sera re&#xE7;u.</p>
        <p>L&apos;argument est un tableau d&apos;octets contenant les donn&#xE9;es
          sysEx.</p>
      </th>
      <th style="text-align:left"><code>fonction sysExEvent(data) { script.log(&quot;Sysex Message re&#xE7;u, &quot;+data.length+&quot; ; bytes :&quot; ;);<br />for(var i=0 ; i &lt; ; data.length ; i++) {<br />script.log(&quot; ; &gt; ; &quot;+data[i]);<br />}<br />}</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| **pitchWheelEvent \(**_channel, value_**\)** | Cette fonction sera appelée à chaque fois qu'un événement pitchWheel sera reçu. Les arguments sont respectivement le canal et la valeur de cet événement. | `fonction pitchWheelEvent(channel, value) { script.log("PitchWheel received "+channel+" ;, "+value); }` |
| :--- | :--- | :--- |


| **channelPressureEvent \(**_channel, value_**\)** | Cette fonction sera appelée à chaque fois qu'un événement ChannelPressure sera reçu. Les arguments sont respectivement le canal et la valeur de cet événement. | `fonction channelPressureEvent(channel, value) { script.log("Channel Pressure received "+channel+" ;, "+value); }` |
| :--- | :--- | :--- |


| **afterTouchEvent \(**_canal, note, valeur_**\)** | Cette fonction sera appelée à chaque fois qu'un événement afterTouch sera reçu. Les arguments sont respectivement le canal, la note et la valeur de cette event. | `fonction afterTouchEvent(channel, note, value) { script.log("After Touch received "+channel+" ;, "+note+" ;, "+value); }` |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="DMX" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **send\(**_startChannel, value1, value2, ..., valueN_**\)** | Envoie des valeurs DMX à partir du **startChannel.** Vous pouvez ajouter autant de valeurs que vous le souhaitez, et vous pouvez même mélanger des tableaux de valeurs avec des valeurs individuelles. Les valeurs vont de 0 à 255. | `local.send(32, 255);` |
{% endtab %}

{% tab title="Serial/UDP/TCP" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>donn&#xE9;esRe&#xE7;ues</b><em><b>(</b>donn&#xE9;es</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Cette fonction sera appel&#xE9;e &#xE0; chaque fois que des donn&#xE9;es
          auront &#xE9;t&#xE9; re&#xE7;ues.</p>
        <p>Si le protocole du Module&apos;s est r&#xE9;gl&#xE9; sur <em><b>Lines,</b></em> alors
          l&apos;argument <b>data</b> sera une cha&#xEE;ne contenant la ligne, sans
          la terminaison \n.</p>
        <p>Sinon, les donn&#xE9;es seront un tableau d&apos;octets contenant les
          data.</p>
      </th>
      <th style="text-align:left">
        <p><code>fonction dataReceived(data) {</code>
        </p>
        <p><code>script.log(&quot;Donn&#xE9;es re&#xE7;ues : &quot;+data);</code>
        </p>
        <p><code>}</code>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="HTTP" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>dataEvent(</b><em>data, requestURL</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Cette fonction sera appel&#xE9;e chaque fois que le module aura re&#xE7;u
          une r&#xE9;ponse de une demande.
          <br /><em><b>data</b></em> est le contenu de la r&#xE9;ponse</p>
        <p><em><b>demandeURL</b></em> est l&apos;url de la demande initiale.</p>
      </th>
      <th style="text-align:left"><code>fonction dataEvent(data, requestURL) {<br />script.log(&quot;Data received, request URL :&quot;+requestURL+&quot;\nContent :\n&quot; ; +data);<br />}</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}
{% endtabs %}

## Module-specific methods \(the local object\)

Some modules have specific methods that are useful if you want to have specific behaviors or send complex or automated data. Those methods are part of the **local** Javascript object, depending on the module it's running in.

{% tabs %}
{% tab title="OSC" %}
| Method | Description | Example |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>send(</b><em>address, arg1, arg2, arg3, ...</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>This sends an OSC message to all the enabled outputs of this module.</p>
        <p><em><b>address</b></em> is the address of the message</p>
      </th>
      <th style="text-align:left"><code>local.send(&quot;/myAddress&quot;, 1, .5f, &quot;cool&quot;);</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| **sendTo\(**_ip, port, address, arg1, arg2, arg3, ..._**\)** | Same as the **send** method, but sending to a specific _**ip**_ and _**port,**_ ignoring the module's output. | `local.sendTo("192.168.1.255", 9000, "/myAddress", 1, .5f, "cool");` |
| :--- | :--- | :--- |
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
      <td style="text-align:left"><b>send(</b><em>channel, value1, value2, ...</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>This will send value to the specified DMX channel.</p>
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
| **sendTo\(**_ip, port, message_**\)** | **\[UDP Only\]** Same as the **send** method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output. | `local.sendTo("192.168.1.255", 8888, "This is my message");` |
| **sendBytesTo\(**_ip, port, byte1, byte2, \[bytes\], ..._**\)** | **\[UDP Only\]** Same as the **sendBytes** method, but will send to a specific _**ip**_ and _**port**_, ignoring the module's output. | `local.sendBytesTo("192.168.1.255", 8888, 30,210, [255,0,0], 5);` |
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

