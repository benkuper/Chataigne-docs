# Exemple 1 : Logique de jeu simple

Par exemple, vous pourriez (et des gens l'ont fait !) créer une logique de jeu simple avec des variables personnalisées, en stockant le score actuel et le meilleur score du jeu.

![Groupe de variables personnalisées simples contenant 2 valeurs.](../../.gitbook/assets/custom-variables.png)

Vous pouvez ensuite faire en sorte que n'importe quel événement, par exemple en appuyant sur un bouton, augmente votre score actuel

![Une action qui incrémente le &quot;Score&quot ; variable personnalisée sur chaque bouton Appuyez sur ](../../.gitbook/assets/increment_score.png)

Et enfin, ajoutez une autre action pour vérifier si le score actuel est un certain nombre pour vérifier si le jeu est terminé. Dans cette même action, vous pouvez alors afficher un message de "fin de partie" et également remettre le score actuel à 0.

![Une action qui affiche &quot;YOU WIN&quot ; et réinitialise le score actuel lorsqu'il atteint 10](../../.gitbook/assets/highscore.png)
