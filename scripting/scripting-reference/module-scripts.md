# Module Scripts

Les scripts de module vous permettent d'ajouter une gestion plus complexe et plus spécifique des valeurs, d'aider à l'analyse des données provenant de flux réseau ou série qui suivent une API spécifique.

C'est également la façon de créer des [Modules personnalisés](../../modules/custom-modules/), où vous pouvez définir vos propres valeurs et paramètres, et faire exécuter la logique principale par des scripts.

## Fonctions communes des modules

Tous les scripts fonctionnant à l'intérieur d'un module auront un ensemble commun de fonctions qui pourront être ajoutées au script. Ces fonctions ne sont pas nécessaires pour exécuter le script.

| Méthode                                          | Description                                                                                                                                                                       | Exemple                                                                                                                                                                                                           |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **function moduleParameterChanged(**_param_**)** | Cette fonction sera appelée chaque fois qu'un paramètre de ce module aura changé, c'est-à-dire un paramètre ou un déclencheur à l'intérieur du panneau "Parameters" de ce module. | `function moduleParameterChanged(param){ script.log("Param changed : "+param.name) ; }` _\`\`_                                                                                                                    |
| **function moduleValueChanged(**_param_**)**     | Cette fonction sera appelée à chaque fois qu'une valeur de ce module aura changé, c'est-à-dire un paramètre ou un déclencheur à l'intérieur du panneau "Values" de ce module.     | `function moduleValueChanged(value) { if(value.isParameter()) { script.log("Valeur du module changée : "+value.name+") > "+value.get()) ; }else { script.log("Valeur du module déclenchée : "+value.name) ; }  }` |

## Fonctions spécifiques aux modules

Certains modules ont des rappels de fonctions spécifiques qui sont utiles si vous souhaitez personnaliser l'analyse des données reçues de ce module.

{% tabs %}
{% tab title="OSC" %}
| Méthode | Description | Exemple |
| ------- | ----------- | ------- |

| **oscEvent(**_address, args_**)** | <p>Cette fonction sera appelée à chaque fois qu'un message du CSP sera reçu.</p><p><em><strong>adresse</strong></em> est l'adresse du message du CSP<br><em><strong>args</strong></em> est un tableau contenant tous les arguments de l'OSC Message</p> | <p><code>fonction oscEvent(adresse, args) {</code><br><code>script.log("OSC Message reçu "+adresse+" ;, "+args.length+" ; arguments" ;);</code></p><p><code>}</code></p> |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
{% endtab %}

{% tab title="MIDI" %}
| Méthode | Description | Exemple |
| ------- | ----------- | ------- |

| **noteOnEvent (**_canal, hauteur, vitesse_**)** | <p>Cette fonction sera appelée à chaque fois qu'un événement noteOn sera reçu.</p><p>Les arguments sont respectivement le canal, le pas et la vitesse de cette event.</p> | <p><code>function noteOnEvent(channel, pitch, velocity) {</code><br><code>script.log("Note on received "+channel+" ;, "+pitch+" ;, "+velocity);</code><br><code>}</code></p> |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| **noteOffEvent (**_canal, hauteur, vitesse_**)** | <p>Cette fonction sera appelée à chaque fois qu'un événement noteOff sera reçu.</p><p>Les arguments sont respectivement le canal, le pas et la vitesse de cette event.</p> | <p><code>function noteOffEvent(channel, pitch, velocity) {</code><br><code>script.log("Note off received "+channel+" ;, "+pitch+" ;, "+velocity);</code><br><code>}</code></p> |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

| **ccEvent (**_canal, nombre, valeur_**)** | <p>Cette fonction sera appelée à chaque fois qu'un événement noteOff sera reçu.</p><p>Les arguments sont respectivement le canal, le nombre et la valeur de cet événement.</p> | <p><code>fonction ccEvent(channel, number, value) {</code><br><code>script.log("ControlChange reçu "+channel+" ;, "+number+" ;, "+value);</code><br><code>}</code></p> |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| **sysExEvent(**_data_**)** | <p>Cette fonction sera appelée à chaque fois qu'un événement sysEx sera reçu.</p><p>L'argument est un tableau d'octets contenant les données sysEx.</p> | <p><code>fonction sysExEvent(data) { script.log("Sysex Message reçu, "+data.length+" ; bytes :" ;);</code><br><code>for(var i=0 ; i &#x3C; ; data.length ; i++) {</code><br><code>script.log(" ; > ; "+data[i]);</code><br><code>}</code><br><code>}</code></p> |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| **channelPressureEvent (**_channel, value_**)** | Cette fonction sera appelée à chaque fois qu'un événement ChannelPressure sera reçu. Les arguments sont respectivement le canal et la valeur de cet événement. | `fonction channelPressureEvent(channel, value) { script.log("Channel Pressure received "+channel+" ;, "+value); }` |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |

| **afterTouchEvent (**_canal, note, valeur_**)** | Cette fonction sera appelée à chaque fois qu'un événement afterTouch sera reçu. Les arguments sont respectivement le canal, la note et la valeur de cette event. | `fonction afterTouchEvent(channel, note, value) { script.log("After Touch received "+channel+" ;, "+note+" ;, "+value); }` |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
{% endtab %}

{% tab title="Serial/UDP/TCP" %}
| Méthode | Description | Exemple |
| ------- | ----------- | ------- |

| **dataReceived**_**(**données_**)** | <p>Cette fonction sera appelée à chaque fois que des données auront été reçues.</p><p>Si le protocole du Module's est réglé sur <em><strong>Lines,</strong></em> alors l'argument <strong>data</strong> sera une chaîne contenant la ligne, sans la terminaison \n.</p><p>Sinon, les données seront un tableau d'octets contenant les data.</p> | <p><code>fonction dataReceived(data) {</code></p><p><code>script.log("Données reçues : "+data);</code></p><p><code>}</code></p> |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
{% endtab %}

{% tab title="HTTP" %}
| Méthode | Description | Exemple |
| ------- | ----------- | ------- |

| **dataEvent(**_data, requestURL_**)** | <p>Cette fonction sera appelée chaque fois que le module aura reçu une réponse de une demande.<br><em><strong>data</strong></em> est le contenu de la réponse</p><p><em><strong>demandeURL</strong></em> est l'url de la demande initiale.</p> | <p><code>fonction dataEvent(data, requestURL) {</code><br><code>script.log("Données reçues, URL de requête :"+requestURL+"\nContenu :\n" ; +data);</code><br><code>}</code>style="text-align:left"><code>fonction dataEvent(data, requestURL) {</code><br><code>script. log("Données reçues, URL de demande :"+requestURL+"\nContenu :\n" ; +data);</code><br><code>}</code></p> |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
{% endtab %}

{% tab title="System" %}
| Method                                             | Description                                                                                                                                                                                                                                                                                     | Example                                                                                                                                       |
| -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **processDataReceived(**_data, originCommand_**)** | <p>Cette fonction est appelée après un appel à <em><strong>launchProcess()</strong></em> et que blocking est à <em>false.</em><br><em><strong>data</strong></em> contient la sortie du process<br><em><strong>originCommand</strong></em> contient la commande qui a déclenché cette sortie</p> | <p><code>function processDataReceived(data, command) {</code><br><code>script.log("Data received",data,command);</code><br><code>}</code></p> |


{% endtab %}
{% endtabs %}

## Méthodes spécifiques au module (l'objet local)

Certains modules ont des méthodes spécifiques qui sont utiles si vous voulez avoir des comportements spécifiques ou envoyer des données complexes ou automatisées. Ces méthodes font partie de l'objet Javascript **local**, en fonction du module dans lequel il s'exécute.

{% tabs %}
{% tab title="OSC" %}
| Méthode                                              | Description                                                                                                                                                                                                                                                                 | Exemple                                                                                                                                                                                                                                                                 |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **send(**_address, arg1, arg2, arg3, ..._**)**       | Envoie un message OSC à toutes les sorties activées du module. _**address**_ est l'adresse du message                                                                                                                                                                       | `local.send("myAddress", 1, .5f, "cool");`                                                                                                                                                                                                                              |
| **sendTo(**_ip, port, address, arg1, arg2, ..._**)** | Même fonctionnement que **send**, mais envoie le message à une adresse _**ip**_ et un _**port**_ spécifique, sans tenir compte des sorties du module.                                                                                                                       | `local.sendTo("192.168.0.30", 9000, "myAddress", 1, .5f);`                                                                                                                                                                                                              |
| **match(**_address, pattern_**)**                    | Vérifie si l'adresse _**address**_ correspond au schéma _**pattern**_, conformément à la [spécification OSC](http://opensoundcontrol.org/spec-1\_0.html). Les astérisques, etc sont reconnus.                                                                               | `if (local.match(address, "/testPattern")) ...`                                                                                                                                                                                                                         |
| **register(**_pattern, callbackFunc_**)**            | Enregistre une fonction du script à appeler quand un message correspondant à  _**pattern**_ est reçu. _**callbackFunc**_ est le nom de la fonction à appeler. **\[Note]** Si le module contient plusieurs scripts, ce nom de fonction est enregistré pour tous les scripts. | <p><code>function init() {</code><br><code>local.register("/testPattern", "testPatternCallback");</code><br><code>}</code><br><code>function testPatternCallback(address, args) {</code><br><code>script.log("Received message "+address);</code><br><code>}</code></p> |
{% endtab %}

{% tab title="MIDI" %}
| Méthode                                        | Description                                                                                                                                                     | Exemple                              |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| **sendNoteOn(**_channel, pitch, velocity_**)** | Cela enverra un événement Note On sur le périphérique MIDI de sortie du module.                                                                                 | `local.sendNoteOn (1, 12, 127);`     |
| **sendNoteOff(**_channel, pitch_**)**          | Cela enverra un événement Note Off sur le périphérique MIDI de sortie du module.                                                                                | `local.sendNoteOff (1, 12);`         |
| **sendCC(**_channel, pitch, velocity_**)**     | Cela enverra un événement Control Change sur le périphérique MIDI de sortie du module.                                                                          | `local.sendCC (3, 20, 65);`          |
| **sendSysEx(**_byte1, byte2, byte3, ..._**)**  | Cela enverra un message SysEx sur le périphérique MIDI de sortie du module. Vous pouvez ajouter autant d'arguments que vous le souhaitez dans le message SysEx. | `local.sendSysex (10, 15,20,20,0);`  |
| **sendPitchWheel(**_channel, value_**)**       | Cela enverra un événement Pitch Wheel sur le périphérique MIDI de sortie du module.                                                                             | `local.sendPitchWheel (3, 2000);`    |
| **sendChannelPressure(**_channel, value_**)**  | Cela enverra un événement Channel Pressure sur le périphérique MIDI de sortie du module.                                                                        | `local.sendChannelPressure (1, 67);` |
| **sendAfterTouch(**_channel, note, value_**)** | Cela enverra un événement After Touch sur le périphérique MIDI de sortie du module.                                                                             | `local.sendAfterTouch (3, 20, 65);`  |
{% endtab %}

{% tab title="DMX" %}
| Méthode                                                   | Description                                                                                                                                                                                                                      | Exemple                |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| **send(**_startChannel, value1, value2, ..., valueN_**)** | Ceci enverra des **valeurs DMX** en démarrant par le **canal DMX** spécifié. Vous pouvez ajouter autant de valeurs que nécessaire, et même mélanger des tableaux de valeurs et des valeurs simples. Les valeurs vont de 0 à 255. | `local.send(32, 255);` |
{% endtab %}

{% tab title="Serial/UDP/TCP" %}
| Méthode                                                      | Description                                                                                                                                                                 | Exemple                                                           |
| ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **send(**_message_**)**                                      | Cela enverra la chaîne passée en caractères ASCII.                                                                                                                          | `local.send("Ceci est mon message");`                             |
| **sendBytes(**_byte1, byte2, \[bytes], ..._**)**             | Cela enverra tous les bytes passés tels quels. Les octets peuvent être regroupés dans des tableaux ou simplement disposés un par un, ou un mélange de tableaux et d'octets. | `local.sendBytes(30,210, [255,0,0], 5);`                          |
| **sendTo(**_ip, port, message_**)**                          | **\[UDP Only]** Même chose que la méthode **send**, mais enverra vers un _**ip**_ et un _**port**_ spécifiques, en ignorant la sortie du module.                            | `local.sendTo("192.168.1.255", 8888, "This is my message");`      |
| **sendBytesTo(**_ip, port, byte1, byte2, \[bytes], ..._**)** | **\[UDP Only]** Identique à la méthode **sendBytes**, mais enverra vers un _**ip**_ et un _**port**_ spécifiques, en ignorant la sortie du module.                          | `local.sendBytesTo("192.168.1.255", 8888, 30,210, [255,0,0], 5);` |
{% endtab %}

{% tab title="HTTP" %}
| Méthode                                                        | Description                                                                                                                                                                             | Exemple                                                                                                               |
| -------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **sendGET(**_url_**)**                                         | Cela enverra une demande HTTP GET. Vous pouvez ajouter des paramètres à la fin de l'argument _**url**_, comme pour toute URL GET.                                                       | <p><code>local.sendGET(</code></p><p><code>"https://httpbin.org/anything?myValue1=1&#x26;myValue2=super");</code></p> |
| **sendPOST(**_url, param1, value1, param2, value2, ..._**)**   | Cela enverra une requête HTTP POST. Après avoir spécifié le _**url**_, vous pouvez ajouter une paire de valeurs qui sont respectivement le nom du _**paramètre**_ et sa _**valeur**_.   | `local.sendPOST( "https://httpbin.org/anything", "myValue1", 1, "myValue2", 2);`                                      |
| **sendPUT(**_url, param1, value1, param2, value2, ..._**)**    | Cela enverra une requête HTTP PUT. Après avoir spécifié le _**url**_, vous pouvez ajouter une paire de valeurs qui sont respectivement le nom du _**paramètre**_ et sa _**valeur**_.    | `local.sendPUT( "https://httpbin.org/anything", "myValue1", 1, "myValue2", 2);`                                       |
| **sendPATCH(**_url, param1, value1, param2, value2, ..._**)**  | Cela enverra une requête HTTP DELETE. Après avoir spécifié le _**url**_, vous pouvez ajouter une paire de valeurs qui sont respectivement le nom du _**paramètre**_ et sa _**valeur**_. | `local.sendPATCH( "https://httpbin.org/anything", "myValue1", 1, "myValue2", 2);`                                     |
| **sendDELETE(**_url, param1, value1, param2, value2, ..._**)** | Cela enverra une requête HTTP DELETE. Après avoir spécifié le _**url**_, vous pouvez ajouter une paire de valeurs qui sont respectivement le nom du _**paramètre**_ et sa _**valeur**_. | `local.sendDELETE( "https://httpbin.org/anything", "myValue1", 1, "myValue2", 2);`                                    |
{% endtab %}

{% tab title="System" %}
| Méthode                                                                                     | Description                                                                                                                                                                                                                                                                                   | Exemple                                                |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| **launchApp(**_appPath, arguments_**)**                                                     | Lance une application au chemin fourni avec les arguments fournis                                                                                                                                                                                                                             | `local.launchApp("myApp.exe", "-p myOption");`         |
| <p><strong>launchCommand(</strong><em>command, silentMode</em><strong>)</strong></p><p></p> | Lance une commande                                                                                                                                                                                                                                                                            | `local.launchCommand("myApp.exe", true);`              |
| **launchProcess(**_command, blocking_**)**                                                  | <p>Lance un process et retourne la sortie.<br>Si <em><strong>blocking</strong></em><strong>  </strong> est false, la sortie sera envoyée dans <em>processDataReceived(data)</em><br><em></em>Sinon, le programme sera bloqué le temps du process, et le contenu sera directement renvoyé.</p> | `var result = local.launchCommand("myApp.exe", true);` |
| **getRunningProcesses()**                                                                   | Liste les process en cours                                                                                                                                                                                                                                                                    | `var result = local.getRunningProcesses();`            |
| **isProcessRunning(**_process_**)**                                                         | Check if un process est en cours                                                                                                                                                                                                                                                              | `var isRunning = local.isProcessRunning("MyApp.exe"`   |
{% endtab %}
{% endtabs %}
