---
project: Suwayomi-Server-docker
stars: 378
description: |-
    Run Suwayomi-Server in a docker container
url: https://github.com/Suwayomi/Suwayomi-Server-docker
---

# Suwayomi-Server Docker Container

|                                                                                                                                                                                                                                                   Status                                                                                                                                                                                                                                                    |                                                                                                                             Stable                                                                                                                              |                                                                                                                             Preview                                                                                                                              |                                                                      Discord Support                                                                       |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------:|
| [![Build Docker Images](https://github.com/Suwayomi/Suwayomi-Server-docker/actions/workflows/build_container_images.yml/badge.svg)](https://github.com/Suwayomi/Suwayomi-Server-docker/actions/workflows/build_container_images.yml) | [![Latest](https://img.shields.io/badge/dynamic/json?url=https://github.com/Suwayomi/Suwayomi-Server-docker/raw/main/scripts/tachidesk_version.json&label=version&query=$.stable&color=blue)](https://github.com/orgs/suwayomi/packages/container/package/suwayomi-server/) | [![Preview](https://ghcr-badge.egpl.dev/suwayomi/suwayomi-server/latest_tag?color=%231183c3&ignore=preview&label=version&trim=)](https://github.com/orgs/suwayomi/packages/container/package/suwayomi-server) | [![Discord](https://img.shields.io/discord/801021177333940224.svg?label=discord&labelColor=7289da&color=2c2f33&style=flat)](https://discord.gg/DDZdqZWaHA) |

Run [Suwayomi-Server](https://github.com/Suwayomi/Suwayomi-Server) inside docker container as non-root user. The server will be running on http://localhost:4567 open this url in your browser.

Docker Releases - https://github.com/Suwayomi/Suwayomi-Server-docker/pkgs/container/suwayomi-server

Dockerfile - https://github.com/Suwayomi/Suwayomi-Server-docker

_**Suwayomi data location - /home/suwayomi/.local/share/Tachidesk**_

Docker images are mutli-arch (linux/amd64, linux/arm64/v8, linux/ppc64le, linux/s390x, linux/riscv64) and has small size based on Ubuntu linux.

Logs are sent to stdout.
This allows docker to manage the logs; view them using `docker logs --tail=1000 <container name>` or if using the docker-compose file `docker compose logs --tail=1000 suwayomi`.
By default, docker stores logs indefinitely, you can [set up logging globally](https://docs.docker.com/engine/logging/configure/) or edit the [compose file with a logging driver](https://docs.docker.com/reference/compose-file/services/#logging).

### Docker compose

Use the template [docker-compose.yml](./docker-compose.yml) in this repo for creating and starting tachidesk docker container.

# Environment Variables

> [!CAUTION]
> Providing an environment variable will <b>overwrite</b> the current setting value when starting the container.

> [!Tip]
> Most of the time you don't need to use environment variables, instead settings can be changed during runtime via the webUI. (which will be rendered useless when providing an environment variable)

> [!NOTE]
> See [server-reference.conf](https://github.com/Suwayomi/Suwayomi-Server/blob/master/server/src/main/resources/server-reference.conf) in the [Suwayomi-Server](https://github.com/Suwayomi/Suwayomi-Server) repository for the default values

There are a number of environment variables available to configure Suwayomi:

|                Variable                |      Server Default      |                                                                                                                              Description                                                                                                                              |
|:--------------------------------------:|:------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|                 **TZ**                 |        `Etc/UTC`         |                                                                                                              What time zone the container thinks it is.                                                                                                               |
|              **BIND_IP**               |        `0.0.0.0`         |                                                                                        The interface to listen on, inside the container. You almost never want to change this.                                                                                        |
|             **BIND_PORT**              |          `4567`          |                                                                                                                  Which port Suwayomi will listen on                                                                                                                   |
|        **SOCKS_PROXY_ENABLED**         |         `false`          |                                                                                                         Whether Suwayomi will connect through a SOCKS5 proxy                                                                                                          |
|        **SOCKS_PROXY_VERSION**         |           `5`            |                                                                                                                    The version of the SOCKS proxy                                                                                                                     |
|          **SOCKS_PROXY_HOST**          |           ` `            |                                                                                                                    The TCP host of the SOCKS proxy                                                                                                                    |
|          **SOCKS_PROXY_PORT**          |           ` `            |                                                                                                                      The port of the SOCKS proxy                                                                                                                      |
|        **SOCKS_PROXY_USERNAME**        |           ` `            |                                                                                                               The username to log in to the SOCKS proxy                                                                                                               |
|        **SOCKS_PROXY_PASSWORD**        |           ` `            |                                                                                                               The password to log in to the SOCKS proxy                                                                                                               |
|          **DOWNLOAD_AS_CBZ**           |         `false`          |                                                                                                     Whether Suwayomi should save the manga to disk in CBZ format                                                                                                      |
|             **AUTH_MODE**              |          `none`          |                                                                                  Whether Suwayomi requires a login to get in. `none` or `basic_auth` or `simple_login` or `ui_login`                                                                                  |
|           **AUTH_USERNAME**            |           ` `            |                                                                                                                  The username to log in to Suwayomi                                                                                                                   |
|           **AUTH_PASSWORD**            |           ` `            |                                                                                                                  The password to log in to Suwayomi                                                                                                                   |
|            **JWT_AUDIENCE**            |  `suwayomi-server-api`   |                                                                                                                The JWT Audience of the ui_login token                                                                                                                 |
|          **JWT_TOKEN_EXPIRY**          |           `5m`           |                                                                                                   The JWT access token expiry timeout, in ISO-8601 Duration format                                                                                                    |
|         **JWT_REFRESH_EXPIRY**         |          `60d`           |                                                                                                   The JWT refresh token expiry timeout, in ISO-8601 Duration format                                                                                                   |
|               **DEBUG**                |         `false`          |                                                                                               If extra logging is enabled. Useful for development and troubleshooting.                                                                                                |
|           **MAX_LOG_FILES**            |           `31`           |                                                                                                     The max number of days to keep files before they get deleted                                                                                                      |
|         **MAX_LOG_FILE_SIZE**          |          `10mb`          |                                                                              The max size of a log file - Possible values: 1 (bytes), 1KB (kilobytes), 1MB (megabytes), 1GB (gigabytes)                                                                               |
|        **MAX_LOG_FOLDER_SIZE**         |         `100mb`          |                                                                          The max size of all saved log files - Possible values: 1 (bytes), 1KB (kilobytes), 1MB (megabytes), 1GB (gigabytes)                                                                          |
|           **WEB_UI_ENABLED**           |          `true`          |                                                                                                                  If the server should serve a webUI                                                                                                                   |
|           **WEB_UI_FLAVOR**            |         `WebUI`          |                                                                                                                          "WebUI" or "Custom"                                                                                                                          |
|           **WEB_UI_CHANNEL**           |         `stable`         |                                                                        "bundled" (the version bundled with the server release), "stable" or "preview" - the webUI version that should be used                                                                         |
|       **WEB_UI_UPDATE_INTERVAL**       |           `23`           |                                                                          Time in hours - 0 to disable auto update - range: 1 <= n < 24 - how often the server should check for webUI updates                                                                          |
|       **AUTO_DOWNLOAD_CHAPTERS**       |         `false`          |                                                                                             If new chapters that have been retrieved should get automatically downloaded                                                                                              |
|    **AUTO_DOWNLOAD_EXCLUDE_UNREAD**    |          `true`          |                                                                                                  Ignore automatic chapter downloads of entries with unread chapters                                                                                                   |
|  **AUTO_DOWNLOAD_NEW_CHAPTERS_LIMIT**  |           `0`            |                                                           0 to disable - how many unread downloaded chapters should be available - if the limit is reached, new chapters won't be downloaded automatically                                                            |
|   **AUTO_DOWNLOAD_IGNORE_REUPLOADS**   |         `false`          |                                                                                         Decides if re-uploads should be ignored during auto download of new chapters chapters                                                                                         |
|        **DOWNLOAD_CONVERSIONS**        |           `{}`           | Image download conversions, the format is `{ "image/filetype" = { target = "image/filetype" }, "image/filetype" = { target = "image/filetype", compressionLevel=0.6 } }`. You can also use `default` instead of `image/filetype` to add a default conversion handler. |
|          **EXTENSION_REPOS**           |           `[]`           |                                                       Any additional extension repos to use, the format is `["https://github.com/MY_ACCOUNT/MY_REPO/tree/repo", "https://github.com/MY_ACCOUNT_2/MY_REPO_2/"]`                                                        |
|      **MAX_SOURCES_IN_PARALLEL**       |           `6`            |                                 Range: 1 <= n <= 20 - Sets how many sources can do requests (updates, downloads) in parallel. Updates/Downloads are grouped by source and all mangas of a source are updated/downloaded synchronously                                 |
|       **UPDATE_EXCLUDE_UNREAD**        |          `true`          |                                                                                                            If unread manga should be excluded from updates                                                                                                            |
|       **UPDATE_EXCLUDE_STARTED**       |          `true`          |                                                                                                  If manga that haven't been started should be excluded from updates                                                                                                   |
|      **UPDATE_EXCLUDE_COMPLETED**      |          `true`          |                                                                                                          If completed manga should be excluded from updates                                                                                                           |
|          **UPDATE_INTERVAL**           |           `12`           |                                                 Time in hours - 0 to disable it - (doesn't have to be full hours e.g. 12.5) - range: 6 <= n < ∞ - Interval in which the global update will be automatically triggered                                                 |
|         **UPDATE_MANGA_INFO**          |         `false`          |                                                                                                        If manga info should be updated along with the chapters                                                                                                        |
|            **BACKUP_TIME**             |         `00:00`          |                                                                                    Range: hour: 0-23, minute: 0-59 - Time of day at which the automated backup should be triggered                                                                                    |
|          **BACKUP_INTERVAL**           |           `1`            |                                                                         Time in days - 0 to disable it - range: 1 <= n < ∞ - Interval in which the server will automatically create a backup                                                                          |
|             **BACKUP_TTL**             |           `14`           |                                                                         Time in days - 0 to disable it - range: 1 <= n < ∞ - How long backup files will be kept before they will get deleted                                                                          |
|        **FLARESOLVERR_ENABLED**        |         `false`          |                                                                                                         Whether FlareSolverr is enabled and available to use                                                                                                          |
|          **FLARESOLVERR_URL**          | `http://localhost:8191`  |                                                                                                                 The URL of the FlareSolverr instance                                                                                                                  |
|        **FLARESOLVERR_TIMEOUT**        |           `60`           |                                                                                              Time in seconds for FlareSolverr to timeout if the challenge is not solved                                                                                               |
|     **FLARESOLVERR_SESSION_NAME**      |        `suwayomi`        |                                                                                                   The name of the session that Suwayomi will use with FlareSolverr                                                                                                    |
|      **FLARESOLVERR_SESSION_TTL**      |           `15`           |                                                                                                             The time to live for the FlareSolverr session                                                                                                             |
| **FLARESOLVERR_RESPONSE_AS_FALLBACK**  |         `false`          |                                                                                                    Use the response from FlareSolverr if Suwayomi does not succeed                                                                                                    |
|     **OPDS_USE_BINARY_FILE_SIZES**     |         `false`          |                                                                                        If the file sizes should be displayed in binary (KiB, MiB, GiB) or decimal (KB, MB, GB)                                                                                        |
|        **OPDS_ITEMS_PER_PAGE**         |           `50`           |                                                                                                           How many items to show on a page - 10 <= n < 5000                                                                                                           |
|   **OPDS_ENABLE_PAGE_READ_PROGRESS**   |          `true`          |                                                                                         Track and update your reading progress by page for each chapter during page streaming                                                                                         |
|   **OPDS_MARK_AS_READ_ON_DOWNLOAD**    |         `false`          |                                                                                                      Automatically mark chapters as read when you download them                                                                                                       |
|   **OPDS_SHOW_ONLY_UNREAD_CHAPTERS**   |         `false`          |                                                                                                      Filter manga feed to display only chapters you haven't read                                                                                                      |
| **OPDS_SHOW_ONLY_DOWNLOADED_CHAPTERS** |         `false`          |                                                                                                    Filter manga feed to display only chapters you have downloaded                                                                                                     |
|      **OPDS_CHAPTER_SORT_ORDER**       |          `DESC`          |                                                                                                                            "DESC" or "ASC"                                                                                                                            |
|      **KOREADER_SYNC_SERVER_URL**      | `http://localhost:17200` |                                                                                                                  The URL of the KOReader Sync server                                                                                                                  |
|       **KOREADER_SYNC_USERNAME**       |           ` `            |                                                                                                                        KOReader Sync UserName                                                                                                                         |
|       **KOREADER_SYNC_USERKEY**        |           ` `            |                                                                                                                         KOReader Sync UserKey                                                                                                                         |
|      **KOREADER_SYNC_DEVICE_ID**       |           ` `            |                                                                                                                      The Device-ID for KOReader                                                                                                                       |
|   **KOREADER_SYNC_CHECKSUM_METHOD**    |         `binary`         |                                                                                                                        "binary" or "filename"                                                                                                                         |
|       **KOREADER_SYNC_STRATEGY**       |        `disabled`        |                                                                                                           "prompt", "silent", "send", "receive", "disabled"                                                                                                           |
| **KOREADER_SYNC_PERCENTAGE_TOLERANCE** |    `0.00000000000001`    |                                                                                             Absolute tolerance for progress comparison from 1 (widest) to 1e-15 (strict)                                                                                              |

> [!CAUTION]
> This docker image is known to occasionally fail to work. This seems to be caused by problems in the download. If the logs simply end with `LD_PRELOAD=/opt/catch_abort.so /home/suwayomi/.local/share/Tachidesk/bin/kcef/libcef.so`, please remove the downloaded image and pull again. If this does not help, open a [new issue](https://github.com/Suwayomi/Suwayomi-Server-docker/issues/new).


### Downloads Folder
We do not allow configuration of the downloads folder, since Docker Volumes can handle that instead, here is an example of a docker-compose.yaml that has downloads volume configuration:
```yaml
  suwayomi_server:
    image: ghcr.io/suwayomi/suwayomi-server:stable
    container_name: Suwayomi-Server
    volumes: # The order matters! Make sure the downloads is first in the volume list or it will not work!
      - /example/suwayomi-server/downloads:/home/suwayomi/.local/share/Tachidesk/downloads
      - /example/suwayomi-server/files:/home/suwayomi/.local/share/Tachidesk
    ports:
      - 4568:4567
    restart: unless-stopped
```

# Docker tags

## Latest

`ghcr.io/suwayomi/suwayomi-server:latest` 

The latest stable release of the server. Also tagged as `:stable`.

## Preview

`ghcr.io/suwayomi/suwayomi-server:preview`

The latest preview release of the server. Can be buggy!

# Credit

[Suwayomi-Server](https://github.com/Suwayomi/Suwayomi-Server) is licensed under `MPL v. 2.0`.

# License

    This Source Code Form is subject to the terms of the Mozilla Public
    License, v. 2.0. If a copy of the MPL was not distributed with this
    file, You can obtain one at http://mozilla.org/MPL/2.0/.

