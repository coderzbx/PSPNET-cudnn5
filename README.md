## Pyramid Scene Parsing Network `(support CUDA 8.0 and cuDNN v.5)`

by Hengshuang Zhao, Jianping Shi, Xiaojuan Qi, Xiaogang Wang, Jiaya Jia, details are in [project page](https://hszhao.github.io/projects/pspnet/index.html).

### Introduction

This repository is for '[Pyramid Scene Parsing Network](https://arxiv.org/abs/1612.01105)', which ranked 1st place in [ImageNet Scene Parsing Challenge 2016](http://image-net.org/challenges/LSVRC/2016/results). The code is modified from Caffe version of [hszhao](https://github.com/hszhao/PSPNet) and [DeepLab v2](https://github.com/xmyqsh/deeplab-v2) which support `cuDNN v.5`.

There is still something wrong in `make runtest` `evaluation` `python` `matlab` `examples` `docs` ... parts. You can skip them, or try to modify them by yourself.

### Installation

* Unbuntu 16.04
* CUDA 8.0
* cuDNN v.5
* other dependency packages 
	- if you have Anaconda and `${anaconda_home}/bin` in `$PATH`, you can install the missing package by `conda`. 
	  For example, 
	  ```shell
	  # check your PATH
	  echo $PATH
	  # install packages
	  conda install opencv openssl libgcc -y
	  ```

For installation, please follow the instructions of [Caffe](https://github.com/BVLC/caffe) and [DeepLab v2](https://bitbucket.org/aquariusjay/deeplab-public-ver2). To enable cuDNN for GPU acceleration, cuDNN v.5 is needed. If you meet error related with 'matio', please download and install [matio](https://sourceforge.net/projects/matio/files/matio/1.5.2) as required in 'DeepLab v2'.

The code has been installed successfully on Ubuntu 16.04 with CUDA 8.0

### Usage

1. Clone the repository:

	```shell
	git clone https://github.com/BassyKuo/PSPNET-cudnn5.git
	```

2. Build Caffe:

	```shell
	cd $PSPNET_DIR
	cp Makefile.config.example Makefile.config
	vim Makefile.config 
	# uncomment configures which you need, then save the file

	mkdir build; cd build
	cmake .. -Wno-dev
	make all -j32
	make install -j32

	# If you need the python interface, add the PSPNET path to the `PYTHONPATH`
	export PYTHONPATH=${PSPNET_DIR}/python:${PYTHONPATH}
	```

	Check it is installed successfully or not.
	```shell
	$ python -c "import caffe; print caffe.__version__"
	1.0.0-rc3
	```

## Citation

If PSPNet is useful for your research, please consider citing:

    @inproceedings{zhao2017pspnet,
      author = {Hengshuang Zhao and
                Jianping Shi and
                Xiaojuan Qi and
                Xiaogang Wang and
                Jiaya Jia},
      title = {Pyramid Scene Parsing Network},
      booktitle = {Proceedings of IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
      year = {2017}
    }