# Module Scripts

Les scripts de module vous permettent d'ajouter une gestion plus complexe et plus spécifique des valeurs, d'aider à l'analyse des données provenant de flux réseau ou série qui suivent une API spécifique.

C'est également la façon de créer des [Modules personnalisés](../../modules/custom-modules/), où vous pouvez définir vos propres valeurs et paramètres, et faire exécuter la logique principale par des scripts.

## Fonctions communes des modules

Tous les scripts fonctionnant à l'intérieur d'un module auront un ensemble commun de fonctions qui pourront être ajoutées au script. Ces fonctions ne sont pas nécessaires pour exécuter le script.

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **function moduleParameterChanged\(**_param_**\)** | Cette fonction sera appelée chaque fois qu'un paramètre de ce module aura changé, c'est-à-dire un paramètre ou un déclencheur à l'intérieur du panneau "Parameters" de ce module. | `function moduleParameterChanged(param){ script.log("Param changed : "+param.name) ; }` _\`\`_ |
| **function moduleValueChanged\(**_param_**\)** | Cette fonction sera appelée à chaque fois qu'une valeur de ce module aura changé, c'est-à-dire un paramètre ou un déclencheur à l'intérieur du panneau "Values" de ce module. | `function moduleValueChanged(value) { if(value.isParameter()) { script.log("Valeur du module changée : "+value.name+") > "+value.get()) ; }else { script.log("Valeur du module déclenchée : "+value.name) ; }  }` |

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

{% tab title="Serial/UDP/TCP" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>dataReceived</b><em><b>(</b>donn&#xE9;es</em><b>)</b>
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
      <th style="text-align:left"><code>fonction dataEvent(data, requestURL) {<br />script.log(&quot;Donn&#xE9;es re&#xE7;ues, URL de requ&#xEA;te :&quot;+requestURL+&quot;\nContenu :\n&quot; ; +data);<br />}</code>style=&quot;text-align:left&quot;&gt;<code>fonction dataEvent(data, requestURL) {<br />script. log(&quot;Donn&#xE9;es re&#xE7;ues, URL de demande :&quot;+requestURL+&quot;\nContenu :\n&quot; ; +data);<br />}</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}
{% endtabs %}

## Méthodes spécifiques au module \(l'objet local\)

Certains modules ont des méthodes spécifiques qui sont utiles si vous voulez avoir des comportements spécifiques ou envoyer des données complexes ou automatisées. Ces méthodes font partie de l'objet Javascript **local**, en fonction du module dans lequel il s'exécute.

{% tabs %}
{% tab title="OSC" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>send(</b><em>address, arg1, arg2, arg3, ...</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Cela envoie un message OSC &#xE0; toutes les sorties activ&#xE9;es de
          ce module.</p>
        <p><em><b>adresse</b></em> est l&apos;adresse du message</p>
      </th>
      <th style="text-align:left"><code>local.send(&quot;/myAddress&quot; ;, 1, .5, &quot;cool&quot; ;);</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| **sendTo\(**_ip, port, adresse, arg1, arg2, arg3, ..._**\)** | Même chose que la méthode **envoi** mais envoi à un _**ip spécifique**_ et _**port,**_ ignoring le module's output. | `local.sendTo("192.168.1.255" ;, 9000, "/myAddress" ;, 1, .5f, "cool" ;);` |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="MIDI" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **sendNoteOn\(**_channel, pitch, velocity_**\)** | Cela enverra un événement Note On sur le périphérique MIDI de sortie du module. | `local.sendNoteOn (1, 12, 127);` |
| **sendNoteOff\(**_channel, pitch_**\)** | Cela enverra un événement Note Off sur le périphérique MIDI de sortie du module. | `local.sendNoteOff (1, 12);` |
| **sendCC\(**_channel, pitch, velocity_**\)** | Cela enverra un événement Control Change sur le périphérique MIDI de sortie du module. | `local.sendCC (3, 20, 65);` |
| **sendSysEx\(**_byte1, byte2, byte3, ..._**\)** | Cela enverra un message SysEx sur le périphérique MIDI de sortie du module. Vous pouvez ajouter autant d'arguments que vous le souhaitez dans le message SysEx. | `local.sendSysex (10, 15,20,20,0);` |
| **sendPitchWheel\(**_channel, value_**\)** | Cela enverra un événement Pitch Wheel sur le périphérique MIDI de sortie du module. | `local.sendPitchWheel (3, 2000);` |
| **sendChannelPressure\(**_channel, value_**\)** | Cela enverra un événement Channel Pressure sur le périphérique MIDI de sortie du module. | `local.sendChannelPressure (1, 67);` |
| **sendAfterTouch\(**_channel, note, value_**\)** | Cela enverra un événement After Touch sur le périphérique MIDI de sortie du module. | `local.sendAfterTouch (3, 20, 65);` |
{% endtab %}

{% tab title="DMX" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **send\(**_startChannel, value1, value2, ..., valueN_**\)** | Ceci enverra des **valeurs DMX** en démarrant par le **canal DMX** spécifié. Vous pouvez ajouter autant de valeurs que nécessaire, et même mélanger des tableaux de valeurs et des valeurs simples. Les valeurs vont de 0 à 255. | `local.send(32, 255);` |

{% endtab %}

{% tab title="Serial/UDP/TCP" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **send\(**_message_**\)** | Cela enverra la chaîne passée en caractères ASCII. | `local.send("Ceci est mon message");` |
| **sendBytes\(**_byte1, byte2, \[bytes\], ..._**\)** | Cela enverra tous les bytes passés tels quels. Les octets peuvent être regroupés dans des tableaux ou simplement disposés un par un, ou un mélange de tableaux et d'octets. | `local.sendBytes(30,210, [255,0,0], 5);` |
| **sendTo\(**_ip, port, message_**\)** | **\[UDP Only\]** Même chose que la méthode **send**, mais enverra vers un _**ip**_ et un _**port**_ spécifiques, en ignorant la sortie du module. | `local.sendTo("192.168.1.255", 8888, "This is my message");` |
| **sendBytesTo\(**_ip, port, byte1, byte2, \[bytes\], ..._**\)** | **\[UDP Only\]** Identique à la méthode **sendBytes**, mais enverra vers un _**ip**_ et un _**port**_ spécifiques, en ignorant la sortie du module. | `local.sendBytesTo("192.168.1.255", 8888, 30,210, [255,0,0], 5);` |
{% endtab %}

{% tab title="HTTP" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **sendGET\(**_url_**\)** | Cela enverra une demande HTTP GET. Vous pouvez ajouter des paramètres à la fin de l'argument _**url**_, comme pour toute URL GET. | `local.sendGET("https://httpbin.org/anything?myValue1=1&myValue2=super");` |
| **sendPOST\(**_url, param1, value1, param2, value2, ..._**\)** | Cela enverra une requête HTTP POST. Après avoir spécifié le _**url**_, vous pouvez ajouter une paire de valeurs qui sont respectivement le nom du _**paramètre**_ et sa _**valeur**_. | `local.sendPOST( "https://httpbin.org/anything", "myValue1", 1, "myValue2", 2);` |
{% endtab %}

{% tab title="System" %}
| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **launchApp\(**_appPath, arguments_**\)** | Lance une application au chemin fourni avec les arguments fournis | `local.launchApp("myApp.exe", "-p myOption");` |
{% endtab %}
{% endtabs %}

