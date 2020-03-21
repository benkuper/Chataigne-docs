# TCP Client

Ce module permet de se connecter en tant que client à un serveur TCP.

![](../../.gitbook/assets/tcpclient.png)

## Parameters

* \*\*\*\*

  **Parameters**

  * **Protocol :** C'est la méthode à utiliser pour interpréter les données entrantes et sortantes.
    * **Lines :** Cela découpera les données par ligne. C'est largement utilisé par les utilisateurs Arduino pour facilement communiquer avec les cartes.
    * **Raw :** Cela va créer une valeur par octet reçu. C'est pratique si tu crées ton propre script d'interprétation des données.
    * **Data255 :** C'est un protocole spécial qui découpe les données à chaque réception du byte 255 . C'est un protocole personnel et très efficace pour envoyer des bytes avec découpage rapide, et même envoyer des couleurs en acceptant de perdre un byte de précision. Par contre cela ne permet pas d'envoyer des float ou des 32bit integers.
    * **COBS :** Cela interprète les données selon le mechanisme ****_COBS_**.** Si tu ne connais pas, check donc la [page Wikipedia](https://en.wikipedia.org/wiki/Consistent_Overhead_Byte_Stuffing).
  * **Auto Add :** Ajoutes automatiquement des values quand des données sont reçues. Garde cette option activée tant que tu veux ajouter automatiquement des values, puis désactive quand tu as finis d'ajouter des values.
  * **Message structure :** Cela décide de comment interpréter le message reçu. Ca dépend du protocole choisi.
  * **First value is the name :** Si activé, le message reçu aura un format attendu d'au moins 2 arguments : la première est le nom de la valeur, et les autres sont la valeur actuelle.
  * **Output :** Cette section gère les paramètres d'envoi des données.  _Si ton module n'a pas vocation à envoyer des messages, mais uniquement recevoir, alors je te conseille de désactiver cette section \(avec le bouton rouge à gauche du titre\). Dans la liste des modules dans le panel Modules", tu verras que l'icône "Outgoing Data" deviendra cachée au moment de désactiver l'envoi._
    * **Local :** Cela permet de forcer l'envoi sur le même ordinateur et ne pas utiliser le champs "Remote Host". Pratique pour basculer rapidement entre un contrôle d'ordinateur à distance ou en local.
    * **Remote host :** C'est l'adresse IP de l'ordinateur à qui tu envoies les données. Tu dois désactiver "Local" pour pouvoir utiliser ce paramètres.
    * **Remote port :** Le port sur lequel envoyer les messages.
  * **Pass-through :** Cette section permet le transfert direct des données **non-filtrées** à tous les modules de type Streaming, i.e. [Serial](serial.md), [UDP](udp.md), [TCP Client](tcp-client.md) and [TCP Server](tcp-server.md). Ce transfert ne passant pas par le système de gestion des données de Chataigne, il est optimisé pour être effectué le plus rapidement possible.

{% hint style="success" %}
Si tu veux utiliser l'envoi et la réception de données TCP,  je recommande [**PacketSender**](https://packetsender.com/)**,** qui est un très bon outils de test, gratuit et cross-platform !
{% endhint %}

