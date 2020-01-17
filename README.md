# ansible-demo-architecture
exemple de structure du Git pour Ansible

## Les filieres

Un repertoire par filiere:
- IUL
- BW
- WVS

Ces repertoires contiennent les playbooks et roles necessaires au fonctionnement des playbooks.
Voici la structure pour une filiere, IUL dans notre exemple:
IUL
|--my_app_to_deploy
   |--my_playbook_to_deploy.yml
      |--get_requirements.sh
      |--requirements.yml
      |--roles
         |--galaxy_nginx
            |--tasks
               |--main.yml
            |--defaults
               |--main.yml
            |--handlers
               |--main.yml
            |--templates
               |--confile.conf.j2
               |--another_confile.conf.j2

## Le dossier group_vars

Le dossier group_vars contient un ensemble de fichiers YAML qui contiennet des variables propres à un groupe de serveur.

Exemple:

.
+--dnsservers.yml
+--webservers.yml
+--centos7servers.yml
+--...

## Le dossier host_vars

A l'instar du dossier group_vars, le dossier host_vars permet de définir des variables propores à un serveur.

> [!WARNING]
> Cette méthode oblige à avoir des fichiers aux noms des serveurs, ce qui posera des problèmes en cas de changement des noms des serveurs car il faudra changer aussi le nom de ces fichiers (ce qui peut être source d'erreurs)

Exemple:

.
+--u3antu457.yml
+--u2antw79.yml
+--u3antu11.yml
+--...

## le dossier my_galaxy

Ce dossier contiendra tous les rôles, comme le Ansible Galaxy mais en local. 

## Les inventaires

Enfin, on trouve à la racine les inventaires propres aux environnements.

│   ├── galaxy_nginx
│   │   ├── defaults
│   │   │   └── main.yml
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── LICENSE
│   │   ├── meta
│   │   │   └── main.yml
│   │   ├── molecule
│   │   │   └── default
│   │   │       ├── molecule.yml
│   │   │       ├── playbook.yml
│   │   │       └── yaml-lint.yml
