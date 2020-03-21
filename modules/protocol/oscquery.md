# OSCQuery

Ce module permet de contrôler n'importe quelle application compatible OSCQuery, récupérer tous les paramètres et synchroniser ses valeurs avec Chataigne.

![](../../.gitbook/assets/oscquery.png)

## Parameters

* **Sync Data :** Une fois connectée à l'application, ce bouton va provoquer une resynchronisation de tout l'abre de données. Il n'y a pour l'instant pas de support de synchronisation temps-réel, donc la synchro doit être manuelle à chaque fois que la structure de données dans le logiciel cible a changé.
* **Output :** C'est ici que tu gères les paramètres de connection à l'application OSCQuery.
  * **Local :** Cela permet de forcer l'envoi sur le même ordinateur et ne pas utiliser le champs "Remote Host". Pratique pour basculer rapidement entre un contrôle d'ordinateur à distance ou en local.
  * **Remote host :** C'est l'adresse IP de l'ordinateur à qui tu te connectes pour synchroniser les données. Tu dois désactiver "Local" pour pouvoir utiliser ce paramètres.
  * **Remote port :** Le port sur lequel se connecter pour synchroniser les données OSCQuery.
  * **Custom OSC Port :** C'est le port sur lequel envoyer les messages OSC. C'est en général le même que le "Remote Port", mais dans certains cas comme avec VDMX, tu dois utiliser  2 ports différents, un pour OSCQuery et un pour OSC, dans ce cas tu peux activer ce paramètre et préciser le port OSC.
  * **Auto detect:** Cette option \(en haut à droite dans l'en-tête de la section\) est pratique pour détecter les logiciels compatibles OSCQuery sur le réseau, et assigner automatiquement bon paramètres pour ce logiciel. Il est possible que cette option ne marche pas, surtout si tu n'as pas le service d'impression "Bonjour" d'Apple installé.

