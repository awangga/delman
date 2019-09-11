# delman
Python with Cuda Support

### Tensorflow keras gpu
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
