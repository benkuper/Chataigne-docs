# DMX

Le module DMX permet de contrôler des boitiers DMX comme Enttec OpenDMX, Enttec DMX Pro, Enttec DMX MkII et également d'enovoyer de l'Artnet.

![](../../.gitbook/assets/dmx.png)

## Parameters

* **DMX Type :** Le type de DMX que tu veux utiliser. Ca dépend tu matos que tu as.
* **Connected :** Affiche l'état de la connection à ton périphérique.

**DMX Device parameters :**

* **Use fixed send rate :** Si cette option est activée, les données DMX seront envoyées à interval régulier. Sinon elle seront envoyées à chaque déclenchement de commande.
* **Target send rate : **Si "fixed send rate" est activée, c'est la fréquence d'envoie des données DMX.
* **Enable receive (DMXPro / Artnet seulement) :** Active la réception de données DMX.
* **Port (OpenDMX / DMXPro seulement) :** Le périphérique sur lequel se connecter.

### ArtNet specific :

![](../../.gitbook/assets/artnet.png)

* **Interface :** L'interface réseau à utiliser pour se connecter au node ArtNet. En fonction de l'OS, tu voudras sûrement tester différents options, mais "All (Default)" marchera probablement.
* **Subnet :** Le subnet sur lequel envoyer les données.
* **Universe :** L'univers DMX sur lequel envoyer les données.
* **Node Name :** The nom du node Artnet de Chataigne qui sera montré aux autres logiciels (si "Enable Receive" est activé).

{% hint style="warning" %}
ArtNet peut présenter des problèmes sur certaines plateformes, si tu as des connaissances pour implémenter ce protocole en C++, tu peux me contacter !
{% endhint %}

