# Special Modules

En plus de tous les modules disponibles, il existe des modules spéciaux qui sont déjà intégrés dans Chataigne et que vous pouvez utiliser comme n'importe quel autre module.

* **Sequences :** Ce module permet de contrôler vos [_sequences_](../the-time-machine-sequences/introduction-to-the-time-machine.md#sequence). Vous pouvez par exemple jouer, reprendre, arrêter une séquence, aller à un repère spécifique, régler un temps spécifique, sauter en avant ou en arrière dans le temps. 
* **State Machine :** Ce module permet de contrôler vos [états](../la-machine à états / introduction à la machine à états.md). Vous pouvez par exemple activer un état, déclencher une [Action](../the-state-machine/actions.md), activer ou désactiver une [Action ](../the-state-machine/actions.md)ou un [Mapping](../the-state-machine/mappings.md)... 
* **Custom Variables :** Ce module vous donne des informations sur l'état actuel de vos variables personnalisées que vous pouvez utiliser dans [Conditions ](../the-state-machine/actions.md#conditions)et [Mapping inputs](../the-state-machine/mappings.md#input), et permet également de contrôler ces variables. Par exemple, vous pouvez définir la valeur d'une variable, ou ajouter +1 à une variable. 
* **Generic :** C'est un module très pratique qui permet de contrôler n'importe quel paramètre de votre projet, et d'obtenir la valeur de n'importe lequel de ces paramètres également.  Il permet également d'enregistrer des messages dans le Logger, ce qui est très pratique pour tester et déboguer votre projet. Vous pouvez également y insérer un script personnalisé, sans savoir s'il est intéressant ou non, mais il est là.

{% hint style="warning" %}
N'utilisez les commandes génériques que lorsqu'aucune autre commande n'est adaptée à cela. Par exemple, vous devriez préférer utiliser les commandes de séquence plutôt que la commande générique "Définir la valeur du paramètre" si vous voulez contrôler la chronologie d'une séquence.
{% endhint %}

d#conditions)and [Mapping inputs](../the-state-machine/mappings.md#input), and allows also control over those variables. For instance you can set a variable's value, or add +1 to a variable. 
* **Generic :** This is a very handy module that allows to control any parameter of your project, and get the value of any of those parameters as well.  It allows also to log messages into the Logger, which is very practical when testing out and debugging your project. You can insert custom script there as well, not sure if it's interesting at all but it's there.

{% hint style="warning" %}
Only use the Generic commands when no other command is suited for that. For example, you should prefer using Sequence commands over Generic "Set parameter value" command if you want to control a sequence's timeline.
{% endhint %}

