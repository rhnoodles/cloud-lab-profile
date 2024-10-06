# cloud-lab-profile

~~~
$ lspci | grep -i nvidia
25:00.0 3D controller: NVIDIA Corporation GA100GL [A30 PCIe] (rev a1)

$ sudo apt install linux-image-nvidia-6.2
$ sudo reboot

$ sudo apt-get install g++ freeglut3-dev build-essential libx11-dev     libxmu-dev libxi-dev libglu1-mesa-dev libfreeimage-dev libglfw3-dev zlib1g
$ sudo apt-get install linux-headers-$(uname -r)
$ wget https://developer.download.nvidia.com/compute/cuda/12.1.0/local_installers/cuda_12.1.0_530.30.02_linux.run

$ sudo sh ./cuda_12.1.0_530.30.02_linux.run
===========
= Summary =
===========

Driver:   Installed
Toolkit:  Installed in /usr/local/cuda-12.1/

Please make sure that
 -   PATH includes /usr/local/cuda-12.1/bin
 -   LD_LIBRARY_PATH includes /usr/local/cuda-12.1/lib64, or, add /usr/local/cuda-12.1/lib64 to /etc/ld.so.conf and run ldconfig as root

To uninstall the CUDA Toolkit, run cuda-uninstaller in /usr/local/cuda-12.1/bin
To uninstall the NVIDIA Driver, run nvidia-uninstall
Logfile is /var/log/cuda-installer.log
~~~

## Setup vLLM
~~~
$ pip install vllm

## allow nvidia repo packages
$ wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
$ sudo dpkg -i cuda-keyring_1.1-1_all.deb

## cuDNN samples
$ wget https://developer.download.nvidia.com/compute/cudnn/redist/cudnn_samples/source/cudnn_samples-source-9.4.0.58-archive.tar.xz

## cuDNN lib and headers
$ wget https://developer.download.nvidia.com/compute/cudnn/redist/cudnn/linux-x86_64/cudnn-linux-x86_64-9.4.0.58_cuda12-archive.tar.xz
$ sudo cp include/cudnn.h /usr/local/cuda/include
$ sudo cp lib64/libcudnn* /usr/local/cuda/lib64
$ sudo chmod a+r /usr/local/cuda/lib64/libcudnn*

## setup nccl
$ sudo apt install libnccl2 libnccl-dev

## setup PATHS
$ export PATH=$PATH:/usr/local/cuda-12.1/bin:/users/hand32/.local/bin
$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-12.1/lib64:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64
~~~