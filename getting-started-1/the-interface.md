# L'Interface

L'interface peut faire un peu peur à la première ouverture, mais un peu de courage, tu vas voir tout va prendre du sens après avoir fait un rapide tour de la bête.

![](../.gitbook/assets/interface_notes.png)

### Notes générales

L'interface est basée sur un sous-système appelé "Organic UI", qui inclut un méchanism de "ShapeShifter.

En gros, ça veut dire que tu peux supprimer, ajouter et déplacer les différents panneaux, et changer la disposition. Puis tu peux sauvegarder ces différents dispositions en fonction de ce sur quoi tu es en train de travailler.

### 1. Les Modules

Ce premier panneau est ton point de démarrage. C'est ici que tu peux créer les différents modules, chacun étant une connection vers un logiciel ou un périphérique. Au moment de créer un projet, la première chose à faire est de faire une liste des logiciels et périphériques avec lesquels tu vas intéragir, et créer les modules correspondants ici. Tu peux trouver plus d'infos sur les modules à la section [Modules](the-modules.md).

### 2. La State Machine

Cette section te permettra de créer tes propres règles d'intéraction pour avoir un contrôle temps-réel de ton système. C'est une machine à état, ce qui veut dire que tu peux créer différents "States", et chaque state est un ensemble de règles que tu peux activer et désactiver quand tu veux. Tu peux aussi créer des transitions entre ces états, ce qui te permettra de créer des intéractions évolutives. Tu peux trouver plus d'infos dans la section [State Machine](../the-state-machine/introduction-to-the-state-machine.md) .

### 2. La Time Machine \(ou Sequence Editor\)

Cette section de permet de créer et d'éditer des séquences pour faire de la création temporelle. Plus d'info dans la section [Time Machine.](../the-time-machine-sequences/introduction-to-the-time-machine.md)

### 3. L' Inspector \(Editeur de propriétés\)

L'inspector est ton panneau principal d'édition, tu vas y passer un paquet de temps ! Tout ce que tu peux sélectionner sera affiché en détails dans ce panneau. Tu pourras ensuite éditer les différentes propriétés de l'objet sélectionné. Si tu sélectionnées un autre élément, alors l'affichage dans ce panneau changera pour montrer les propriétés de ce nouvel élément sélectionné.

### 4. Le Logger

The Logger est ton ami bavard. Il te donnera des infos sur ce qu'il se passe dans le logiciel, si quelque chose c'est bien ou mal passé, mais également t'affichera d'autres infos comme les adresses IP de ton ordinateur. Tu peux aussi afficher des messages personnalisés dedans pour vérifier des données et suivre ce qu'il se passe dans le logiciel quand ton projet devient plus complexe.

### 5. Le panneau "Help"

Ce panneau est un pense-bête idéal pour commencer, et t'affichera des informations et des raccourcis clavier sur l'élément que tu survoles avec la souris.

### 6. Les Warnings

Le panneau Warning rassemble toutes les erreurs détectées dans le logiciel comme des liens cassés, des serveurs OSC ou TCP mal initialisés, etc.

## Suite

Interface, check. Maintenant on va s'amuser avec les [Modules ](the-modules.md)!

