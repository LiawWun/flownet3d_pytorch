# flownet3d_pytorch
The pytorch implementation of [flownet3d](https://github.com/xingyul/flownet3d) based on [WangYueFt/dcp](https://github.com/WangYueFt/dcp), [sshaoshuai/Pointnet2.PyTorch](https://github.com/sshaoshuai/Pointnet2.PyTorch) and [yanx27/Pointnet_Pointnet2_pytorch](https://github.com/yanx27/Pointnet_Pointnet2_pytorch)

## Installation

### Requirements
PyTorch>=1.0: https://pytorch.org

```
conda install pytorch==1.6.0 torchvision==0.7.0 cudatoolkit=10.2 -c pytorch
```

scipy>=1.2

numpy

h5py

tqdm

In the lib/src

Replaced all mentions of ```AT_CHECK``` and ```THCState_getCurrentStream(state)``` with ```TORCH_CHECK``` and ```at::cuda::getCurrentCUDAStream()```, respectively.

### Install
Install this library by running the following command:
```bash
cd lib
python setup.py install
cd ../
```
## Training

The processed Flyingthings3d data is provided [here](https://drive.google.com/file/d/1CMaxdt-Tg1Wct8v8eGNwuT7qRSIyJPY-/view?usp=sharing) for download (total size ~11GB).

Then run the following command to train:
```bash
python main.py --exp_name=flownet3d --dataset_path=xx/yy
```
where xx/yy is the dataset path

## Performance comparison
All of the following experiments were tested on a TITAN RTX

1. GPU memory usage:

batch size|flownet3d(GB)|flownet3d_pytorch(GB)
---|---|---
16|16.9|9.1

2. Training time per epoch on Flyingthings3d dataset:

batch size|flownet3d(min)|flownet3d_pytorch(min)
---|---|---
16|6.7|3.4
