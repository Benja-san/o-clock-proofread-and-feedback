# Parcours PHP : Review apprenant 4 :fire:

## 1 : Global :earth_africa:
**Concernant Le routing**
- Je vois que sur ton fichier racine "public/index.php", tu as commencé à paramétrer via la méthode map de ton router ($router->map()) les routes de ton application. Je t'invite à documenter un peu plus chacune de tes routes (vers quelle page la route me mène t'elle) afin que tu t'y retrouves un peu plus. Ensuite je pense que tu as compris les paramètres que prenait en compte la méthode map. Le premier est la méthode utilisée, le deuxième l'url qui sera tapée dans la barre, le troisième est un tableau qui réfère à la méthode du contrôleur qui sera appelée ainsi que le nom de la Class contrôleur auquel la méthode refère et le dernier est le nom que tu donnes à la route. Je t'invite à regarder [la documentation de AltoRouter](https://altorouter.com/usage/mapping-routes.html) pour plus d'informations.
Si je mets cette méthode au clair c'est parce que je vois que tu réfères à des contrôlers (et des méthodes) qui n'existent pas dans ton arborecense. De ce fait, ton application ne peut fonctionner car dans une architecture MVC, le contrôleur est le lien entre le modèle et la vue. Il est donc nécessaire de créer un fichier contrôleur pour chaque modèle que tu souhaites gérer.
**Concernant le Model**
- Tu as entièrement compris à quoi réfère le modèle dans le MVC. Les propriétés et méthodes sont correctement déclarées, et un paramètre d'entrée et de sortie sont à chaque fois déclarés afin de fortifier la sécurité du code.
**Concernant la Vue**
- Tu as compris la notion de templating et la notion de rendu de données dynamiques via les données que tu essayes de récuperer de ton contrôleur!
- Pense à modifier tes inputs afin qu'ils correspondent plus à la donnée que souhaite saisir l'utilisateur. Cela améliore l'ux mais aussi la sécurisation de données (Par exemple le choix de statuts que tu as mis en input de type texte... mériterait de changer pour un select)
**Concernant le Contrôleur**
- Je pense que c'est sur cette partie que tu titubes finalement. Je vois que tu as bien compris le rôle du contrôleur, à savoir vérifier / passer l'information entre la vue et le modèle. En revanche n'hésite pas à revoir la notion d'instanciation dans la programmation orientée objet, ainsi que la notion de fonctions. Je vois que dans le contrôleur "TeachersController" tu essayes ce code suivant :
```php
// VERIFICATION QUE L'UTILISATEUR AIT LES DROITS
$teachersModel = new Teachers
teachers();
$teachers = $teachersdModel->findAll();

$this->show("teachers/teachers_list", [
    'teachers' => $teachers
]);
```
Le fait d'instancier un nouvel objet à partir de Teachers ne vérifie en aucun cas les droits de l'utilisateur. Il va juste te créér un objet vide avec les propriétés et méthodes de Class Teachers. N'oublie pas le ";" en fin de ligne, c'est primordial en PHP et dans bien d'autres langages. Pense également à placer les "()" après le nom de class que tu souhaites instancier.
Tu essayes ensuite de lancer une fonction "teachers()", celle-ci n'est pas déclarer dans ton code. C'est pourquoi je t'invite à revoir les notions de fonctions et la OOP afin que tu puisses bien comprendre leur fonctionnement.
Le code en dessous est bon ! Ce qui m'amène au prochain point...
**L'organisation de travail**
C'est ce point qui te ferait passer au niveau supérieur. Je vois que tu as compris la notion de MVC, Tu comprends également la notion de Class (excepté l'instanciation à revoir) et l'appel aux méthodes me montre que tu comprends la notion de getter / setter / propriétés privées / publiques.
Par contre tu essayes de tout faire en même temps... et d'une traite !
Je reprends l'exemple de ton fichier "TeachersController.php" :
Tu essayes d'instancier un objet, de lancer une fonction, de rendre une vue... alors que ton routing lui-même pose problème. Ce qui cause une couche de problèmes à gérer, et complexifie énormement la phase de débuggage.
En bonne pratique de travail il est plus productif de :
- Découper les tâches que tu te fixes en plusieurs étapes.
- Organiser ton travail
- Tester ton code dès que tu implèmentes une nouvelle fonctionnalité.
Pour l'exemple de ce projet je me serais fixé :
- D'afficher une page sans erreur (même vide, ce qui permet de valider que le routing fonctionne)
- Afficher une vue pour la page professeurs, sans données (ce qui me permet de mettre en place le contrôleur et la méthode render de ce dernier avec la vue nécessaire)
- Instancier un objet à partir de Teachers, récupérer les professeurs de la BDD, voir ce que je récupère (pense aux fonctions var_dump + die)

## 2 : Keep up :fire:
Le fait que tu as essayé de compléter en partie chaque point du projet nous donne un rendu à double tranchant :
- Quand on regarde le code on voit que tu as compris la plupart des notions, c'est top ! Et ça permet de définir un axe de travail !
- Quand on essaye de lancer ton projet on ne voit absolument rien, c'est dommage. 
En appliquant les bonnes méhodes et avec un peu d'entraînement je suis sûr que tu vas vite progresser ! Tu y es presque, continue comme ça !