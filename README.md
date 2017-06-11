# Docker Image Baselayout

Adds some convenience scripts to docker images


| File                                | Description                                                                               |
|:------------------------------------|:------------------------------------------------------------------------------------------|
| /usr/local/bin/apk-install          | `apk add` wrapper for Alpine                                                              |
| /usr/local/bin/apk-upgrade          | Upgrades all packages on Alpine Linux                                                     |
| /usr/local/bin/apt-add-repository   | Wrapper for `apt-add-repository` with auto cleanup                                        |
| /usr/local/bin/apt-install          | `apt-get install` wrapper for Debian/Ubuntu with auto cleanup                             |
| /usr/local/bin/apt-update           | `apt-get update` wrapper for Debian/Ubuntu for multiple apt-install runs                  |
| /usr/local/bin/apt-upgrade          | `apt-get dist-upgrade` wrapper for Debian/Ubuntu with auto cleanup                        |
| /usr/local/bin/yum-install          | `yum install` wrapper for RedHat with auto cleanup                                        |
| /usr/local/bin/yum-upgrade          | `yum upgrade` wrapper for RedHat with auto cleanup                                        |
| /usr/local/bin/docker-image-cleanup | Cleanup for docker images after package installations                                     |
| /usr/local/bin/docker-image-info    | Gets information about the current docker images (run `generate-dockerimage-info before`) |
| /usr/local/bin/generate-locales     | Generates system locales (eg. for number or date formatting)                              |


## Usage

### General docker images

    RUN umask 0022 \
        && wget -O /tmp/baselayout.tar.gz https://github.com/webdevops/Docker-Image-Baselayout/archive/latest.tar.gz \
        && tar  --no-same-permissions --strip-components=2 -xf /tmp/baselayout.tar.gz  -C / \
        && rm -f /tmp/baselayout.tar.gz

### Alpine

    RUN umask 0022 \
        && apk add --no-cache ca-certificates wget \
        && update-ca-certificates \
        && wget -O /tmp/baselayout.tar.gz https://github.com/webdevops/Docker-Image-Baselayout/archive/latest.tar.gz \
        && tar --no-same-permissions --strip-components=2 -xf /tmp/baselayout.tar.gz  -C / \
        && rm -f /tmp/baselayout.tar.gz