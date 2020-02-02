Docker Django
=============

## tl;dr
```bash
$ git clone git@github.com:erroneousboat/docker-django.git
$ docker-compose up
```

Now you can access the application at <https://localhost> and the admin site
at <https://localhost/admin>.

## Setting up

### Environment variables
The file `config/environment/development.env` contains the environment
variables needed in the containers. You can edit this as you see fit, and at
the moment these are the defaults that this project uses. However when you
intend to use this, keep in mind that you should keep this file out of version
control as it can hold sensitive information regarding your project. The file
itself will contain some commentary on how a variable will be used in the
container.

## Fire it up
Start the container by issuing one of the following commands:
```bash
docker-compose up --build
docker-compose up --build -d
```

## Other commands
Build images:
```bash
docker-compose build
docker-compose build --no-cache       # build without cache
```

### Some commands for managing the webapp
To initiate a command in an existing running container use the `docker exec`
command.

```bash
# migrate
docker-compose exec webapp python3 srv/thes/manage.py makemigrations
docker-compose exec webapp python3 srv/thes/manage.py migrate

# create a super user
docker-compose exec webapp python3 srv/thes/manage.py createsuperuser
```

