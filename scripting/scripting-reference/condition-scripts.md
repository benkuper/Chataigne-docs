# Scripts de condition

Les cas d'utilisation de Condition Scripts sont plus rares mais peuvent s'avérer pratiques dans des configurations très spécifiques et complexes. Certaines situations sont tout simplement trop complexes ou bizarres pour les réduire à un comportement "si". Vous pouvez alors utiliser un script et décider d'activer cette partie de la condition comme vous le souhaitez.

Par exemple, si je veux détecter une suite de notes à chanter, je pourrais facilement créer un script qui vérifiera automatiquement la prochaine note à chanter afin de valider la condition.

## Méthodes spécifiques à la condition \(l'objet local)

Lorsque des scripts sont exécutés comme condition, l'objet Javascript **local** dispose de méthodes spécifiques pour modifier l'état de validation de cette condition.

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **setValid\(**_value_**\)** | Cela fixe l'état de validation de la condition à la _**value**_ | `local.setValid(true);` |

