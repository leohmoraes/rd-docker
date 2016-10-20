# rd-docker

A client that controls Docker containers in the development environment. It is designed to work alongside Docker Compose and has the objective to make easier common operations docker operations on development environment.

## Installation

To install rd-docker type the following in a terminal window:

```
curl -sSL https://raw.githubusercontent.com/ResultadosDigitais/rd-docker/master/rd-docker-install | sudo sh
```

It will install rd-docker in your environment and if you use linux it will try to install Docker and Docker Compose as well. On Mac OS X you will need to manually install Docker after rd-docker is installed.

## Configuration

To configure rd-docker first be shure to have docker-compose.yml configured on your project folder. Then crate a file named **rd-docker.config** in your project folder like the following:

```
IMAGE=resultadosdigitais/rdstation-dev:alpha
MAIN_CONTAINER_NAME="web"
```

### Configuration options

#### IMAGE (required):

Docker image of the main application container. rd-docker will use it to auto update before server starts.

#### MAIN_CONTAINER_NAME (required):

The name of the main container on docker-compose.yml. It's the container where the project server runs.

#### APP_PREFIX (optional):

The prefix which will be used on container names. Project folder name is used if it's omitted. Example:

```
APP_PREFIX="rdstation_"
```

#### VOLUME_NAMES (optional):

The volume names to rd-docker create and ensure the existence before starting containers.

```
VOLUME_NAMES=(
  "rdstation_postgres"
  "rdstation_mongo"
  "rdstation_redis"
)
```

## Usage

All rd-docker commands should be executed on your project root folder.

Type the following to start your application server:

```bash
$ rd-docker start
```

To access a bash console inside your main container use the following command:

```bash
$ rd-docker console
```

To stop and remove all your project containers use the following:

```bash
$ rd-docker stop
```

If you want to run any other command on any of your Docker Compose containers use the following:

```bash
$ rd-docker exec "container name" "command"
```

These are the most common rd-docker commands. To see a list of all commands type the following:

```bash
$ rd-docker help
```

## Troubleshooting

If rd-docker says that `docker` or `docker-compose` commands doesn't exist it means the there was some problem on docker automatic installation. When it occurs you must install them manually. Go to the following links to know more about manual installation:

[Docker Engine instalation](https://docs.docker.com/engine/installation/linux/) (Linux)

[Docker Compose instalation](https://docs.docker.com/compose/install/) (Linux)

[Docker Toolbox instalation](https://github.com/ResultadosDigitais/rd-product-team-wiki/wiki/Como-configurar-o-ambiente-de-desenvolvimento-utilizando-Docker#mac-os-x-109) (Mac OS X 10.9+)
