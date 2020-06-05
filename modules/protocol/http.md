# HTTP

Ce module permet la communication bi-directionnelle à des pages web et des webservices, en envoyant et récupérant des données depuis les sites internet et des APIs.

![](../../.gitbook/assets/http.png)

## Parameters

* **Base Address :** En considérant chaque module HTTP comme un service, il y a de fortes chances que la plupart des requêtes aient la même adresse de base. Si c'est le cas, tu peux spécifier ici cette base, ce qui est pratique au moment où le service est relocalisé sur une autre URL, car tu n'auras qu'à changer ce paramètre, sans avoir à changer chaque commande.
* **Auto-add :** Si activé, à la réception de données structurées en _JSON_, des values seront créées avec la même hiérarchie que le JSON reçu. 
* **Clear Values :** Permet de facilement supprimer toutes les values.

