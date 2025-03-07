# Docker commands

## Setup

The followings scripts assume that [Docker](https://www.docker.com/) has already been installed.

They also assume that the user has Docker permissions without requiring `sudo`. If you do not have these permissions:

1. Enter the following command:

  ```
  sudo usermod -a -G docker $USER
  ```

2. Log out and log back into your console to enable them.

## Installation Scripts

### Linux
```
wget https://raw.githubusercontent.com/hummingbot/gateway/main/docker/gateway-create.sh
wget https://raw.githubusercontent.com/hummingbot/gateway/main/docker/gateway-set-certs.sh
chmod a+x *.sh
```

### MacOS
```
curl https://raw.githubusercontent.com/hummingbot/gateway/main/docker/gateway-create.sh -o gateway-create.sh
curl https://raw.githubusercontent.com/hummingbot/gateway/main/docker/gateway-set-certs.sh -o gateway-set-certs.sh
chmod a+x *.sh
```

### Windows (WSL)

This assumes that the user is using Windows Subsystem for Linux (WSL):

```
cd ~
curl https://raw.githubusercontent.com/hummingbot/gateway/main/docker/gateway-create.sh -o gateway-create.sh
curl https://raw.githubusercontent.com/hummingbot/gateway/main/docker/gateway-set-certs.sh.sh -o gateway-set-certs.sh.sh
chmod a+x *.sh
```

## Create Gateway Instance

The `gateway-create.sh` script helps you pull, configure, and run the Gateway Docker image.

```
./gateway-create.sh
```

## Set Hummingbot Certs

If you didn't do this step during `gateway-create.sh`, the `gateway-set-certs.sh` script helps you copy the SSL certificates to your Gateway files folder needed for your Hummingbot instance to access Gateway securely.

```
./gateway-set-certs.sh
```

## Useful Commands

These commands assume a Gateway container with the default instance name `gateway`:

* List all Gateway containers: `docker ps -a --filter ancestor=hummingbot/gateway`
* Start Gateway container and attach to it: `docker start gateway && docker attach gateway`
* Stop Gateway container: `docker stop gateway`
* Update Gateway container to latest version: `docker pull hummingbot/gateway:latest`
* Remove Gateway container: `docker rm gateway`
