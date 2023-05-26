# Configuration et mise en place des hôtes virtueles
Il faut commencer à créer un répértoire pour le projet réaliser avec Ansible et puis on y accède.
> mkdir myproject_ansible
> 
> cd myproject_ansible
> 

# Fichier de configuration 
On doit trouver le dossier contenant les fichiers de configuration d'Apache2. 
Par défaut, sur les systèmes Linux, les fichiers de configuration d'Apache2 se trouvent dans le répertoire /etc/apache2.
Cette commande copie le fichier de configuration par défaut (000-default.conf)
dans un nouveau fichier (www.hei.school.conf ou api.hei.school.conf ou front.hei.school.conf ou back.hei.school.conf) 
afin de modifier mon hôte virtuel.

> sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/www.hei.school.conf
> 
> sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/api.hei.school.conf
> 
> sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/front.hei.school.conf
> 
> sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/back.hei.school.conf
> 

# Changement de contenu du template
On doit modifier les fichiers de configuration pour chaque hôte virtuel en utilisant un éditeur de texte Nano

> sudo nano /etc/apache2/sites-available/www.hei.school.conf
> 
> sudo nano /etc/apache2/sites-available/api.hei.school.conf
> 
> sudo nano /etc/apache2/sites-available/front.hei.school.conf
> 
> sudo nano /etc/apache2/sites-available/back.hei.school.conf
> 

# Configuration de DNS locale 
On doit configurer le DNS locale sur mon propre machine avec celui de nom de domaine que je vais créer.
NB : les adresses IP ont été choisi selon l'adresse ip de mon machine virtuelle.
> 127.0.0.1       localhost
>
> 127.0.1.1       lisa-virtual-machine
> 
> 127.0.1.2       www.hei.school
> 
> 127.0.1.3       api.hei.school
> 
> 127.0.1.4       front.hei.school
> 
> 127.0.1.5       back.hei.school
> 

# Création d'un fichier d'inventaire Ansible 
Cela permet de spécifier les hôtes sur lesquels on souhaite configurer les hôtes virtuels.
Exemple : inventory.ini

> touch  inventory.ini

En exécutant cette commande, on crée un nouveau fichier vide avec le nom spécifié, dans ce cas inventory.ini, prêt à être édité.

On utilise nano pour ajouter le contenu du fichier inventory.ini qui doit être correctement configuré avec les adresses IP et les noms d'hôte cibles. 


> nano  inventory.ini

contenu :
> [virtual_host]
> 
> www.hei.school ansible_host=192.0.1.2
> 
> api.hei.school ansible_host=192.0.1.3
> 
> front.hei.school ansible_host=192.0.1.4
> 
> back.hei.school ansible_host=192.0.1.5

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

# Configuration des fichier.conf
On configure chaque contenu de template en adaptant avec le nom de domaine dans le fichier inventory.ini en exécutant le éditeur de texte ci-dessus

# Création d'un fichier de tâches .yml 
Ce fichier de tâches copie le fichier de configuration Apache2 
spécifique à chaque hôte virtuel, 
crée les répertoires 
documentRoot et active les hôtes virtuels.
Il redémarre également le service Apache2 pour appliquer les changements.

> nano ansible.yml (fichier ansible.yml)

