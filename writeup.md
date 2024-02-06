# WriteUp

Explication de la résolution de chacun des exercices

## Exercice intro2.rs
On comprend que l'utilisateur veut afficher un message.

Or il utilise la macro printline! qui n'existe pas.

Donc pour que le code fonctionne il faut changer la macro "printline!" par "println!" ou "print"

## Exercice variable6.rs

On voit que l'utilisateur veut afficher la constante  NUMBER.

Or il déclare la constante de la manière suivante "const NUMBER = 3;"

On sait que quand on déclare une constante le type de valeur doit être obligatoirement indiqué.

Donc pour que le programme fonctionne on a déclaré la constante comme suit en ajoutant le type : "const NUMBER: i32 = 3;"

## Exercice functions4.rs

On voit que l'utilisateur veut assigner une valeur à  la variable answer en utilisant la fonction square qui est censé retourner le carré de la variable indiqué en paramètre.

Or ici on voit que dans la fonction square, à la ligne 14 il y a un point virgule.

On sait que le compilateur l'interprète comme une instruction sachant que se qu'on souhaite c'est une expression car on veut on veut simplement obtenir le résultat de la multiplication sans conditions.

Donc pour le programme fonctionne il faut enlever le point virgule de la ligne 14.

## Exercice if3.rs

On comprend ici qu'en fonction d'un str l'utilisateur veut retourner un integer.

Or ici on a à la ligne 11 un float et à la ligne 15 un str.

On sait grace à la suite du code (l.18 à l.27), que la valeur attendu est un integer.

Donc pour que le programme fonctionne j'ai remplacer la float de la ligne 11 par "2" et  le str de la 15 par 0.

## Exercice primitive_types6.rs

L'objectif ici est que la variable "second" contienne la deuxième valeur du tableau pour que le test soi valide.

Or ici la variable "numbers" est un tuple.

On sait que l'index d'un tuple commence à 0.

Donc pour que "second" contienne la 2eme valeur du tableau il faut lui donner la valeur d'index 1.

Soit let second = numbers.1;

## Exercice vecs2.rs
L'objectif ici est de modifier chaque élément des vecteur v par sa valeur multiplié par 2.

Pour la fonction vec_loop, on sait que la boucle parcours chaque élément du vecteur, "element" est une référence mutable de chaque élément du vecteur (un pointeur vers l'élément). Pour accéder à la valeur pointé et donc pouvoir la modifier on utilise l'opérateur "*" devant "element".
Enfin on procède a une multiplication standard.

Pour la fonction vec_map, on sait que chaque élément du vecteur sont immuables, la modification de celui ci n'est donc pas possible.
A l'aide de la méthode "map" qui crée un nouvel itérateur et "collect" qui assemble les résultats dans un nouveau vecteur, on va créer un nouveau vecteur contenant le double de chaque valeur contenu dans le vecteur v initiale.
A noter que comme la multiplication est effectué dans la méthode "map" Rust sait effectué l'opération sans pointer vers la valeur à l'aide de "*".
Donc pour que le code fonctionne on ajoute "element*2" à la ligne 27. 

## Exercice move_semantics1

