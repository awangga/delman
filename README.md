# delman
Python with Cuda Support

## Tensorflow 2.0 Windows
Compile tensorflow 2.0 in old CPU without AVX support
Requirements:
1. tensorflow_gpu-2.0.0	
2. python 3.7
3. MSVC 2017
4. Bazel 0.26.1	
5. cuDNN 7.4.2.24
6. CUDA 10.0.130 and replace C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin\cudafe++.exe from CUDA 10.1 update 1(check only to install nvcc)
7. Make sure avoid default set extension /arch:AVX set to unknown option like SSE4 or /arch:SSE4

```sh
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow
git checkout r2.0
cmd admin:
python configure.py

/arch:SSE4.2
/arch:SSE4
SSE4

bazel build --config=opt --config=cuda --define=no_tensorflow_py_deps=true --copt=-nvcc_options=disable-warnings //tensorflow/tools/pip_package:build_pip_package
bazel-bin\tensorflow\tools\pip_package\build_pip_package C:/Users/LENOVO/Downloads/tmp/tensorflow_pkg
```


### Tensorflow 1.x keras gpu
Installation of keras gpu :

```sh
conda install python=3.6
conda install keras-gpu
```

test if GPU was connected to the tensorflow

```python
import tensorflow as tf
sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
```

### Check GPU Support in Matlab
To show Existing GPU, in the Command Window of Matlab 
```m
gpuDeviceCount
gpuDevice(1)
```

To use GPUArray

```matlab
g = gpuDevice(1);
M = gpuArray(magic(4));
M_exists = existsOnGPU(M)
```
