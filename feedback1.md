# Parcours PHP : Review apprenant 1 :fire:

## 1 : Global :earth_africa:
- Très bonne séparation du code répartie entre le modèle, le contrôleur et la vue, tu as compris et utilisé le design pattern MVC à bon escient, bien joué :clap: !
- Tu as nommé tes fichiers contrôleurs et modèles de manière claire  :thumbsup: !
- Les modèles créés sont corrects et les propriétés + méthodes fonctionnels. N'hésite pas à typer les propriétés de tes modèles, cela permet de mieux comprendre le code et de mieux gérer les erreurs. De même pour les paramètres d'entrée et de sortie de tes méthodes.
- N'hésite pas à retirer le "code mort" (commentaires, code non utilisé, etc...) afin de garder un code propre et lisible.
- :warning: ATTENTION :warning: La tâche principale du développement back-end est de vérifier l'information passée par l'utilisateur afin d'éviter toute tentative d'action malveillante. Lorsque tu récupères les données venant d'un formulaire utilisateur, n'hésite pas à ajouter des vérifications afin d'être sûr(e) que les données soient correctes et dans le type souhaité, tu peux rajouter les filtres correspondant au type de retour souhaité pour tes fonctions filter_input. Je t'envoie également vers les fonctions [trim](https://www.php.net/manual/en/function.trim.php) et [htmlentities](https://www.php.net/manual/fr/function.htmlentities.php) de php. Concernant tes requêtes via PDO, tu peux également sécuriser le code SQL en utilisant des requêtes dites "préparées". Je t'invite à regarder [la documentation de PDO pour plus d'informations](https://www.php.net/manual/fr/pdo.prepare.php). Petite vidéo bonus si tu veux en savoir plus sur [l'injection sql](https://www.youtube.com/watch?v=ciNHn38EyRc)

## 2 : Lister les professeurs , les étudiants
- Tu as su récupérer les professeurs et les étudiants à partir de la BDD en créant la méthode appropriée dans leur fichier de modèle.
- Tu as préparé un objet correspondant dans le contrôleur et tu as su appeler la méthode créée dans ton modèle pour récupérer les professeurs / élèves. Cependant le nom de tes variables pourrait induire un développeur en erreur. En effet en nommant la variable contenant les enseignants "teacher" ou "student" au singulier, on s'attend naturellement à ce que cette variable contienne un seul objet. Je t'invite à nommer ta variable "teachers" ou "students" pour qu'elle soit plus explicite. De même pour le nom de la méthode "teacher" ou "student" qui gagnerait en lisibilité en s'appelant "getTeachers" ou "getStudents" par exemple. 
- D'autant plus que tu as bien nommé la variable que tu appelles dans ta vue ("teachers" / "students") :thumbsup: !
- Dans ton fichier racine index.php tu aurais pu, dans un souci de cohérence, appeler la route listant tous les étudiants de la même manière que celle listant tous les professeurs pour une meilleure cohérence.

## 3 : Ajouter un étudiant, un professeur
- :warning: ATTENTION :warning: La méthode d'ajout d'élève avec la méthode GET ne contient pas le bon code ! Dans ta hâte, tu as dû laisser le code concernant la logique métier associée aux professeurs dans la méthode dédiée aux élèves.
- La méthode POST est bien cablée, je peux bien ajouter un(e) professeur(e) ou un(e) étudiant(e).

## 3 : Utilisateur et vérification 
- Les rôles sont bien implémentés et également bien associés aux routes selon leurs droits.
- L'accès au dashboard est bien protégé par une connexion !
- La vérification de mot de passe est effective.

## Bonus : Validation de données
- Les vérifications demandées sont bien implémentées pour les champs vides. En revanche, bien que tu vérifies que le statut soit un nombre entier (integer), le but ici est de vérifier qu'il soit compris entre 1 et 2. N'hésite pas à effectuer une petite vérification supplémentaire sur ce champ afin d'être sûr(e) d'obtenir un entier qui soit 1 ou 2.
- Tu as bien implémenté la gestion des erreurs sur le formulaire en cas de données vides. Pour une sécurisation optimale, je t'invite à regarder le point évoqué dans le partie "Global".

## Bonus : Mise à jour d'un étudiant, d'un professeur
Pour cette partie, tu t'es un peu perdu(e) dans la configuration de routing.
- Ta route est bien présente sur le fichier CoreController.php et accessible à partir du rôle User pour les étudiants, du rôle Admin pour les professeurs. (Tu as en revanche dupliqué l'accès "Get" pour les étudiants et donc oublié d'ajouter la partie "POST")
- Sur ton index.php, tu as bien mappé la route avec le format POST, la route comprennant l'id de la ligne à modifier, la bonne méthode qui mène au contrôleur et le bon nom de chemin...
- :warning: Par contre si tu regardes bien ton template d'update, tu verras que sur la génération de l'attribut "action" de ton formulaire, il manque une information (regarde du côté de la génération du lien de suppression si tu veux un indice). 
- Cette information est primordiale afin de récupérer la route et d'accéder au contrôleur lorsque l'utilisateur va cliquer sur le bouton de validation du formulaire ! Et c'est l'unique oubli qui empéchait tes fonctionalités d'update de fonctionner ! :sweat_smile:
- La vérification côté contrôleur est bien implémentée, le modèle également. Si tu veux aller plus loin dans la validation de données je te renvoie au point évoqué dans la partie "Global".

## Bonus : Suppression d'un étudiant, d'un professeur
RAS

## MegaBonus CRUD utilisateur
Tu n'as certainement pas eu le temps de le faire, je t'invite à effectuer cette partie en autonomie quand tu as le temps, histoire de valider le CRUD avec les MVC. Tu as déjà bien compris le concept et la logique, cela te permettra de confirmer l'essai :wink:

## MegaBonus Attaques CSRF
Je t'invite à te renseigner sur ce concept et à le mettre en place sur ton projet. Cela te permettra de sécuriser ton projet et de valider ce point.


