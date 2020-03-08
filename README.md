# delman
Python with Cuda Support

## Tensorflow 2.1.0 Windows (Untested)
Compile tensorflow 2.0 in old CPU without AVX support
Requirements:
1. tensorflow 2.1.0	
2. python 3.7
3. MSVC 2017
4. Bazel 0.27.1	
5. cuDNN 7.6.5
6. CUDA 10.1 update 1
7. Make sure avoid default set extension /arch:AVX. Please set to unknown option like /arch:SSE4

```sh
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow
git checkout r2.1
cmd admin:
python configure.py

XLA JIT support : no
/arch:SSE4

bazel build --config=opt --config=cuda --define=no_tensorflow_py_deps=true --copt=-nvcc_options=disable-warnings //tensorflow/tools/pip_package:build_pip_package

bazel-bin\tensorflow\tools\pip_package\build_pip_package C:/Users/LENOVO/Downloads/tmp/tensorflow_pkg

pip install package_name
```


## Tensorflow 2.0.0 / 2.0.1 Windows
Compile tensorflow 2.0 in old CPU without AVX support
Requirements:
1. tensorflow_gpu-2.0.0	
2. python 3.7
3. MSVC 2017
4. Bazel 0.26.1	
5. cuDNN 7.4.2.24 (on ubuntu not tested in windows use v7.6.5)
6. CUDA 10.0.130 and replace C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin\cudafe++.exe from CUDA 10.1 update 1(check only to install nvcc)
7. Make sure avoid default set extension /arch:AVX. Please set to unknown option like /arch:SSE4

```sh
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow
git checkout r2.0
cmd admin:
python configure.py

XLA JIT support : no
/arch:SSE4

bazel build --config=opt --config=cuda --define=no_tensorflow_py_deps=true --copt=-nvcc_options=disable-warnings //tensorflow/tools/pip_package:build_pip_package

bazel-bin\tensorflow\tools\pip_package\build_pip_package C:/Users/LENOVO/Downloads/tmp/tensorflow_pkg

pip install package_name
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
