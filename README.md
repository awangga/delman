# delman
Python with Cuda Support

### Tensorflow keras gpu
conda install keras-gpu

import tensorflow as tf
sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))