# Images

!!! tip "Pre-build images"

    Open Voice OS provides pre-build images available on [Docker Hub](https://hub.docker.com/u/smartgic). These images are referenced by default within the `docker-compose.*.yml` files.

Open Voice OS is a sofisticated piece of software which has several [components](../../about/glossary/components.md). These components have been split into containers to provide a better isolation and a microservice approach.

## Supported CPU architectures

Container images could be build for different CPU architecture using the [multi-platform images](https://docs.docker.com/build/building/multi-platform/) feature.

| CPU architecture                                                 | Description                                                                |
| ---------------------------------------------------------------- | -------------------------------------------------------------------------- |
| :material-check-circle-outline:{ style="color: green"} `amd64`   | Such as AMD and Intel processors                                           |
| :material-check-circle-outline:{ style="color: green"} `aarch64` | Such as Raspberry Pi 64-bit                                                |
| :material-close-circle-outline:{ style="color: red" } `armlv7`   | Such as Raspberry Pi 32-bit (*not supported because of `onnxruntime`[^1]*) |

## Containers

The list below is not exhaustive and doesn't mention anything about skill containers, but it is a fair list of the main components currently supported in [ovos-docker](https://github.com/OpenVoiceOS/ovos-docker).

| Container                | Description                                                                                   |
| ------------------------ | --------------------------------------------------------------------------------------------- |
| `ovos_messagebus`        | [Read more about ovos-messagebus](../../about/glossary/components.md#ovos-messagebus)         |
| `ovos_phal`              | [Read more about ovos-phal](../../about/glossary/components.md#ovos-phal)                     |
| `ovos_phal_admin`        | [Read more about ovos-phal admin variant](../../about/glossary/components.md#ovos-phal)       |
| `ovos_audio`             | [Read more about ovos-audio](../../about/glossary/components.md#ovos-audio)                   |
| `ovos_listener`          | [Read more about ovos-listener](../../about/glossary/components.md#ovos-listener)             |
| `ovos_core`              | [Read more about ovos-core](../../about/glossary/components.md#ovos-core)                     |
| `ovos_cli`               | [Read more about ovos-cli](../../about/glossary/components.md#ovos-cli)                       |
| `ovos_gui_websocket`     | [Read more about ovos-gui-messagebus](../../about/glossary/components.md#ovos-gui-messagebus) |
| `ovos_gui`               | [Read more about ovos-gui](../../about/glossary/components.md#ovos-gui)                       |
| `ovos_hivemind_listener` | [Read more about hivemind-listener](../../about/glossary/terms.md#hivemind)                   |
| `ovos_hivemind_cli`      | [Read more about hivemind-cli](../../about/glossary/terms.md#hivemind)                        |

## Tags

Container image tags allows you to deploy a specific version of Open Voice OS, it could be an untested version based on nigthly build or a stable build.

| Image tag                                                       | Description                                                          |
| --------------------------------------------------------------- | -------------------------------------------------------------------- |
| :material-check-circle-outline:{ style="color: green"} `alpha`  | Nightly build based on alpha releases from [PyPi](https://pypi.org/) |
| :material-check-circle-outline:{ style="color: green"} `0.0.8a` | Nightly build based on alpha releases from [PyPi](https://pypi.org/) |
| :material-close-circle-outline:{ style="color: red" } `stable`  | Build at every new stable release                                    |
| :material-close-circle-outline:{ style="color: red" } `0.0.8`   | Build at every new stable release                                    |

!!! warning "Stable release"

    As Open Voice OS doesn't have a stable release for version `0.0.8` which has been designed to work with containers, there is no `stable` or `0.0.8` tags available.

## Volumes

To allow data persistence, Docker or Podman volumes are required, they will prevent downloading the requirements everytime the containers are re-created.

| Volume                  | Description                                                                                                                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `ovos_listener_records` | [Wake word](../../about/glossary/terms.md#wake-word) and [utterance](../../about/glossary/terms.md#utterance) recorded samples  |
| `ovos_models`           | Models downloaded by `precise-lite` wake word plugin                                                                            |
| `ovos_nltk`             | [Punkt](https://www.askpython.com/python-modules/nltk-punkt) Python package required by [NLTK](https://www.nltk.org/index.html) |
| `ovos_vosk`             | Models downloaded by [VOSK](https://alphacephei.com/vosk/) during the initial boot                                              |

`ovos_listener_records` allows you to store samples of wake words and utterances which could help you to build or improve models.

!!! info "Enable samples recording"

    By default, the recording features are disabled, `"record_wake_words": true` and `"save_utterances": true` will have to be added to the `listener` section of `mycroft.conf` to enable these capabilities.

    ```json title="mycroft.conf"
    {
    "listener": {
        "record_wake_words": true,
        "save_utterances": true
      }
    }
    ```

    But first thing's first you need to have Open Voice OS's containers up and running. [Follow the guide](./installation/requirements.md).

[^1]: <https://github.com/microsoft/onnxruntime/issues/15337>