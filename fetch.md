# Fetch with JS one 0 one!

## Un peu de background :
Avant de parler de la fonction Fetch, parlons un peu d'applications web. Sur toutes les applications web modernes où tu peux te rendre aujourd'hui. Tu remarqueras que le comportement de navigation diffère un petit peu de l'application Skoule que tu as créé. En effet, que ça soit Instagram, TikTok, Netflix ou Facebook (on reviendra sur ce dernier très vite), tu remarqueras que lorsque tu navigues sur ces applications, tu n'es pas redirigé vers une nouvelle page. Tu restes sur la même page et les données sont chargées dynamiquement. C'est ce que l'on appelle le **Single Page Application** (SPA). C'est une application web qui ne nécessite pas de recharger la page à chaque fois que tu navigues. C'est un comportement qui est très apprécié par les utilisateurs car cela permet de garder une UX fluide et agréable. C'est aussi un comportement qui est très apprécié par les développeurs car cela permet de créer des applications web plus performantes et plus rapides.
Ce comportement SPA est rendu possible par le chargement asyncrone des données sur ta page web en fonction des clics que tu effectues. C'est ce que l'on appelle l' **Ajax**. Ajax est un acronyme qui signifie **Asynchronous JavaScript And XML**. C'est une technique qui permet de charger des données asynchrones sur une page web. C'est une technique qui est très utilisée dans les applications web modernes (IOT / Applications / Web...).
Ainsi, si on imagine ton application Skoule en SPA, lorsque tu passeras de la page (ou de la route) /home vers la page /teachers aucun rechargement de page ne s'effectuera. En revanche, tu verras bien disparaître le contenu propre à la route /home et apparaître le contenu propre à la route /teachers. C'est ce que l'on appelle le **routing**. Surprise ! Tu connais déjà ce terme et tu l'utilises pour ton MVC. 
## Utilité, fonction
Passons maintenant à [l'API (application programming interface) Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch). Cette API propose une méthode du même nom fetch() qui va te permettre via un script en JS d'aller chercher des données comme le ferait ton application mais de manière asyncrone (sans que l'utilisateur ne s'en rende compte). Cette méthode est en majeure partie utilisée pour aller rechercher (ou envoyer) de la donnée sur un back-end (que tu as déjà en PHP par exemple), qui fournira ces données au format **JSON**. Ces back-ends spécifiques servant à fournir et manipuler de la donnée sous ce format ont un nom particulier. On les appelle les **API** (généralement **REST** ou **GRAPHQL**).
Pour faire simple, revoyons ton contrôleur, une fois qu'il a récupéré la donnée des enseignants :
```php	
/**
 * Display teacher 
 *
 * @return void
 */
public function teacher()
{
    $newteacher = new Teacher();

    $teacher = $newteacher->findAll();
    
    $this->show("teacher/teacher_list", [
        'teachers' => $teacher
    ]);
}
```	
Sur ce bout de code, le tableau d'objets $teacher sera envoyé via la méthode show afin d'être afficher sur une page côté front-end grâce à ton templating.
Et bien là on va plutôt demander à ton contrôleur de juste renvoyer la donnée au format JSON. Pour cela, on va utiliser une méthode qu'on appelerait **json()** de la classe **Controller**. Cette méthode va nous permettre de renvoyer la donnée au format JSON. On va donc modifier notre contrôleur de la manière suivante :
```php
/**
 * Display teacher 
 *
 * @return void
 */
public function teacher()
{
    $newteacher = new Teacher();

    $teacher = $newteacher->findAll();
    
    $this->json($teacher);
}
```
Une fois fait, si tu te rends sur la route /teachers de ton back-end... Tu n'auras plus d'interface front-end, juste le JSON qui contiendra tous les professeurs. Si tu as compris ce point, bravo, tu viens de paramétrer la première route de ton API rest skoule : la route GET de /teachers. Si tu souhaites plus d'informations sur les API Rest je te laisse te renseigner sur le sujet (google / Chat GPT, les ressources ne manquent pas).
Maintenant passons au javascript ! Je décide de créer une application web Frontend qui va aller requêter ton API REST Skoule de manière asyncrone, histoire d'avoir une jolie SPA (combinaison des nouvelles notions vues plus haut en une phrase : done ! :nerd:) 
Je vais donc créer ma page HTML et le CSS qui va bien avec (jusqu'ici rien de nouveau)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Skoule</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="teachers"></div>
    <script src="fetch.js"></script>
</body>
</html>
```
Tu vois sur cet exemple que lorsque j'affiche ma page web, je n'ai pas de contenu. C'est normal, je n'ai pas encore fait de requête.
Puis je vais y ajouter un script qui va me permettre de faire des requêtes asyncrones sur ton API REST. Je vais donc créer un fichier js qui va s'appeler **fetch.js** et qui va contenir le code suivant :
```js
// On récupère la div qui va contenir les données
const teachersContainer = document.getElementById("teachers")
// On crée une variable qui va contenir l'url de l'API
const url = "http://localhost:8000/teachers"
// On crée une fonction qui va faire la requête
const getTeachers = async () => {
    // On crée une variable qui va contenir la réponse de l'API
    const response = await fetch(url)
    // On crée une variable qui va contenir les données de l'API
    const data = await response.json()
    // On crée une variable qui va contenir le contenu HTML qui va être affiché
    let html = ""
    // On crée une boucle qui va parcourir les données de l'API
    for (let i = 0; i < data.length; i++) {
        // On ajoute à la variable html le contenu HTML qui va être affiché
        html += `<div class="teacher">
                    <h2>${data[i].firstname} ${data[i].lastname}</h2>
                    <p>${data[i].email}</p>
                </div>`
    }
    // On affiche le contenu HTML dans la div
    teachersContainer.innerHTML = html
}
// On appelle la fonction
getTeachers()
```
Une fois cette fonction appelée dans mon fichier, la donnée de l'API sera affichée dans ma div. Et voilà, tu viens de créer une application web Frontend qui va aller requêter ton API REST Skoule de manière asyncrone. Bravo ! :tada:

## que fait la méthode fetch() ?
Attention, contrairement aux requêtes effectuées côté serveur, Fetch reviendra toujours avec une réponse, même si elle est vide. C'est pourquoi il est important de vérifier que la réponse est bien un succès (code 200) avant de traiter le contenu de la réponse.

## Un peu de pratique ?
Voici un lien qui pourrait t'aider à comprendre / pratiquer la méthode fetch() :
- [Web Dev Simplified](https://www.youtube.com/watch?v=cuEtnrL9-H0) un de mes youtubeurs préférés qui explique très bien la méthode fetch()
Et si tu es à l'aise avec le JS et que tu veux tester une librairie reactive (créée par META, on y revient) et extrêmement utilisée aujourd'hui : 
[web dev simplified react fast course](https://www.youtube.com/watch?v=hQAHSlTtcmY)
[doc officielle](https://react.dev/)
Cela te permettra de te mettre à l'aise avec le développement Frontend asyncrone de manière bien plus confortable qu'avec du JS pur.