# Introduction à la State Machine

![Une state machine plut&#xF4;t complexe.](../.gitbook/assets/statemachine-1.png)

La State Machine vous permettra de créer vos propres règles d'interaction pour contrôler en temps réel l'ensemble de votre système. Comme son nom l'indique, c'est une machine à états, ce qui signifie que vous pouvez créer différents états, appelés "State", chacun étant un groupe de règles que vous pouvez activer ou désactiver comme vous le souhaitez. Vous pouvez également créer des transitions entre eux, ce qui permet de créer des interactions évolutives.

Lors de la création d'une interaction, vous devrez d'abord créer un état qui contiendra les règles.

{% hint style="success" %}
\*\*SHORTCUTS

* **Alt + glisser ou MSB** \(bouton du milieu de la souris\) :\*\* déplacer la vue pour naviguer dans un monde de merveilles infini !  
* **Shift + scroll de la souris :** Zoom avant/arrière pour voir plus de choses, ou avoir une UI agrandie
* **Ctrl + C, Ctrl + V, Ctrl + D :** Copier, coller, dupliquer des éléments \(ceci s'applique à tous les éléments des listes et des vues, c'est-à-dire les Etats, les Mappings, les Actions, les Modules, les Séquences...\)
{% endhint %}

## States

Les States sont des conteneurs qui contiendront des règles d'interaction différentes. Ils peuvent être activés et désactivés manuellement ou automatiquement, et vous pouvez créer une transition entre eux.

Actuellement, il existe deux types de règles : [**Actions**](actions.md) **et** [**Mappings**](mappings.md)**.**

Lorsque vous créez une interaction, vous voudrez soit un contrôle ponctuel pour déclencher des commandes : ce sont les [**Actions**](actions.md)**, soit un contrôle continu pour lier des valeurs d'entrée à des paramètres : ce sont les** [**Mappings**](mappings.md).

### Transitions et réseau de State

Les transitions ont des cas d'utilisation multiples :

* Elles peuvent agir comme une action qui transférera automatiquement l'activation d'un State à un autre State. Elles agissent comme une action, et peuvent même avoir des conséquences de sorte que vous pouvez avoir des comportements différents lorsque vous venez d'un état ou d'un autre. 
* Ils peuvent être utilisés pour relier plusieurs états entre eux. C'est ce que nous appelons un réseau de State.

{% hint style="info" %}
C'est pourquoi il est utile de créer des transitions entre plusieurs States lorsque vous voulez vous assurer qu'il n'y a qu'un seul State actif à la fois dans un groupe de States.
{% endhint %}

En les reliant entre eux, vous pouvez avoir autant de réseaux de State que vous le souhaitez, ce qui signifie que vous pouvez toujours avoir plusieurs States actifs en même temps.

