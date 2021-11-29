# Mapping Layer

Un Mapping Layer contient une automatisation, qui est une animation basée sur des courbes. Cette courbe est ensuite utilisée comme entrée pour un mapping. Vous pouvez ensuite utiliser ce layer comme un mapping et ajouter des filtres et des sorties

Le Mapping Layer possède plusieurs fonctionnalités faciliant la création d'animations.

![](../.gitbook/assets/screenshot\_1.png)

## The Recorder

Le recorder vous permet d'enregistrer dans le temps une valeur d'entrée et de la convertir en une courbe. Il vous suffit de choisir une valeur d'entrée, d'activer le paramètre **Arm **et de commencer à jouer. La valeur de ce paramètre sera alors affichée en rouge dans le calque et à l'arrêt de la séquence, elle sera automatiquement convertie en une courbe modifiable.

![Recording a perlin noise from the Generator module](../.gitbook/assets/recording.gif)

## Painting Automation&#x20;

{% hint style="info" %}
Cette fonctionnalité n'est disponible qu'à partir de la version 1.7.x
{% endhint %}

Vous pouvez tracer une courbe en maintenant la touche **Ctrl + Shift** enfoncée et en faisant glisser votre souris de gauche à droite dans la ligne de temps du Mapping layer. Votre dessin sera alors automatiquement converti en une automation modifiable.

![Drawing and modifying a mapping curve](../.gitbook/assets/automation-painting.gif)

## Setting range and timeline navigation&#x20;

{% hint style="info" %}
Cette fonctionnalité n'est disponible qu'à partir de la version 1.7.x
{% endhint %}

Vous pouvez choisir les valeurs minimum et maximum de votre automation à partir du paramètre "Range" dans le panel. Vous pouvez également la rendre "infinie" en désactivant ce paramètre. Vous pourrez alors vous déplacer dans le layer en utilisant **Alt **(et **Alt+Shift** pour le zoom) et en faisant glisser la souris verticalement..
