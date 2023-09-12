# Composition and environement files

The easiest and quickest way to install Open Voice OS containers is to use a [composer](./index.md#composer-definition) such as `docker composer` or `podman-compose`.

## Composition files

Composition files provide an easy way to provision the stack *(services and volumes)* with the required options and configuration for each of the services.

| Compose file                         | Platforms                                                                                                                                                                                                               | Description                                                                        |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `docker-compose.yml`                 | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" }                                                                                                           | Install [core](../../about/glossary/components.md) components *(except the GUI)*   |
| `docker-compose.gui.yml`             | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" }                                                                                                           | Install [GUI](../../about/glossary/components.md#ovos-gui) components              |
| `docker-compose.skills.yml`          | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | Install few [skills](../../about/glossary/terms.md#skill)                          |
| `docker-compose.hivemind.yml`        | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | Install [HiveMind](../../about/glossary/terms.md#hivemind) components              |
| `docker-compose.macos.yml`           | :fontawesome-brands-apple:{ .lg title="Mac OS" }                                                                                                                                                                        | Install [core](../../about/glossary/components.md) components *(except the GUI)*   |
| `docker-compose.windows.yml`         | :fontawesome-brands-windows:{ .lg title="Windows WSL2" }                                                                                                                                                                | Install [core](../../about/glossary/components.md) components *(except the GUI)*   |
| `docker-compose.raspberrypi.yml`     | :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" }                                                                                                                                                           | Add GPIO support to `ovos_core` component                                          |
| `docker-compose.raspberrypi.gui.yml` | :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" }                                                                                                                                                           | Add `/dev/vchiq` to `ovos_gui` component                                           |

## Environment files

A Docker environment file is a file that contains lines about environment variables that are usable by the Docker CLI. It is a convenient way to pass many environment variables to a single command.

| Environment file   | Platforms                                                                                                                                                 | Description                                    |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| `.env`             | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | Set of variables used by the compositions file |
| `.env-raspberrypi` | :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" }                                                                                             | Add `GPIO_GID` and `RENDER_GID` variables      |

Some variables might need to be tuned to match your setup such as the `TZ`, `XDG_RUNTIME_DIR`, etc...

| Variable                 | Default | Platforms                                                                                                                                                                                                                           | Description |
| ------------------------ | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| `GPIO_GID`               | `997`               | :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" }                                                                                                                                                           | `gpio` group ID on Raspberry Pi |
| `HIVEMIND_CONFIG_FOLDER` | `~/hivemind/config` | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | HiveMind configuration directory |
| `HIVEMIND_SHARE_FOLDER`  | `~/hivemind/share`  | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | HiveMind shared directory |
| `OVOS_CONFIG_FOLDER`     | `~/ovos/config`     | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | OVOS configureation directory |
| `OVOS_SHARE_FOLDER`      | `~/ovos/share`      | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | OVOS shared directory |
| `OVOS_USER`              | `ovos`              | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | Running user in the container |
| `RENDER_GID`             | `106`               | :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" }                                                                                                                                                           | `render` group ID on Raspberry Pi |
| `TMP_FOLDER`             | `~/ovos/tmp`        | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | OVOS temporary directory |
| `TZ`                     | `America/Montreal`  | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | Timezone to set in the container |
| `VERSION`                | `alpha`             | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-apple:{ .lg title="Mac OS" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" } | Container image tag to pull |
| `XDG_RUNTIME_DIR`        | `/run/user/1000`    | :fontawesome-brands-linux:{ .lg title="Linux" } :fontawesome-brands-raspberry-pi:{ .lg title="Raspberry Pi" } :fontawesome-brands-windows:{ .lg title="Windows WSL2" }                                                  | Path to XDG runtime directory |

!!! bug "Don't change `OVOS_USER`"

    The `OVOS_USER` variable should not be changed except if you build your own container images.

### How to get the GID?

The `getent` command could be used in order to get the `GID` of `gpio` and `render` groups on Raspberry Pi.

=== "Raspberry Pi"

    ```shell
    getent group gpio
    getent group render
    ```

### How to get the UID?

The `XDG_RUNTIME_DIR` variables requires a `UID`, this `UID` is the `ID` of the current user which will run the `docker compose` or `podman-compose` command.

=== "Linux"

    ```shell
    echo $UID
    ```

=== "Windows WSL2"

    ```shell
    echo $UID
    ```

!!! info "XDG Base Directory"

    Mac OS doesn't leverage `XDG_RUNTIME_DIR` variable as there is support of [XDG Base Directory](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html) on Mac OS.