# Introduction aux Scripts

## Scripter dans  Chataigne

Bien que Chataigne essaie de permettre le plus de choses possible sans coder, certains mécanismes et comportements sont tout simplement trop complexes pour bénéficier d'un système uniquement visuel. Lorsque le cas se présente, les scripts sont là pour combler ce trou. Ils ont été intégrés dans Chataigne de telle sorte que leur empreinte est très petite et qu'ils semblent sans faille.

[Exemple d'un script chargé](https://github.com/benkuper/Chataigne-docs/tree/c35ac6b398b503ce64c710770212db510b933fa8/.gitbook/assets/module_scripts.png)

Les scripts peuvent être trouvés et créés dans différents endroits de Chataigne, en fonction de leur rôle :

* dans [Modules ](../getting-started-1/the-modules.md) : voir la section [Scripts de module](scripting-reference/module-scripts.md). 
* dans [Conditions ](../the-state-machine/actions.md#conditions) : voir la section [Scripts de condition](scripting-reference/condition-scripts.md). 
* dans [Filtres ](../the-state-machine/mappings.md#filters) : voir la section [Scripts de filtre](scripting-reference/filter-scripts.md).

### Création d'un script

Lors de la création d'un script, le conteneur de script sera vide. Vous pouvez alors choisir soit de charger un fichier déjà existant en cliquant sur "Parcourir...", soit de créer un nouveau fichier en cliquant sur l'icône bleue avec un crayon à l'intérieur \[\(je sais qu'il est très petit et non reconnaissable\)\]. Cela créera le fichier et l'ouvrira dans votre éditeur par défaut.

{% hint style="info" %}
La plupart des systèmes n'ont pas d'éditeur par défaut pour les fichiers Javascript. Je recommande fortement d'utiliser [**Sublime Text**](https://www.sublimetext.com/) ou [**VS Code**](https://code.visualstudio.com/) _\*\*_ comme éditeur Javascript par défaut !
{% endhint %}

Lors de la création d'un nouveau script, le fichier nouvellement créé sera déjà rempli de contenu visant à guider les nouveaux utilisateurs. Ce contenu est généré dynamiquement en fonction de l'objet à partir duquel vous avez créé votre script. Par exemple, si vous le créez dans un module OSC, vous aurez un contenu générique, mais aussi un contenu spécifique au module ainsi qu'un contenu spécifique à l'OSC.

Les scripts sont compilés et interprétés en temps réel, ce qui signifie que chaque fois que vous enregistrez votre fichier de script, il sera automatiquement rechargé dans Chataigne. À tout moment, vous pouvez consulter le panneau [Logger](../getting-started-1/the-interface.md#4-the-logger) pour voir le résultat de la compilation :

* Si le script est bien écrit et se compile, le Logger vous dira qu'il s'est chargé avec succès et vous verrez dans l'inspecteur du script un point vert comme dans l'image ci-dessus. 
* Si le script est mal écrit ou comporte des erreurs de compilation, le Logger indiquera qu'il y a une erreur et affichera l'erreur et la ligne d'erreur, ce qui est très rapide et pratique pour corriger les bogues. Lorsqu'un script a des problèmes de chargement, un avertissement s'affiche également, et un point rouge est visible sur l'inspecteur du script.

