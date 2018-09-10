# Deep Leaninng VM (with docker)

This is a boilerplate docker image for doing most kind of deep learning stuff. It includes latest versions 
(at the time of writing) of cuda, tensorflow, pytorch and caffe. It borrows heavily from [floydhub](https://github.com/floydhub/dl-docker).

## Installation

```
nvidia-docker build -t kampta/dl-docker -f Dockerfile .
nvidia-docker run -it -p 8888:8888 -p 6006:6006 -v /mnt:/mnt kampta/dl-docker bash

```

#### For Azure
Follow instructions [here](https://github.com/NVIDIA/nvidia-docker/wiki/Deploy-on-Azure) to run cuda images on azure VM.
