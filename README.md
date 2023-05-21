# Script Virtual Host

# Utiliser Ansible pour configurer l'hôte virtuelle Apache2

## _Rôle ansible_

Ansible est un outil de gestion de configuration et d'automatisation qui peut être utilisé pour configurer un hôte virtuel avec Apache 2. Les rôles d'Ansible dans ce contexte incluent :

## Installation d'Apache 2 : 
Ansible peut gérer l'installation d'Apache 2 sur l'hôte cible en utilisant des modules dédiés, tels que le module apt pour les distributions basées sur Debian/Ubuntu.

## Configuration d'Apache 2 :
Ansible peut gérer la configuration d'Apache 2 en utilisant des fichiers de configuration spécifiques. On peut définir des templates de configuration Apache 2 et les déployer sur l'hôte cible en utilisant le module template d'Ansible. Cela permet de personnaliser les directives telles que le répertoire racine, les fichiers d'index, les règles de réécriture, etc.

## Gestion des Virtual Hosts : 
Ansible peut créer et gérer les fichiers de configuration des Virtual Hosts pour Apache 2. Cela peut inclure la création de fichiers de configuration spécifiques pour chaque Virtual Host, l'activation et la désactivation des Virtual Hosts selon les besoins, et la gestion des directives spécifiques à chaque Virtual Host.

## Redémarrage d'Apache 2 : 
Une fois que les configurations des Virtual Hosts ont été appliquées, Ansible peut redémarrer le service Apache 2 pour prendre en compte les modifications. Cela se fait en utilisant le module service d'Ansible.
