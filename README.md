# Docker Tuleap

Ce dépôt contient les fichiers de configuration nécessaires pour construire un conteneur Docker Tuleap avec MySQL.

## Prérequis

- Docker installé sur votre machine

## Installation

1. Clonez ce dépôt :
    ```bash
    git clone https://github.com/votre-utilisateur/docker-tuleap.git
    ```

2. Accédez au répertoire du projet :
    ```bash
    cd docker-tuleap
    ```

3. Construisez l'image Docker :
    ```bash
    docker build -t tuleap-container .
    ```

## Utilisation

Pour exécuter le conteneur Tuleap :

```bash
docker run -d tuleap-container
```

Variables d'environnement

    TULEAP_SERVER_NAME : Nom du serveur Tuleap
    MYSQL_PASSWORD : Mot de passe pour l'utilisateur MySQL

Fichiers de configuration

    Dockerfile : Définition de l'image Docker
    setup-tuleap.service : Service systemd pour la configuration de Tuleap
    script.sh : Script de configuration
