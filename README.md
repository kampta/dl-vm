# Deep Leaninng VM (with docker)

This is a boilerplate docker image for doing most kind of deep learning stuff. It includes latest versions 
(at the time of writing) of cuda, tensorflow, pytorch and caffe. It borrows heavily from [floydhub](https://github.com/floydhub/dl-docker).

## Installation

```
sudo docker build -t kampta/caffe2-vm:latest -f Dockerfile.caffe2 .
sudo docker run --runtime=nvidia -v /home/kampta/dev:/home/kampta/dev -p 8888:8888 --rm -itd kampta/caffe2-vm:latest
```

#### For Azure
Follow instructions [here](https://github.com/NVIDIA/nvidia-docker/wiki/Deploy-on-Azure) to run cuda images on azure VM.

-----------------------------------


## Troubleshooting
Don't use `Dockerfile.all`. Use `Dockerfile.caffe2` instead. 