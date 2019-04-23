# Formulaires - Sessions - Fichiers

Pour cet exercice, il s'agit de :
- Créer une page d’inscription permettant à un utilisateur de fournir un login (qui devra être unique) et un mot de passe.
- Créer une page de login permettant à un utilisateur préalablement inscrit de se connecter.
- Créer une page profil à laquelle l’utilisateur accède lorsqu’il se connecte.

Dans celle-ci : un rappel du login de l’utilisateur, l’avatar de l’utilisateur, un formulaire permettant d’uploader une nouvelle image d’avatar, un bouton permettant à l’utilisateur de supprimer son profil (après confirmation). Enfin, un lien vers une page reprenant la liste des utilisateurs existants.
- Créer une page listing reprenant la liste des utilisateurs existants. Les utilisateurs seront présentés par ordre alphabétique de login. Si l’utilisateur connecté est un superuser, il a la possibilité pour chaque utilisateur de modifier ses droits (user=>superuser ou l’inverse).
- Créer une page de déconnexion permettant à un utilisateur préalablement connecté de se déconnecter.

L’ensemble des informations sur les utilisateurs sera stocké dans un fichier users.dat situé à la racine du site. Dans le fichier, on stockera un tableau sérialisé contenant en clé principale le nom d’utilisateur et en valeur un tableau avec mot de passe, genre, droits et avatar de l’utilisateur.

Le login sera unique, le mot de passe stocké sous forme de hash, le genre sera soit M soit F ; Les droits seront par défaut 0 (user), ils pourront être positionnés à 1 (superuser) par un administrateur. L’avatar de l’utilisateur consiste en une image de 100 pixels sur 100 au format JPG ou PNG, stockée sous forme base64_encodée dans le tableau sérialisé.

Dans le fichier, on stocke un tableau sérialisé contenant en clé principale le nom d’utilisateur et en valeur un tableau avec mot de passe, droit et image (et d’autres si on veut). Un admin peu éditer tous les utilisateur et l’utilisateur une fois connecté peut modifier son image en en envoyant une nouvelle. 

## Références
[file-exists](https://www.php.net/manual/fr/function.file-exists.php)
https://www.php.net/manual/fr/function.file-get-contents.php
https://www.php.net/manual/fr/function.file-put-contents.php

https://www.php.net/manual/fr/function.serialize.php
https://www.php.net/manual/fr/function.unserialize.php

https://www.php.net/manual/fr/function.array-key-exists.php
https://www.php.net/manual/fr/function.ksort.php

## Encoder un image base64

```php
function base64_encode_image ($filename=string,$filetype=string)
{
    if ($filename)
    {
        $imgbinary = fread(fopen($filename, "r"), filesize($filename));
        return 'data:image/' . $filetype . ';base64,' . base64_encode($imgbinary);
    }
}
```
