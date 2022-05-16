# Serial

Permet de te connecter et communiquer avec n'importe quel périphérique série comme les cartes Arduino.

![](../../.gitbook/assets/serial.png)

## Parameters

* **Protocol :** C'est la méthode à utiliser pour interpréter les données entrantes et sortantes.
  * **Lines :** Cela découpera les données par ligne. C'est largement utilisé par les utilisateurs Arduino pour facilement communiquer avec les cartes.
  * **Raw :** Cela va créer une valeur par octet reçu. C'est pratique si tu crées ton propre script d'interprétation des données.
  * **Data255 :** C'est un protocole spécial qui découpe les données à chaque réception du byte 255 . C'est un protocole personnel et très efficace pour envoyer des bytes avec découpage rapide, et même envoyer des couleurs en acceptant de perdre un byte de précision. Par contre cela ne permet pas d'envoyer des float ou des 32bit integers.
  * **COBS :** Cela interprète les données selon le mechanisme **** _COBS_**.** Si tu ne connais pas, check donc la [page Wikipedia](https://en.wikipedia.org/wiki/Consistent\_Overhead\_Byte\_Stuffing).
* **Auto Add :** Ajoutes automatiquement des values quand des données sont reçues. Garde cette option activée tant que tu veux ajouter automatiquement des values, puis désactive quand tu as finis d'ajouter des values.
* **Message structure :** Cela décide de comment interpréter le message reçu. Ca dépend du protocole choisi.
* **First value is the name :** Si activé, le message reçu aura un format attendu d'au moins 2 arguments : la première est le nom de la valeur, et les autres sont la valeur actuelle.
* **Port :** Le port série sur lequel se connecter.
* **Baud rate :** Le vitesse à laquelle se connecter. Ce paramètre est décidé dans le programme sur le périphérique. Sur Arduino, ce paramètre est décidé avec la fonction _**Serial.begin(\<baudrate>)**;_
* **Is connected :** Affiche si le périphérique est connecté ou non.&#x20;
* **Pass-through :** Cette section permet le transfert direct des données **non-filtrées** à tous les modules de type Streaming, i.e. [Serial](serial.md), [UDP](udp.md), [TCP Client](tcp-client.md) and [TCP Server](tcp-server.md). Ce transfert ne passant pas par le système de gestion des données de Chataigne, il est optimisé pour être effectué le plus rapidement possible.

{% hint style="success" %}
Désactiver ce module déconnectera automatiquement le périphérique, ce qui veut dire que tu n'as pas besoin de ferme Chataigne ou de supprimer le module pour connecter la carté à un autre logiciel. Par exemple si tu veux uploadre un nouveau sketch à ta carte Arduino, tu peux juste désactiver le module, uploader le sketch, puis réactiver le module.
{% endhint %}

{% hint style="success" %}
En activant "Log Incoming", tu peux utiliser Chataigne comme un très simple moniteur série !
{% endhint %}
