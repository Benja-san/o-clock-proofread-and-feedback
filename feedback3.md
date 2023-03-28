# Parcours PHP : Review apprenant 3 :fire:

## 1 : Global :earth_africa:
- Très bonne séparation du code répartie entre le modèle, le contrôleur et la vue, tu as compris et utilisé le design pattern MVC à bon escient, bien joué :clap: !
- Tu as nommé tes fichiers contrôleurs et modèles de manière claire  :thumbsup: !
- N'hésite pas à typer les propriétés et les paramètres d'entrée de tes modèles, cela permet de mieux comprendre le code et de mieux sécuriser ton application.
- Pense à garder en tête une convention de nommage uniforme afin de faciliter la lecture du code / du site et garder une meilleure cohérence. Je pense à la route "teacher_list" que tu as donné qui mériterait de gagner un "s"
- Concernant la validation des données des formulaires que tu as implémenté : c'est une très bonne idée d'utiliser la fonction filter_input pour valider les données. Par contre tu as oublié de définir dans ton modèle (mais aussi dans la récupération de tes données de formulaire) la propriété contenant l'id du professeur lié à l'élève... ce qui bloque ta requête.
- Petit commentaire supplémentaire même si ça reste léger, veille à coder exclusivement en anglais, c'est une bonne pratique à prendre dès le début de ton parcours : 
```php
// aucune erreur détectée
// j'ai soumis mon formulaire et je n'ai pas d'erreur
$retour = $newStudent->insert();
```
Pour le moment les commentaires en français ne sont pas dérangeants mais les noms de variables, fonctions, propriétés etc... doivent être en anglais. Cela permet de faciliter la lecture du code par des personnes qui ne parlent pas la même langue que toi et de faciliter la communication avec les autres développeurs.

**Concernant le modèle**
- Les méthodes et propriétés implémentées dans tes classes sont correctes (revoir le typage des propriétés et des paramètres d'entrée) dans l'ensemble.... excepté cet exemple :
```php
    /**
     * Get the value of id
     */ 
    public function getId()
    {
        return $this->id;
    }

    /**
     * Set the value of id
     *
     * @return  self
     */ 
    public function setId($id)
    {
        $this->id = $id;

        return $this;
    }
```
Il me semble que la classe abstraite avec laquelle tu étends ta classe Teacher (et Student d'ailleurs) comportait déjà un getter pour l'id, (ou mériterait d'en avoir un). En revanche, on ne propose JAMAIS un setter pour l'id d'une entité, ces dernières sont dans la majeure partie des cas implémentées de manière automatique et permettent de retrouver une entrée dans la table visée. Si tu viens modifier l'id d'une entrée tu risques de chambouler ta table et de créer plusieurs erreurs.
- Mis à part cette coquille tu as compris l'essence du modèle et tu as implémenté les méthodes nécessaires pour récupérer les données de la base de données. Bien joué :clap: !

**Concernant le contrôleur**
- Tu as compris à quoi refère un contrôleur, c'est top ! Et tu as réussi à instancier / appeler les méthodes de manière efficace pour récupérer / ajouter les données demandées selon la page.
- :warning: Dans ton contrôleur TeacherController tu as collé une méthode qui était initialement prévue pour le contrôleur dédié aux étudiants... C'est très bien de réutiliser ce code ! Par contre, pense à modifier le nom des variables et le nom des Classes utilisées car là on se retrouve avec des variables qui n'ont plus de sens, qui ne sont plus définies et surtout tu risques d'ajouter des professeurs dans la table des étudiants si par mégarde tu "tombes en marche" (dixit, si ton code fonctionne alors qu'il ne devrait probablement pas).

**Concernant la vue**
- Le templating est ok, en revanche, pense aux fonctions include afin d'éviter de répéter le code html dans chaque fichier de vue. Cette répétition laisse la porte ouverte à des bugs... Lorsque je navigue sur la route pour accéder à la liste des étudiants / des professeurs, je n'ai plus accès à la navbar... Et lorsque je suis sur le formulaire d'ajout de professeur/ étudiant, le chemin qui mène aux listes / à l'accueil sont erronés. Pense à compartimenter ton code (pourquoi pas créer un dossier spécifique afin d'y intégrer header / footer / navbar etc...).

## 2 : Keep practicing ! :fire:
- Un coup de révision sur les bonnes pratiques de la POO ! Un peu de pratique et ça devrait être bon ! Courage! :muscle: