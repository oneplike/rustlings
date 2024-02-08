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

## Exercice move_semantics6.rs

L'objectif du programme est de récupérer le dernier caractère de la chaîne "data" en utilisant la fonction "get_char", puis de convertir cette même chaîne en majuscules à l'aide de la fonction "string_uppercase", et finalement de l'afficher.

Or ici, pour éviter de perdre "data" après l'appel à "get_char", on utilise "data.clone()" pour créer une copie de "data" et passer cette copie à "get_char". Cela permet de garder "data" intacte et utilisable par la suite.

On sait que cloner une donnée crée une nouvelle instance identique qui peut être utilisée indépendamment de l'originale. Cela résout le problème de perdre l'accès à "data" après son utilisation dans "get_char". De plus, passer une référence à "data" à "string_uppercase" (au lieu de la transférer) permet d'utiliser "data" sans en prendre possession, ce qui est conforme à l'intention de ne pas modifier l'original de manière permanente.

Donc pour que le programme fonctionne on utilise "clone" pour permettre à "get_char" d'opérer sur une copie de "data", préservant ainsi l'original pour un usage ultérieur. Ensuite, "string_uppercase" reçoit une référence à "data", évitant ainsi la modification ou la perte de l'original. Cette approche maintient l'accès à "data" tout au long du programme tout en accomplissant les opérations voulues.

## Exercice structs3.rs

L'objectif du programme est de gérer des colis, vérifier s'ils vont à l'étranger et calculer leurs frais d'envoi.

Or ici, le code initial ne précisait pas ce que les fonctions "is_international" et "get_fees" devaient retourner. Cela posait problème car Rust a besoin de savoir à l'avance le type de chaque donnée.

On sait que pour que Rust comprenne et exécute correctement le code, il faut dire clairement quel type de résultat attendre de chaque fonction.

Donc, en ajoutant "bool" comme type de retour de "is_international"  et "u32" pour "get_fees" pour donner le montant des frais, le programme peut maintenant fonctionner. 

## Exercice enums3.rs
L'objectif du programme est de gérer différents types de messages pour modifier l'état d'un objet "State" en ajustant sa couleur, sa position, son état de sortie (quit), ou son message.

Or ici, dans le code initial, l'énumération "Message" est déclarée mais elle est vide, ce qui signifie qu'il n'y a pas de moyens de spécifier les différents types de messages à traiter dans la méthode "process". Sans variantes dans l'énumération, il est impossible de définir les actions à entreprendre en fonction des messages reçus.


Donc, la correction apporte des variantes à l'énumération "Message": "ChangeColor" pour modifier la couleur, "Echo" pour définir un message, "Move" pour déplacer la position, et "Quit" pour signaler que l'exécution doit cesser. Ensuite, dans la méthode "process", un "match" est utilisé pour décomposer le message reçu et appeler la méthode appropriée sur l'instance de "State" en fonction du type de message.

## Exercice strings4.rs

L'objectif du programme est de montrer les différentes manières de passer des chaînes de caractères à deux fonctions distinctes : "string_slice", qui prend une référence à une chaîne ("&str"), et "string", qui prend la propriété d'une chaîne ("String").

1.string_slice("blue");
Or ici, la chaîne "blue" est une chaîne str, ce qui signifie qu'elle est déjà une référence ("&str"). La fonction "string_slice" est donc choisie car elle accepte une référence ("&str") en argument.


2.string("red".to_string());
La méthode "to_string" est utilisée pour convertir la chaîne str "red" en une chaîne proprement ("String"). La fonction "string" est choisie car elle accepte une propriété ("String") en argument.

3.string(String::from("hi"));
La méthode "String::from" est utilisée pour créer une nouvelle chaîne à partir de la chaîne str "hi", ce qui retourne une propriété ("String"). La fonction "string" est donc choisie car elle accepte une propriété ("String") en argument.

4.string("rust is fun!".to_owned());
La méthode "to_owned" est utilisée pour créer une nouvelle chaîne à partir de la chaîne littérale "rust is fun!", ce qui retourne une propriété ("String"). La fonction "string" est donc choisie car elle accepte une propriété ("String") en argument.

5.string_slice("nice weather".into());
La méthode "into" est utilisée pour convertir la chaîne str "nice weather" en une référence ("&str"). La fonction "string_slice" est donc choisie car elle accepte une référence ("&str") en argument.

6.string(format!("Interpolation {}", "Station"));
La fonction "format" crée une nouvelle chaîne en interpolant les valeurs, ce qui retourne une propriété ("String"). La fonction "string" est donc choisie car elle accepte une propriété ("String") en argument.

7.string_slice(&String::from("abc")[0..1]);
La méthode "String::from" crée une nouvelle chaîne à partir de la chaîne str "abc", puis l'opérateur slice "[0..1]" est utilisé pour obtenir une slice de la première lettre, qui est une référence ("&str"). La fonction "string_slice" est donc choisie car elle accepte une référence ("&str") en argument.

8.string_slice(" hello there ".trim());
La méthode "trim" est utilisée pour supprimer les espaces avant et après la chaîne " hello there ", ce qui retourne une référence ("&str"). La fonction "string_slice" est donc choisie car elle accepte une référence ("&str") en argument.

9.string("Happy Monday!".to_string().replace("Mon", "Tues"));
La méthode "to_string" est utilisée pour convertir la chaîne str "Happy Monday!" en une chaîne proprement ("String"). Ensuite, la méthode "replace" est utilisée pour remplacer "Mon" par "Tues" dans cette chaîne, ce qui retourne une propriété ("String"). La fonction "string" est donc choisie car elle accepte une propriété ("String") en argument.

10.string("mY sHiFt KeY iS sTiCkY".to_lowercase());
La méthode "to_lowercase" est utilisée pour convertir la chaîne "mY sHiFt KeY iS sTiCkY" en minuscules, ce qui retourne une propriété ("String"). La fonction "string" est donc choisie car elle accepte une propriété ("String") en argument.

## Exercice modules3.rs

On doit ajouter les bon module pour que le programme compile, comme indiqué dans l'indice, les modules "UNIX_EPOCH" et "SystemTime" sont dans le module "std::time", on a plus qu'a mettre le chemin absolue vers chacun des modules pour que ça compile.

## Exercice hashmaps3.rs

La correction apportée dans le code utilise la méthode "entry" pour accéder à une équipe dans la hashmap ou insérer une nouvelle équipe si elle n'existe pas encore. Ensuite, elle met à jour les scores des équipes en conséquence, en ajoutant les buts marqués et concédés à chaque équipe respectivement. Cette approche garantit que chaque équipe est correctement mise à jour en fonction des résultats de chaque match.

## options3.rs

 La variable y est consommée dans le match, ce qui signifie qu'elle n'est plus disponible pour être utilisée après. Cela génère une erreur de "valeur inutilisée" pour y à la fin du code.

On sait que dans Rust, lorsqu'on fait correspondre une référence dans un match, il est possible d'utiliser ref pour ne faire correspondre que la référence au lieu de déstructurer la valeur. Cela permet de conserver la propriété de la variable d'origine après le match.

Donc, pour corriger le code sans supprimer la ligne y, on peut utiliser ref dans le match pour faire correspondre une référence à p, et ainsi permettre à y d'être utilisée après le match.

## errors6.rs

L'objectif du programme est de gérer les erreurs de manière plus précise lors de la conversion d'une chaîne en entier et lors de la création d'un entier positif non nul à partir de cette valeur entière.

Or ici, le programme précédent utilisait unwrap() pour traiter les erreurs lors de la conversion de la chaîne en entier, ce qui provoquait un arrêt brutal du programme en cas d'erreur. De plus, il ne gérait pas correctement les erreurs de création d'un entier positif non nul.

On sait que unwrap() est une méthode qui déclenche une panique si elle rencontre une erreur, ce qui n'est pas une gestion appropriée des erreurs.

Donc, en ajoutant des lignes de code pour définir un type d'erreur personnalisé (ParsePosNonzeroError) et des fonctions pour convertir les erreurs de création et de conversion en ce type d'erreur personnalisé, nous permettons au programme de gérer plus efficacement les erreurs et de les traiter de manière appropriée sans interrompre brusquement l'exécution.

## generics2.rs

L'objectif du programme est de créer une structure Wrapper qui peut envelopper n'importe quel type de données. Cependant, dans la version initiale du code, la structure Wrapper était conçue uniquement pour stocker des valeurs de type u32, ce qui la rendait moins flexible.

Or ici, dans le test store_str_in_wrapper, nous avons essayé de stocker une chaîne de caractères ("Foo") dans la structure Wrapper, mais cela n'était pas possible avec la version précédente du code car la structure Wrapper n'était pas générique et ne pouvait contenir que des valeurs de type u32.    

Donc, en intégrant les génériques dans la structure Wrapper, nous pouvons maintenant créer des instances de Wrapper avec n'importe quel type de données, ce qui permet au test store_str_in_wrapper de fonctionner correctement en stockant une chaîne de caractères dans la structure Wrapper.

## traits5.rs   

En spécifiant <T: SomeTrait + OtherTrait> dans la signature de some_func, on garantit que la fonction ne sera applicable que sur des instances de types qui respectent simultanément ces deux contraintes. Cela permet à some_func de compiler sans erreurs lorsqu'elle est appelée avec des instances de SomeStruct ou OtherStruct, car ces types sont explicitement déclarés pour implémenter  les deux traits requis. En conséquence, cette approche assure la flexibilité et la sécurité de type, en veillant à ce que la fonction puisse exécuter les opérations demandées sur les objets passés en argument.

