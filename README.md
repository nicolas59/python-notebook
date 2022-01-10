## Installation

1. Installer la version python3
2. Récupérer le projet https://github.com/nicolas59/python-notebook.git
3. Aller dans le repertoire di projet et créer un environnement virtuel

`python3 -m venv .`

4. Activer votre environnement virtuelle
5. Récupérer les dependances du projet
   
`pip install -r requirements.txt`

6. Lancer jupyter-lab

`jupyter-lab`


## Utilisation base de données
### Pre requis
Installation de docker ou de podman.

Les exemples suivants se base sur l'utilisation de *podman*.

### Installation mariabd

Installation lib python

` pip3 install mysql-connector-python`

Lancement du container mariadb

```
$ podman run -d  --name mariadb \
   --env MARIADB_USER=user \
   --env MARIADB_PASSWORD=secret \
   --env MARIADB_ROOT_PASSWORD=secret-pw   \
   --env MARIADB_DATABASE=demo \
   -p 3306:3306 \
   mariadb:latest
```

### Installation postgres

Installation lib python

` pip install psycopg2-binary`

Lancement du container postgres

```
$ podman run -d --name postgres  \
    -e POSTGRES_USER=user \
    -e POSTGRES_PASSWORD=secret  \
    -e POSTGRES_DB=demo \
    -p 5432:5432 \
    postgres:latest
```

### Arret et suppression

``` 
podman stop mariadb \
 && podman rm mariadb \
 && podman rmi mariadb \
 && podman image prune
```

``` 
podman stop postgres \
 && podman rm postgres \
 && podman rmi postgres \
 && podman image prune
```
