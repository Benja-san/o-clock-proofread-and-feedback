# Parcours PHP : Review apprenant 1 :fire:

## 1 : Global :earth_africa:
- Très bonne séparation du code répartie entre le modèle, le controlleur et la vue, tu as compris et utilisé le design pattern MVC à bon escient, bien joué :clap: !
- Tu as nommé tes fichiers controlleurs et modèles de manière claire  :thumbsup: !
- N'hésite pas à typer les propriétés et les paramètres d'entrée de tes modèles, cela permet de mieux comprendre le code et de mieux sécuriser ton application.
- Pense à garder en tête une convention de nommage uniforme afin de faciliter la lecture du code / du site et garder une meilleure cohérence. Je pense à la route "teacher_list" que tu as donné qui mériterais de gagner un "s"
- Concernant la validation des données des formulaires que tu as implémenté : C'est une très bonne idée d'utiliser la fonction filter_input pour valider les données, par contre tu as oublié de définir dans ton modèle (mais aussi dans la récupération de tes données de formulaire) la propriété contenant l'id du professeur lié à l'élève... ce qui bloque ta requête.

**Concernant le model**
- Les méthodes et propriétés implémentées dans tes classes sont correctes (revoir le typage des propriétés et des paramètres d'entrée) dans l'ensemble.... excépté cet exemple :
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
Il me smeble que la classe abstraite avec laquelle tu étends ta classe Teacher (et Student d'ailleurs) comportait déjà un getter pour l'id, (ou mériterais d'en avoir un). en revanche on ne propose JAMAIS un setter pour l'id d'une entité, ces dernières sont dans la majeure parties des cas implémentées de manière automatique et permettent de retrouver une entrée dans la table visée. Si tu viens modifier l'id d'une entrée tu risque de chambouler ta table et de créer plusieurs erreurs.
- Mis à part cette coquille tu as compris l'essence du modèle et tu as implémenté les méthodes nécessaires pour récupérer les données de la base de données. Bien joué :clap: !

**Concernant le controller**
- Tu as compris à quoi refère un controller, c'est top. Et tu as reussi à instancier / appeler les méthodes de manière efficace pour récupérer / ajouter les données demandées selon la page.
- :warning: Dans ton controlleur TeacherController tu as collé une méthode qui était initialement prévue pour le controlleur dédié aux étudiants... C'est très bien de réutiliser ce code! Par contre pense à modifier le nom des variables et le nom des Classes utilisées car là on se retrouve avec des variables qui n'ont plus de sens, qui ne sont plus définies et surtout tu risque d'ajouter des professeurs dans la table des étudiants si par mégarde tu "tombe en marche" (dixit, si ton code fonctionne alors qu'il ne devrait probablement pas).

**Concernant la vue**
- Le templating est ok, en revanche pense aux fonction include afin d'éviter de répéter le code html dans chaque fichier de vue. Cette répétition laisse la porte ouverte à des bugs... Lorsque je navigue sur la route pour accèder à la liste des étudiants / des professeurs, je n'ai plus accès à la navbar... Et lorsque je suis sur le formulaire d'ajout de professeur/ étudiant, le chemin qui mène aux listes / à l'accueil sont érronés. Pense à compartimenter ton code (pourquoi pas créer un dossier spécifique afin d'y integrer header / footer / navbar etc...).

## 2 : Keep practicing ! :fire:
-Un coup de révision sur les bonnes pratiques de la POO! Un peu de pratique et ça devrait être bon! courage! :muscle: