# Exemple 2 : Presets d'un système de particules

Une autre utilisation des variables personnalisées consiste à stocker différentes valeurs prédéfinies.

Imaginons que vous ayez un système de particules réalisé en Unity ou Processing, ou une vidéo de particules en Resolume ou MadMapper. Votre système est contrôlé par OSC, vous pouvez donc envoyer plusieurs valeurs OSC pour en changer le style.

Les variables personnalisées peuvent vous aider à créer des ensembles de paramètres que vous souhaitez conserver et envoyer

![4 variables dans un groupe, avec 2 présélections.](../../.gitbook/assets/particles.png)

Une fois que vous avez différents préréglages, vous pouvez commencer à les interpoler avec les commandes du module spécial

[Un Mapping qui prend un signal d'entrée et l'utilise pour interpoler entre 2 presets](../../.gitbook/assets/interpolate.png)

Voici le résultat dans la vue des variables personnalisées

![](../../.gitbook/assets/particle_anim.gif)
