---
title: ai开发环境搭建
date: 2024-02-21 14:28:05
tags:
---

### 一、配置
- OS： Ubuntu 23.04
- 显卡： GeForce RTX 4060
- 内存： 64G
- 显卡驱动： 530.30.02
- cuda: 12.1.0
- cuDNN: 8.9.0
### 二、显卡驱动
1. 安装
```
方式1：
系统->Software&Updates->Additional Drivers ,选择Using NVIDIA driver metapackage from nvidia-driver-525(proprietary) , Apply Changes即可。
方式2：
卸载干净nvidia显卡驱动，由cuda安装（目前采用这种方式）
```
2. 验证
```
（1）查看显卡型号
    $ lspci | grep -i nvidia
（2）查看显卡驱动版本
    $ cat /proc/driver/nvidia/version
（3）详细的NVIDIA显卡信息
    $ nvidia-smi (-L)
```
### 三、CUDA
CUDA全称Compute Unified Device Architecture，是由NVIDIA推出的一种计算架构，通过CUDA我们可以使用NVIDIA GPU进行计算。

CUDA Toolkit视为开发CUDA程序的工具包（类似于VS之于C++），但我们不仅在开发CUDA程序时需要CUDA Toolkit，很多时候，由于硬件、软件环境的不同，他人编译好的CUDA程序我们是不能直接运行的，于是我们就要在自己的计算机上编译他人写好的CUDA代码
1. 安装
```
下载地址获取：
    https://developer.nvidia.com/cuda-toolkit-archive 选择版本-->runfile(local)
下载：
    wget https://developer.download.nvidia.com/compute/cuda/12.1.0/local_installers/cuda_12.1.0_530.30.02_linux.run
安装：
    sudo sh cuda_12.1.0_530.30.02_linux.run
配置：
    /usr/local目录下软连接设置（切换）
        查看指向：stat cuda
        删除链接：sudo rm -rf cuda
        创建链接：sudo ln -s /usr/local/cuda-12.0 /usr/local/cuda
                sudo ln -s /usr/local/cuda-12.1 /usr/local/cuda
    ~/.bashrc 配置环境变量
        export PATH=$PATH:/usr/local/cuda/bin
        export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
```
2. 验证
```
方式1：
    nvcc -V 
    输出Cuda版本等信息
方式2：
    cuda-samples/Samples/1_Utilities/deviceQuery
        make clean & make
        ./deviceQuery
    输出Result = PASS
```
### 三、cuDNN
NVIDIA cuDNN是用于深度神经网络的GPU加速库。它强调性能、易用性和低内存开销。NVIDIA cuDNN可以集成到更高级别的机器学习框架中，如谷歌的Tensorflow、加州大学伯克利分校的流行caffe软件。简单的插入式设计可以让开发人员专注于设计和实现神经网络模型，而不是简单调整性能，同时还可以在GPU上实现高性能现代并行计算。

1. 安装
```
下载地址获取：
    https://developer.nvidia.com/rdp/cudnn-archive选择cudnn-linux-x86_64对应
下载：
    wget https://developer.download.nvidia.com/compute/cudnn/redist/cudnn/linux-x86_64/cudnn-linux-x86_64-9.0.0.312_cuda12-archive.tar.xz
安装：
解压下载好的tar.xz文件
    tar -xvf cudnn-linux-xxx.tar.xz
将解压的文件拷贝到cuda对应目录，进行cudnn的安装
    sudo cp include/* /usr/local/cuda-12.1/include
    sudo cp lib/libcudnn* /usr/local/cuda-12.1/lib64
    sudo chmod a+r /usr/local/cuda-12.1/include/cudnn*
    sudo chmod a+r /usr/local/cuda-12.1/lib64/libcudnn*
    
删除
    sudo rm -f /usr/local/cuda-12.1/include/cudnn*.h
    sudo rm -f /usr/local/cuda-12.1/lib64/libcudnn* 
```
2. 验证
```
方式1：
    cat /usr/local/cuda/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
方式2：
    cudnn_samples_v8/mnistCUDNN
        make clean & make
        ./mnistCUDNN
    报错：nvcc fatal   : Unsupported gpu architecture 'compute_35'
    修改mnistCUDNN/Makefile:
        ifeq ($(GENCODE_FLAGS),)
        # Generate SASS code for each SM architecture listed in $(SMS)
        #$(foreach sm,$(SMS),$(eval GENCODE_FLAGS += -gencode arch=compute_$(sm),code=sm_$(sm)))
        $(foreach sm,$(filter-out 35,$(SMS)),$(eval GENCODE_FLAGS += -gencode arch=compute_$(sm),code=sm_$(sm)))
    输出Test passed!
```

### 四、CUDA与CUDNN的关系
CUDA看作是一个工作台，上面配有很多工具，如锤子、螺丝刀等。cuDNN是基于CUDA的深度学习GPU加速库，有了它才能在GPU上完成深度学习的计算。它就相当于工作的工具，比如它就是个扳手。但是CUDA这个工作台买来的时候，并没有送扳手。想要在CUDA上运行深度神经网络，就要安装cuDNN，就像你想要拧个螺帽就要把扳手买回来。这样才能使GPU进行深度神经网络的工作，工作速度相较CPU快很多。


### 五、Pytorch
基于conda进行python环境管理，创建环境ai_env，后续相关命令基于该环境进行。

1. 安装
```
下载地址获取：
    https://pytorch.org/get-started/locally/选择CUDA12.1对应命令
安装：
    GPU： conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
    CPU： conda install pytorch torchvision torchaudio cpuonly -c pytorch
```
2. 验证
```
ai_env环境下，执行如下代码：
import torch
print('CUDA版本:',torch.version.cuda)
print('Pytorch版本:',torch.__version__)
print('显卡是否可用:','可用' if(torch.cuda.is_available()) else '不可用')
print('显卡数量:',torch.cuda.device_count())
print('是否支持BF16数字格式:','支持' if (torch.cuda.is_bf16_supported()) else '不支持')
print('当前显卡型号:',torch.cuda.get_device_name())
print('当前显卡的CUDA算力:',torch.cuda.get_device_capability())
print('当前显卡的总显存:',torch.cuda.get_device_properties(0).total_memory/1024/1024/1024,'GB')
print('是否支持TensorCore:','支持' if (torch.cuda.get_device_properties(0).major >= 7) else '不支持')
print('当前显卡的显存使用率:',torch.cuda.memory_allocated(0)/torch.cuda.get_device_properties(0).total_memory*100,'%')

输出：
CUDA版本: 12.1
Pytorch版本: 2.2.0
显卡是否可用: 可用
显卡数量: 1
是否支持BF16数字格式: 支持
当前显卡型号: NVIDIA GeForce RTX 4060 Laptop GPU
当前显卡的CUDA算力: (8, 9)
当前显卡的总显存: 7.7540283203125 GB
是否支持TensorCore: 支持
当前显卡的显存使用率: 0.0 %
```

### 五、显卡驱动 & CUDA & cuDNN & Pytorch版本选择
[参考地址：https://zhuanlan.zhihu.com/p/633473214](https://zhuanlan.zhihu.com/p/633473214)
