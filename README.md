# delman
Python with Cuda Support

## Installation Cuda
conda install -c anaconda accelerate
conda install -c anaconda numba=0.43
numba -s


### Tensorflow keras gpu
conda install -c anaconda mkl=2017.0
conda install -c anaconda keras-gpu


import tensorflow as tf
sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))