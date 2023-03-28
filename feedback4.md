# Parcours PHP : Review apprenant 1 :fire:

## 1 : Global :earth_africa:
**Concernant Le routing**
- Je vois que sur ton fichier racine "public/index.php", tu as commencé à paramètrer via la méthode map de ton router ($router->map()) les routes de ton application. Je t'invite à documenter un peu plus chacune de tes routes (vers quelle page la route me mène t'elle) afin que tu t'y retrouve un peu plus. Ensuite je pense que tu as compris les paramètres que prenaient en compte la méthode map. Le premier est la méthode utilisée, le deuxième l'url qui sera tapée dans la barre, le troisième est un tableau qui réfère à la méthode du controller qui sera appelée ainsi que le nom de la Class controlleur auquel la méthode refèrre et le dernier est le nom que tu donne à la route. Je t'invite à regarder [la documentation de AltoRouter](https://altorouter.com/usage/mapping-routes.html) pour plus d'informations.
Si je met cette méthode au clair c'est parce que je vois que tu réfère à des controllers (et des méthodes) qui n'existent pas dans ton arborecense. De ce fait, ton application ne peut fonctionner car dans une architecture MVC, le controlleur est le lien entre le modèle et la vue. Il est donc nécessaire de créer un fichier controlleur pour chaque modèle que tu souhaites gérer.
**Concernant le Model**
- Tu as entièrement compris à quoi réfère le modèle dans le MVC, Les propriétés et méthodes sont correctement déclarés, et un paramètre d'entrée et de sortie sont à chaque fois déclarés afin de fortifier la sécurité du code.
**Concernant la Vue**
- Tu as compris la notion de templating et la notion de rendu de données dynamiques via les données que tu essayes de récuperer de ton controlleur!
**Concernant le Controller**
- Je pense que c'est sur cette partie que tu titubes finalement. Je vois que tu as bien compris le rôle du controlleur, à savoir vérifier / passer l'information entre la vue et le modèle. En revanche n'hésite pas à revoir la notion d'instanciation dans la programmation orientée objet, ainsi que la notion de fonctions. Je vis que dans le controller "TeachersController" tu essayes ce code suivant :
```php
// VERIFICATION QUE L'UTILISATEUR AIT LES DROITS
$teachersModel = new Teachers
teachers();
$teachers = $teachersdModel->findAll();

$this->show("teachers/teachers_list", [
    'teachers' => $teachers
]);
```
Le fait d'instancier un nouvel objet à partir de Teachers ne vérifie en aucun cas les droits de l'utilisateur. Il va juste te créér un objet vide avec les propritétés et méthodes de Class Teachers? N'oublie pas le ";" en fin de ligne, c'est primordial en PHP et dans bien d'autres langages. Penses également à placer les "()" après l enom de class que tu souhaites instancier.
Tu essayes ensuite d elancer une fonction "teachers()", celle ci n'est pas dévlarer dans ton code. C'est pourquoi je t'invite à revoir les notions de fonctions de fonctions et la OOP afin que tu puisses bien comprendre leurs fonctionnement.
Le code en dessous est bon! Ce qui m'amène au prochain point...
**L'organisation de travail**
C'est sur ce point ou progresser te ferais passer au niveau supérieur. Je vois que tu as compris la notion de MVC, Tu comprends également la notion de Class (excépté l'instanciation à revoir) et l'appel aux méthodes me montre que tu comprend la notion de getter / setter / propriétés privées / public.
Par contre tu essaye de TOUT FAIRE EN MÊME TEMPS.... ET D'UNE TRAITE! C'est ce qui cause ta perte.
Je reprend l'éxemple de ton fichier "TeachersController.php" :
Tu essayes d'instancier un objet, de lancer une fonction, de rendr eune vue... alors que ton routing lui même pose problème. Ce qui cause une couche de problèmes à gérer, et complexifie énormement la phase de débuggage.
En bonne pratique de travail il est plus productif de :
- Découper les tâches que tu te fixes en plusieurs étapes.
- Organiser ton travail
- Tester ton code dès que tu implèmente une nouvelle fonctionalité.
Pour l'exemple de c eprojet je me serais fixé :
- D'afficher une page sans erreur (même vide, ce qui permet de valider que le routing fonctionne)
- Afficher une vue pour la page professeurs, sans données (ce qui me permet de mettre en place le controlleur et la méthode render de ce dernier avec la vue necessaire)
- instancier un objet à partir de Teachers, récupérer les professeurs de la BDD, voir ce que je récupère (pense aux fonctions var_dump + die)

## 2 : Keep up :fire:
Le fait que tu as essayé de compléter en partie chaque points du projet nous donne un rendu à double tranchant :
- Quand pon regarde le code on voit que tu as compris la plupart de snotions, c'est top! et ça permet de définir un axe de travail!
- Quand on essaye de lancer ton projet on ne voit absolument rien, c'est dommage. 
En appliquant les bonnes méhodes et avec un peu d'entrainement je suis sûr que tu vas vite progresser! Tu y es presque, continue comme ça!