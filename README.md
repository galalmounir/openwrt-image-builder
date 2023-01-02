# OpenWRT Image Builder using a Docker container
A docker container to build a OpenWRT firmware image. Useful for automation and CI/CD pipelines.

## Prerequisites
- Docker
- A Mac/Linux host (tested on macOS 13.0 and Ubuntu Github Runner)
- A working internet connection

## Usage
To build an image you will need to specify the OpenWRT version (tag from repo) and the target device. The image will be saved in the `output` folder.

```bash
docker build --build-arg OPENWRT_VERSION=v22.03.2 --build-arg DEVICE=ea8300 -o output . 
```

### Arguments
| Argument            | Description                                    | Default       |
|---------------------|------------------------------------------------|---------------|
| OPENWRT_VERSION     | OpenWRT version to build                       | v21.02.2      |
| DEVICE              | Target device to build the firmware for        | ea8300        |
| SHOULD_ADD_HAASMESH | Whether or not to add HaasMesh to the image    | 0             |
| CPUS                | The number of CPUs/Threads to use for building | All Available |

## Notes
It is normal for the build to take at least 30 minutes. The build process is very resource intensive and will use all available CPU cores.
To limit the number of cores used, you can use the `CPUS` build argument.
