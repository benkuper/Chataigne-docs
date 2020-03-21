# Special Modules

En plus de tous les modules disponibles, il existe des modules spéciaux qui sont déjà intégrés dans Chataigne et que vous pouvez utiliser comme n'importe quel autre module.

* **Sequences :** Ce module permet de contrôler vos [_sequences_](../the-time-machine-sequences/introduction-to-the-time-machine.md#sequence). Vous pouvez par exemple jouer, reprendre, arrêter une séquence, aller à un repère spécifique, régler un temps spécifique, sauter en avant ou en arrière dans le temps. 
* **State Machine :** Ce module permet de contrôler vos [états](https://github.com/benkuper/Chataigne-docs/tree/1563252dcff2f882d499d8566be3279004a77e43/la-machine%20à%20états%20/%20introduction%20à%20la%20machine%20à%20états.md). Vous pouvez par exemple activer un état, déclencher une [Action](../the-state-machine/actions.md), activer ou désactiver une [Action ](../the-state-machine/actions.md)ou un [Mapping](../the-state-machine/mappings.md)... 
* **Custom Variables :** Ce module vous donne des informations sur l'état actuel de vos variables personnalisées que vous pouvez utiliser dans [Conditions ](../the-state-machine/actions.md#conditions)et [Mapping inputs](../the-state-machine/mappings.md#input), et permet également de contrôler ces variables. Par exemple, vous pouvez définir la valeur d'une variable, ou ajouter +1 à une variable. 
* **Generic :** C'est un module très pratique qui permet de contrôler n'importe quel paramètre de votre projet, et d'obtenir la valeur de n'importe lequel de ces paramètres également.  Il permet également d'enregistrer des messages dans le Logger, ce qui est très pratique pour tester et déboguer votre projet. Vous pouvez également y insérer un script personnalisé, sans savoir s'il est intéressant ou non, mais il est là.

{% hint style="warning" %}
N'utilisez les commandes génériques que lorsqu'aucune autre commande n'est adaptée à cela. Par exemple, vous devriez préférer utiliser les commandes de séquence plutôt que la commande générique "Définir la valeur du paramètre" si vous voulez contrôler la chronologie d'une séquence.
{% endhint %}

