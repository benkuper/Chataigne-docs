# Multiplex \(1.8\)

Attendez, autre chose que les actions et les mappings ?   
Oui ! Enfin non... mais oui !   
Le multiplex est un moyen d'élaborer plusieurs actions et mappings à la fois. 

  
Si vous avez plusieurs valeurs qui nécessitent le même filtrage, ou les mêmes conditions à vérifier, une liste de boutons ou de curseurs que vous voulez traiter de la même manière, alors vous trouverez un moyen de ne pas avoir à dupliquer les actions et les mappages. 

### Un seul pour tous 

Les multiplex fonctionnent avec des listes : un multiplex possède un paramètre de comptage qui définit le nombre d'itérations qu'il traite. Vous pouvez ensuite créer autant de listes que vous le souhaitez, qui seront de la même longueur que le compte du multiplex. Après avoir paramétré cela, vous pouvez ajouter des actions et des correspondances dans le multiplex, et elles obtiendront automatiquement de nouvelles capacités. 

Vous pourrez utiliser une liste comme entrée pour les conditions, ou lier un paramètre spécifique dans Conséquence, Mapping Output ou Mapping Filter à un élément de la liste. 

Ensuite, tous les éléments sont vérifiés, et lorsqu'un élément d'une liste est modifié, cela déclenchera le processus des actions ou des mappages qui ont cette liste en entrée et la traitera en connaissance de l'index de l'élément source dans sa liste. L'ensemble du processus conservera ensuite ces informations pour un usage ultérieur, comme par exemple la liaison d'un élément sur le même index d'un autre lien. 

C'est très pratique d'avoir le même processus pour beaucoup d'éléments mais un résultat spécifique pour chacun d'entre eux.

### Liaison des paramètres 

Un paramètre peut être lié de différentes manières : 

* Dans une sortie de cartographie, il peut être lié à l'une des valeurs d'entrée 
* Dans un multiplex, il peut être lié soit à l'index associé \(basé sur 0 ou sur 1\) de l'élément source qui a déclenché le processus, soit à un élément de la liste du multiplex au même index que l'élément source. 

{% hint style="success" %}
Pour les String Parameters, il est possible d'utiliser des jokers pour créer une combinaison plus complexe de différents liens : 

* **{index}** sera remplacé par l'index \(basé sur 1\) 
* **{index0}** sera remplacé par l'indice \(basé sur 0\) 
* **{input:0}** sera remplacé par la première valeur de l'entrée de cartographie 
* **{list:names}** sera remplacé par l'élément ayant le même index dans la liste appelée "Names" \(conversion camelCase\) 

De cette façon, quelque chose comme   
**Bonjour {list:names}, vous êtes le numéro du patient {index}**   
se traduirait par  
**Bonjour Léon, vous êtes le patient numéro 5**
{% endhint %}



