# FLUX.1-RealismLora docker

Dockerization of the [Hugging Face FLUX.1-RealismLora Space](https://huggingface.co/spaces/DamarJati/FLUX.1-RealismLora)

![FLUX.1-RealismLora](assets/FLUX.1 RealismLora.png)

 * Space: [https://huggingface.co/spaces/DamarJati/FLUX.1-RealismLora](https://huggingface.co/spaces/DamarJati/FLUX.1-RealismLora)

## Requisites

[Docker](https://docs.docker.com/desktop/) and [nvidia container toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html) must be installed.

## Usage

### Download the image from the Docker Hub

You can download the image and run it

```bash
docker pull maximofn/flux-1-realismlora:latest
./run_app.sh
```

### Build the image

Or you can build the image and run it

```bash
./build_docker_image.sh
./run_app.sh
```