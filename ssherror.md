# SSH avec les hôtes virtuels échoué
En raison de la vérification de l'authenticité de la clé d'hôte l'établissement de la connexion SSH avec les hôtes virtuels a échoué.
Cela se produit lorsque les clés SSH des hôtes virtuels sont inconnues ou n'ont pas été ajoutées à votre fichier known_hosts.
Pour résoudre ce problème, on doit supprimer les clés SSH existantes pour les hôtes virtuels à l'aide de commande :

- ssh-keygen -R 127.0.1.2
- ssh-keygen -R 127.0.1.3
- ssh-keygen -R 127.0.1.4
- ssh-keygen -R 127.0.1.5

# Reconfiguration de clé SSH avec les hôtes virtuels
- Si l'erreur d'authetification pesiste avec les hôtes virtuels, il faut vérifier les clés SSH sur l'hôte distant avec : ssh lisa@www.hei.school
- On passe à la vérification d'autorisation de l'utilisateur sur l'hôte distant avec : sh lisa@www.hei.school sudo -l
- On edite le fichier sshd_config sur l'hôte distant (www.hei.school) sudo nano /etc/ssh/sshd_config

NB: ses étapes doit être répéter avec les autres hôtes virtuels

# /etc/ssh/sshd_config
Dans ce fichier, on doit appliquer quelques configuration 
Pour autoriser l'authentification par clé SSH :
- PubkeyAuthentication yes : pour désactiver l'authentification par mot de passe :
- PasswordAuthentication no : pour autoriser la connexion en tant que root (uniquement si nécessaire) :
- PermitRootLogin yes : pour spécifier un port SSH personnalisé (22) :
- Port 22
- sudo service ssh restart




