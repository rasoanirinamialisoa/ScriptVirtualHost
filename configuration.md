# Configuration et mise en place des hôtes virtueles
Il faut commencer à créer un répértoire pour le projet réaliser avec Ansible et puis on y accède.
> mkdir myproject_ansible
> 
> cd myproject_ansible
> 

# Création d'un fichier d'inventaire Ansible 
Cela permet de spécifier les hôtes sur lesquels on souhaite configurer les hôtes virtuels.
Exemple : inventory.ini

> touch  inventory.ini

En exécutant cette commande, on crée un nouveau fichier vide avec le nom spécifié, dans ce cas inventory.ini, prêt à être édité.

On utilise nano pour ajouter le contenu :

> nano  inventory.ini

contenu :
> [virtual_host]
> 
> www.hei.school
> 
> api.hei.school
> 
> front.hei.school
> 
> back.hei.school

# Création d'un fichier d'inventaire Apache2 pour chaque hôte virtuel.
Tout d'abord, il faut vérifier où se trouve le dossier et le fichier de configuration
> ???

Pour ce cas, on doit procéder à la création de répertoire "templates" et on y accède.
> mkdir templates
> 
> cd templates
> 

Une fois dans le repértoire templates, on utilisez un éditeur de texte pour créer les fichiers de configuration Apache2 pour chaque hôte virtuel.
> nano www.hei.school.conf
> 
> nano api.hei.school.conf
> 
> nano front.hei.school.conf
> 
> nano back.hei.school.conf
> 

