
## tf.math.is_finite

### [tf.math.is_finite](https://www.tensorflow.org/versions/r2.0/api_docs/python/tf/math/is_finite)
``` python
tf.math.is_finite(
    x,
    name=None
)
```

### [paddle.fluid.layers.isfinite](http://paddlepaddle.org/documentation/docs/zh/1.3/api_cn/layers_cn.html#paddle.fluid.layers.isfinite)
``` python
paddle.fluid.layers.isfinite(x)
```

### 功能差异：

#### 输

## paddlepaddle示例:
```python
# 示例1 
# 结合pad2d，实现SAME方式的padding
# 输入Shape：(None, 3, 200, 200)
# 输出Shape：(None, 5， 67， 67）
# 卷积核Shape: (5, 3, 4, 4)
inputs = paddle.fluid.layers.data(dtype='float32', shape=[3, 200, 200], name='inputs)
pad_inputs = paddle.fluid.layers.pad2d(inputs, paddings=[1, 2, 1, 2])
outputs = paddle.fluid.layers.conv2d(pad_inputs, 5, [4, 4], (1, 1))
