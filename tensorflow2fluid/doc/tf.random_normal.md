## tf.random_normal

### [tf.random_normal](https://www.tensorflow.org/api_docs/python/tf/random/normal)
``` python
tf.random.normal(
    shape,
    mean=0.0,
    stddev=1.0,
    dtype=tf.dtypes.float32,
    seed=None,
    name=None
)
```

### PaddlePaddle实现
PaddlePaddle中目前无对应接口，可使用`create_parameter`和初始化参数组合实现，
``` python
def random_normal(shape, mean=0.0, stddev=1.0, dtype='float32', seed=0):
    data = fluid.layers.create_parameter(shape=shape, dtype=dtype,
       default_initializer=fluid.initializer.Normal(loc=0.0, scale=1.0, seed=seed)
    return data                         
```

### 代码示例
``` python
# 调用上述自定义函数
random_data = random_normal([2, 4, 5], mean=0.0, stddev=1.0)
```
