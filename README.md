# ansible-role-docker
Installs docker, docker-compose and optional docker compose applications.

Docker installation follows this documentation steps:
https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

If variable docker_apps is present, each defined docker compose application will be installed and automatically started using systemd services. A service template ensures startup of docker compose application after docker service has been started. This mechanism is based on this gist:
https://gist.github.com/mosquito/b23e1c1e5723a7fd9e6568e5cf91180f

## Variables

* docker_user: This user will be added to the docker group and has permission to perform docker cli commands
* docker_apps: List of applications to install. If empty, no docker compose applications will be installed

Applications of the list docker_apps are defined by this object properties:

* name: The application name, will be used by systemctl to start and stop application
* url: URL to docker compose file
* env: Dictonary of application environment variables and their values