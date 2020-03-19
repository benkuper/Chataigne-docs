# Histoire et philosophie de Chataigne

## L' Histoire

### Pourquoi faire Chataigne ?

Au fil des années, j'ai travaillé sur beaucoup de projets pour lesquels j'ai du créer des outils très similaires. Même si ces outils étaient fonctionnels, comme ils étaient à chaque fois créés in situ, ils n'étaient ni optimisés, ni facile à prendre en main, je ne pouvais donc pas souvent laisser sereinement ces outils en autonomie aux artistes avec qui je travaillais.

Il y a quelques années, j'ai décidé de concentrer cette énergie dans un outil qui conviendrait à la plupart des usages auquel j'ai été confronté pendant mes projets, et qui pourrait être utilisé à la fois par des techniciens du spectacle \(lumière, vidéo, son..\) et les artistes. Après quelques années de test et usage privé, j'ai décidé de redévelopper une solution optimisée basée sur JUCE/C++, et de l'ouvrir au public en mettant ce projet à la fois gratuit et open-source. 

### Pourquoi "Chataigne" ?

L'histoire derrière le choix de ce nom la implique une histoire d'amour, et mon envie de m'en rappeler. Et puis c'est marrant surtout.

## La Philosophie

### Qu'est-ce que c'est exactement, Chataigne ?

Dans la plupart des projets artistiques intégrant de la technologie, les différents créateurs vont utiliser plusieurs logiciels et matériels différents : un logiciel pour contrôler le son, un ou plusieurs pour la vidéo, un logiciel ou une console pour la lumière, des capteurs, moteurs...

Dans ces systèmes, la communication et synchronisation entre les différentes parties peut ne pas être évident, et rapidement devenir trop complexe. Un autre facteur important est que chacun de ces logiciels requiert potentiellement une expérience technique spécifique.

Chataigne a pour but d'être le "chef" de cette orchestre technologique : bien qu'il ne fasse rien de visible pour le public de lui-même, il sera l'élément qui aura connaissance du projet dans son ensemble et s'assurera que chacun des acteurs du système reçoive ce dont il a besoin. Je travaille dur pour que l'interface de Chataigne soit compréhensible et utilisable à la fois pour les techniciens et les artistes, en espérant qu'il puisse devenir un terrain de rencontre et de travail commun entre les techniciens et les artistes.

### Pourquoi et quand devrais-je l'utiliser ?

Tout d'abord, Chataigne est un "chef d'orchestre" et ne "joue pas" d'instrument lui-même, vous n'aurez donc pas beaucoup d'intérêt à l'utiliser sans "orchestre". Chataigne ne prend de sens que si vous avez un projet dans lequel vous voulez contrôler et synchroniser plusieurs logiciels et matériels ensemble.

#### Chataigne est principalement un outil pour les spectacles et installation interactives

Si vous avez un projet impliquant plusieurs logiciels et / ou périphériques physiques, vous voudrez probablement synchroniser le tout à un endroit unique et dédié à cette tâche plutôt que de se retrouver avec des connections croisées et complexes entre les différents logiciels.

#### Chataigne supporte à la fois le temps-réel "interactive" et le contrôle temporel linéaire.

Chataigne tourne autour de deux concepts : la [State Machine](../the-state-machine/introduction-to-the-state-machine.md) \(Machine à état\) et la [Time Machine ](../the-time-machine-sequences/introduction-to-the-time-machine.md)\(Sequences\)

La State Machine s'occupera de toutes les intéractions temps réel, avec des règles d'intéraction qui peuvent aller des plus simples concepts à des systèmes complexes en fonction des besoins.

La Time Machine s'occupera de toute ce qui est géré dans le temps. Elle utilise principalement des timelines classiques, qui peuvent déclencher des événements à des moments précis, ou animer des paramètres et des couleurs dans le temps. Elle intègre aussi un support basique de l'audio, mais si vous avez des besoins plus complexe en son, vous devrez utiliser un autre logiciel dédié, que vous pourrez ensuite contrôler depuis Chataigne.

#### Chataigne contient également plusieurs outils secondaires pour tester et prototyper rapidement

Chataigne contient beaucoup de "perles cachées" et d'outils qui s'intègrent avec le reste du logiciel, mais qui peuvent aussi être utilisés séparement, comme le [Router ](../modules/the-module-router.md)qui peut rapidement rediriger les informations d'un logiciel à un autre logiciel et convertir les données en même temps. Vous découvrirez ces outils au fur et à mesure de l'utilisation du logiciel et de la lecture de cette documentation.

## Ensuite

Maintenant que tu as une bonne idée générale, rentrons dans le vif du sujet ! Découvrons  [L'interface](the-interface.md)

