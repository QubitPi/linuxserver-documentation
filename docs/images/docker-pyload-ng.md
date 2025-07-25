---
title: pyload-ng
tags:
    - Downloaders
description: "[pyLoad](https://pyload.net/) is a Free and Open Source download manager written in Python and designed to be extremely lightweight, easily extensible and fully manageable via web."
---
<!-- DO NOT EDIT THIS FILE MANUALLY -->
<!-- Please read https://github.com/linuxserver/docker-pyload-ng/blob/main/.github/CONTRIBUTING.md -->
# [linuxserver/pyload-ng](https://github.com/linuxserver/docker-pyload-ng)

[![Scarf.io pulls](https://scarf.sh/installs-badge/linuxserver-ci/linuxserver%2Fpyload-ng?color=94398d&label-color=555555&logo-color=ffffff&style=for-the-badge&package-type=docker)](https://scarf.sh)
[![GitHub Stars](https://img.shields.io/github/stars/linuxserver/docker-pyload-ng.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&logo=github)](https://github.com/linuxserver/docker-pyload-ng)
[![GitHub Release](https://img.shields.io/github/release/linuxserver/docker-pyload-ng.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&logo=github)](https://github.com/linuxserver/docker-pyload-ng/releases)
[![GitHub Package Repository](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=GitHub%20Package&logo=github)](https://github.com/linuxserver/docker-pyload-ng/packages)
[![GitLab Container Registry](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=GitLab%20Registry&logo=gitlab)](https://gitlab.com/linuxserver.io/docker-pyload-ng/container_registry)
[![Quay.io](https://img.shields.io/static/v1.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=linuxserver.io&message=Quay.io)](https://quay.io/repository/linuxserver.io/pyload-ng)
[![Docker Pulls](https://img.shields.io/docker/pulls/linuxserver/pyload-ng.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=pulls&logo=docker)](https://hub.docker.com/r/linuxserver/pyload-ng)
[![Docker Stars](https://img.shields.io/docker/stars/linuxserver/pyload-ng.svg?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=stars&logo=docker)](https://hub.docker.com/r/linuxserver/pyload-ng)
[![Jenkins Build](https://img.shields.io/jenkins/build?labelColor=555555&logoColor=ffffff&style=for-the-badge&jobUrl=https%3A%2F%2Fci.linuxserver.io%2Fjob%2FDocker-Pipeline-Builders%2Fjob%2Fdocker-pyload-ng%2Fjob%2Fmain%2F&logo=jenkins)](https://ci.linuxserver.io/job/Docker-Pipeline-Builders/job/docker-pyload-ng/job/main/)
[![LSIO CI](https://img.shields.io/badge/dynamic/yaml?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=CI&query=CI&url=https%3A%2F%2Fci-tests.linuxserver.io%2Flinuxserver%2Fpyload-ng%2Flatest%2Fci-status.yml)](https://ci-tests.linuxserver.io/linuxserver/pyload-ng/latest/index.html)

[pyLoad](https://pyload.net/) is a Free and Open Source download manager written in Python and designed to be extremely lightweight, easily extensible and fully manageable via web.

[![pyload-ng](https://github.com/linuxserver/docker-templates/raw/master/linuxserver.io/img/pyload-logo.png)](https://pyload.net/)

## Supported Architectures

We utilise the docker manifest for multi-platform awareness. More information is available from docker [here](https://distribution.github.io/distribution/spec/manifest-v2-2/#manifest-list) and our announcement [here](https://blog.linuxserver.io/2019/02/21/the-lsio-pipeline-project/).

Simply pulling `lscr.io/linuxserver/pyload-ng:latest` should retrieve the correct image for your arch, but you can also pull specific arch images via tags.

The architectures supported by this image are:

| Architecture | Available | Tag |
| :----: | :----: | ---- |
| x86-64 | ✅ | amd64-\<version tag\> |
| arm64 | ✅ | arm64v8-\<version tag\> |

## Version Tags

This image provides various versions that are available via tags. Please read the descriptions carefully and exercise caution when using unstable or development tags.

| Tag | Available | Description |
| :----: | :----: |--- |
| latest | ✅ | Stable releases from pyLoad Next |
| develop | ✅ | Releases from pyload Next develop branch |

## Application Setup

Access the web interface at `http://your-ip:8000` the default login is:
username - **pyload**
password - **pyload**

For general usage please see the pyLoad wiki [here](https://github.com/pyload/pyload/wiki) .

## Usage

To help you get started creating a container from this image you can either use docker-compose or the docker cli.

!!! info

    Unless a parameter is flaged as 'optional', it is *mandatory* and a value must be provided.

### docker-compose (recommended, [click here for more info](https://docs.linuxserver.io/general/docker-compose))

```yaml
---
services:
  pyload-ng:
    image: lscr.io/linuxserver/pyload-ng:latest
    container_name: pyload-ng
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      - /path/to/pyload-ng/config:/config
      - /path/to/downloads:/downloads
    ports:
      - 8000:8000
      - 9666:9666 #optional
    restart: unless-stopped
```

### docker cli ([click here for more info](https://docs.docker.com/engine/reference/commandline/cli/))

```bash
docker run -d \
  --name=pyload-ng \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Etc/UTC \
  -p 8000:8000 \
  -p 9666:9666 `#optional` \
  -v /path/to/pyload-ng/config:/config \
  -v /path/to/downloads:/downloads \
  --restart unless-stopped \
  lscr.io/linuxserver/pyload-ng:latest
```

## Parameters

Containers are configured using parameters passed at runtime (such as those above). These parameters are separated by a colon and indicate `<external>:<internal>` respectively. For example, `-p 8080:80` would expose port `80` from inside the container to be accessible from the host's IP on port `8080` outside the container.

### Ports (`-p`)

| Parameter | Function |
| :----: | --- |
| `8000:8000` | Allows HTTP access to the application |
| `9666:9666` | Click'n'Load port. |

### Environment Variables (`-e`)

| Env | Function |
| :----: | --- |
| `PUID=1000` | for UserID - see below for explanation |
| `PGID=1000` | for GroupID - see below for explanation |
| `TZ=Etc/UTC` | specify a timezone to use, see this [list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List). |

### Volume Mappings (`-v`)

| Volume | Function |
| :----: | --- |
| `/config` | Persistent config files |
| `/downloads` | Destination of pyLoad downloads |

#### Miscellaneous Options

| Parameter | Function |
| :-----:   | --- |

## Environment variables from files (Docker secrets)

You can set any environment variable from a file by using a special prepend `FILE__`.

As an example:

```bash
-e FILE__MYVAR=/run/secrets/mysecretvariable
```

Will set the environment variable `MYVAR` based on the contents of the `/run/secrets/mysecretvariable` file.

## Umask for running applications

For all of our images we provide the ability to override the default umask settings for services started within the containers using the optional `-e UMASK=022` setting.
Keep in mind umask is not chmod it subtracts from permissions based on it's value it does not add. Please read up [here](https://en.wikipedia.org/wiki/Umask) before asking for support.

## User / Group Identifiers

When using volumes (`-v` flags), permissions issues can arise between the host OS and the container, we avoid this issue by allowing you to specify the user `PUID` and group `PGID`.

Ensure any volume directories on the host are owned by the same user you specify and any permissions issues will vanish like magic.

In this instance `PUID=1000` and `PGID=1000`, to find yours use `id your_user` as below:

```bash
id your_user
```

Example output:

```text
uid=1000(your_user) gid=1000(your_user) groups=1000(your_user)
```

## Docker Mods

[![Docker Mods](https://img.shields.io/badge/dynamic/yaml?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=pyload-ng&query=%24.mods%5B%27pyload-ng%27%5D.mod_count&url=https%3A%2F%2Fraw.githubusercontent.com%2Flinuxserver%2Fdocker-mods%2Fmaster%2Fmod-list.yml)](https://mods.linuxserver.io/?mod=pyload-ng "view available mods for this container.") [![Docker Universal Mods](https://img.shields.io/badge/dynamic/yaml?color=94398d&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=universal&query=%24.mods%5B%27universal%27%5D.mod_count&url=https%3A%2F%2Fraw.githubusercontent.com%2Flinuxserver%2Fdocker-mods%2Fmaster%2Fmod-list.yml)](https://mods.linuxserver.io/?mod=universal "view available universal mods.")

We publish various [Docker Mods](https://github.com/linuxserver/docker-mods) to enable additional functionality within the containers. The list of Mods available for this image (if any) as well as universal mods that can be applied to any one of our images can be accessed via the dynamic badges above.

## Support Info

* Shell access whilst the container is running:

    ```bash
    docker exec -it pyload-ng /bin/bash
    ```

* To monitor the logs of the container in realtime:

    ```bash
    docker logs -f pyload-ng
    ```

* Container version number:

    ```bash
    docker inspect -f '{{ index .Config.Labels "build_version" }}' pyload-ng
    ```

* Image version number:

    ```bash
    docker inspect -f '{{ index .Config.Labels "build_version" }}' lscr.io/linuxserver/pyload-ng:latest
    ```

## Updating Info

Most of our images are static, versioned, and require an image update and container recreation to update the app inside. With some exceptions (noted in the relevant readme.md), we do not recommend or support updating apps inside the container. Please consult the [Application Setup](#application-setup) section above to see if it is recommended for the image.

Below are the instructions for updating containers:

### Via Docker Compose

* Update images:
    * All images:

        ```bash
        docker-compose pull
        ```

    * Single image:

        ```bash
        docker-compose pull pyload-ng
        ```

* Update containers:
    * All containers:

        ```bash
        docker-compose up -d
        ```

    * Single container:

        ```bash
        docker-compose up -d pyload-ng
        ```

* You can also remove the old dangling images:

    ```bash
    docker image prune
    ```

### Via Docker Run

* Update the image:

    ```bash
    docker pull lscr.io/linuxserver/pyload-ng:latest
    ```

* Stop the running container:

    ```bash
    docker stop pyload-ng
    ```

* Delete the container:

    ```bash
    docker rm pyload-ng
    ```

* Recreate a new container with the same docker run parameters as instructed above (if mapped correctly to a host folder, your `/config` folder and settings will be preserved)
* You can also remove the old dangling images:

    ```bash
    docker image prune
    ```

### Image Update Notifications - Diun (Docker Image Update Notifier)

!!! tip

    We recommend [Diun](https://crazymax.dev/diun/) for update notifications. Other tools that automatically update containers unattended are not recommended or supported.

## Building locally

If you want to make local modifications to these images for development purposes or just to customize the logic:

```bash
git clone https://github.com/linuxserver/docker-pyload-ng.git
cd docker-pyload-ng
docker build \
  --no-cache \
  --pull \
  -t lscr.io/linuxserver/pyload-ng:latest .
```

The ARM variants can be built on x86_64 hardware and vice versa using `lscr.io/linuxserver/qemu-static`

```bash
docker run --rm --privileged lscr.io/linuxserver/qemu-static --reset
```

Once registered you can define the dockerfile to use with `-f Dockerfile.aarch64`.

To help with development, we generate this dependency graph.

??? info "Init dependency graph"

    ```d2
    "pyload-ng:latest": {
      docker-mods
      base {
        fix-attr +\nlegacy cont-init
      }
      docker-mods -> base
      legacy-services
      custom services
      init-services -> legacy-services
      init-services -> custom services
      custom services -> legacy-services
      legacy-services -> ci-service-check
      init-migrations -> init-adduser
      init-os-end -> init-config
      init-config -> init-config-end
      init-crontab-config -> init-config-end
      init-pyload-config -> init-config-end
      init-config -> init-crontab-config
      init-mods-end -> init-custom-files
      init-adduser -> init-device-perms
      base -> init-envfile
      base -> init-migrations
      init-config-end -> init-mods
      init-mods-package-install -> init-mods-end
      init-mods -> init-mods-package-install
      init-adduser -> init-os-end
      init-device-perms -> init-os-end
      init-envfile -> init-os-end
      init-config -> init-pyload-config
      init-custom-files -> init-services
      init-services -> svc-cron
      svc-cron -> legacy-services
      init-services -> svc-pyload
      svc-pyload -> legacy-services
    }
    Base Images: {
      "baseimage-alpine:3.22"
    }
    "pyload-ng:latest" <- Base Images
    ```

## Versions

* **09.06.25:** - Rebase to Alpine 3.22.
* **20.07.24:** - Revert to Alpine 3.19 due to inconsistent upstream addon support for Python 3.12.
* **27.06.24:** - Rebase to Alpine 3.20.
* **23.12.23:** - Rebase to Alpine 3.19.
* **08.10.23:** - Install unrar from [linuxserver repo](https://github.com/linuxserver/docker-unrar).
* **10.08.23:** - Bump unrar to 6.2.10.
* **01.06.23:** - Replace p7zip with 7zip, add unrar.
* **25.05.23:** - Rebase to Alpine 3.18, deprecate armhf.
* **02.02.22:** - Rebase master to alpine 3.17.
* **02.02.22:** - Add ffmpeg for the Youtube plugin.
* **24.01.22:** - Replace unrar with p7zip.
* **24.01.22:** - Initial release.
