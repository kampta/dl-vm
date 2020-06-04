# Deep Leaninng VM (with docker)

## Caffe2

For running caffe2 codes (also contains codes for [detectron](https://github.com/facebookresearch/Detectron) and [densepose](https://github.com/facebookresearch/DensePose))

```
# build from dockerfile
sudo docker build -t kampta/caffe2-vm:latest -f Dockerfile.caffe2 .

# or run the dockerfile directly
sudo docker run --rm --runtime=nvidia -p 8888:8888 --rm -itd kampta/caffe2-vm:latest

# with bash
sudo docker run --rm -it --runtime nvidia kampta/caffe2-vm bash

```

Running densepose
```
# run the dockerfile directly
sudo docker run --rm -it --runtime=nvidia kampta/caffe2-vm bash

# enter densepose directory
cd /densepose

# run densepose on a file
python tools/infer_simple.py \
    --cfg configs/DensePose_ResNet101_FPN_s1x-e2e.yaml \
    --image-ext jpg \
    --wts https://s3.amazonaws.com/densepose/DensePose_ResNet101_FPN_s1x-e2e.pkl \
    --output-dir DensePoseData/infer_out/ \
    DensePoseData/demo_data/demo_im.jpg
```

## Openpose

Openpose 1.4

```
# build from dockerfile
sudo docker build -t kampta/openpose:1.4 -f Dockerfile.openpose .

# or run the dockerfile directly
sudo docker run --rm -it --runtime=nvidia kampta/openpose:1.4  bash

./build/examples/openpose/openpose.bin \
    --display 0 --render_pose 0 --face --hand \
    --video examples/media/video.avi \
    --write_json output/
```

## Vid2Vid
```
# build from dockerfile
sudo docker build -t kampta/vid2vid:CUDA8-py35 -f Dockerfile.vid2vid .

# or run the dockerfile directly
sudo docker run --rm -it --runtime=nvidia --shm-size 8G kampta/vid2vid:CUDA8-py35 bash

# run example
python train.py --name pose2body_256p_g1 \
    --dataset_mode pose \
    --input_nc 6 --ngf 64 --num_D 2 \
    --resize_or_crop randomScaleHeight_and_scaledCrop --loadSize 384 --fineSize 256 \
    --niter 5 --niter_decay 5 \
    --no_first_img --n_frames_total 12 --max_frames_per_gpu 4 --max_t_step 4 \
    --dataroot datasets/pose
```

## Docker troubleshooting
Remove not running docker containers and associated images
```
sudo docker system prune -a
```
