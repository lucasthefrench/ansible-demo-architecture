# ansible-demo-architecture
exemple de structure du Git pour Ansible

## Les filieres

Un repertoire par filiere:
- IUL
- BW
- WVS

Ces repertoires contiennent les playbooks et roles necessaires au fonctionnement des playbooks.
Voici la structure pour une filiere, IUL dans notre exemple:
```bash
├── IUL
│   ├── deploy_my_application
│   │   ├── deploy_my_app.yml
│   │   ├── get_requirements.sh
│   │   ├── requirements.yml
│   │   └── roles
│   ├── deploy_ntp
│   │   ├── deploy_ntp.yml
│   │   ├── get_requirements.sh
│   │   ├── requirements.yml
│   │   └── roles
│   │       └── geerlingguy.ntp
│   │           ├── defaults
│   │           │   └── main.yml
│   │           ├── handlers
│   │           │   └── main.yml
│   │           ├── LICENSE
│   │           ├── meta
│   │           │   └── main.yml
│   │           ├── molecule
│   │           │   └── default
│   │           │       ├── molecule.yml
│   │           │       ├── playbook.yml
│   │           │       └── yaml-lint.yml
│   │           ├── README.md
│   │           ├── tasks
│   │           │   ├── clock-rhel-6.yml
│   │           │   └── main.yml
│   │           ├── templates
│   │           │   ├── clock.j2
│   │           │   └── ntp.conf.j2
│   │           └── vars
│   │               ├── Archlinux.yml
│   │               ├── Debian.yml
│   │               ├── FreeBSD.yml
│   │               ├── RedHat.yml
│   │               └── Suse.yml
│   ├── group_vars
│   │   ├── dns.yml
│   │   ├── mysql.yml
│   │   └── webserver.yml
│   ├── host_vars
│   │   ├── u3antu16.yml
│   │   ├── u3antu2.yml
│   │   └── u3antu457.yml
│   └── update_upgrade_os
│       ├── get_requirements.sh
│       ├── requirements.yml
│       ├── roles
│       └── update_upgrade_os.yml
```
## Le dossier group_vars

Le dossier group_vars contient un ensemble de fichiers YAML qui contiennent des variables propres à un groupe de serveur.

Exemple:

```bash
├── group_vars
│   ├── dns.yml
│   ├── mysql.yml
│   └── webserver.yml
```
## Le dossier host_vars

A l'instar du dossier group_vars, le dossier host_vars permet de définir des variables propores à un serveur.

> [!WARNING]
> Cette méthode oblige à avoir des fichiers aux noms des serveurs, ce qui posera des problèmes en cas de changement des noms des serveurs car il faudra changer aussi le nom de ces fichiers (ce qui peut être source d'erreurs)

Exemple:

```bash
├── host_vars
│   ├── u3antu16.yml
│   ├── u3antu2.yml
│   └── u3antu457.yml
```
## Le dossier my_galaxy

Ce dossier contiendra tous les rôles, comme le Ansible Galaxy mais en local. 

## Les inventaires

Enfin, on trouve à la racine les inventaires propres aux environnements.

## Apercu de l'aborescence complete
```bash
.
├── inventories_backup
│   ├── back_inventory_dev
│   ├── back_inventory_prod
│   └── back_inventory_rec
├── IUL
│   ├── deploy_my_application
│   │   ├── deploy_my_app.yml
│   │   ├── get_requirements.sh
│   │   ├── requirements.yml
│   │   └── roles
│   ├── deploy_ntp
│   │   ├── deploy_ntp.yml
│   │   ├── get_requirements.sh
│   │   ├── requirements.yml
│   │   └── roles
│   │       └── geerlingguy.ntp
│   │           ├── defaults
│   │           │   └── main.yml
│   │           ├── handlers
│   │           │   └── main.yml
│   │           ├── LICENSE
│   │           ├── meta
│   │           │   └── main.yml
│   │           ├── molecule
│   │           │   └── default
│   │           │       ├── molecule.yml
│   │           │       ├── playbook.yml
│   │           │       └── yaml-lint.yml
│   │           ├── README.md
│   │           ├── tasks
│   │           │   ├── clock-rhel-6.yml
│   │           │   └── main.yml
│   │           ├── templates
│   │           │   ├── clock.j2
│   │           │   └── ntp.conf.j2
│   │           └── vars
│   │               ├── Archlinux.yml
│   │               ├── Debian.yml
│   │               ├── FreeBSD.yml
│   │               ├── RedHat.yml
│   │               └── Suse.yml
│   ├── group_vars
│   │   ├── dns.yml
│   │   ├── mysql.yml
│   │   └── webserver.yml
│   ├── host_vars
│   │   ├── u3antu16.yml
│   │   ├── u3antu2.yml
│   │   └── u3antu457.yml
│   └── update_upgrade_os
│       ├── get_requirements.sh
│       ├── requirements.yml
│       ├── roles
│       └── update_upgrade_os.yml
└── my_galaxy
    ├── galaxy_docker
    │   ├── defaults
    │   │   └── main.yml
    │   ├── handlers
    │   │   └── main.yml
    │   ├── LICENSE
    │   ├── meta
    │   │   └── main.yml
    │   ├── molecule
    │   │   └── default
    │   │       ├── molecule.yml
    │   │       ├── playbook.yml
    │   │       └── yaml-lint.yml
    │   ├── README.md
    │   └── tasks
    │       ├── docker-compose.yml
    │       ├── docker-users.yml
    │       ├── main.yml
    │       ├── setup-Debian.yml
    │       └── setup-RedHat.yml
    ├── galaxy_nginx
    │   ├── defaults
    │   │   └── main.yml
    │   ├── handlers
    │   │   └── main.yml
    │   ├── LICENSE
    │   ├── meta
    │   │   └── main.yml
    │   ├── molecule
    │   │   └── default
    │   │       ├── molecule.yml
    │   │       ├── playbook.yml
    │   │       └── yaml-lint.yml
    │   ├── README.md
    │   ├── tasks
    │   │   ├── main.yml
    │   │   ├── setup-Archlinux.yml
    │   │   ├── setup-Debian.yml
    │   │   ├── setup-FreeBSD.yml
    │   │   ├── setup-OpenBSD.yml
    │   │   ├── setup-RedHat.yml
    │   │   ├── setup-Ubuntu.yml
    │   │   └── vhosts.yml
    │   ├── templates
    │   │   ├── nginx.conf.j2
    │   │   ├── nginx.repo.j2
    │   │   └── vhost.j2
    │   └── vars
    │       ├── Archlinux.yml
    │       ├── Debian.yml
    │       ├── FreeBSD.yml
    │       ├── OpenBSD.yml
    │       └── RedHat.yml
    └── galaxy_pip
        ├── defaults
        │   └── main.yml
        ├── LICENSE
        ├── meta
        │   └── main.yml
        ├── molecule
        │   └── default
        │       ├── molecule.yml
        │       ├── playbook.yml
        │       ├── tests
        │       │   └── test_default.py
        │       └── yaml-lint.yml
        ├── README.md
        └── tasks
            └── main.yml
```
