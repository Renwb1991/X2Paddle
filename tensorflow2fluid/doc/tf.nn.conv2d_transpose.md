
## tf.nn.conv2d_transpose

### [tf.nn.conv2d_transpose](https://www.tensorflow.org/api_docs/python/tf/nn/conv2d_transpose)
``` python
tf.nn.conv2d_transpose(
    value,
    filter,
    output_shape,
    strides,
    padding='SAME',
    data_format='NHWC',
    name=None
)
```

### [paddle.fluid.layers.conv2d_transpose](http://paddlepaddle.org/documentation/docs/zh/1.3/api_cn/layers_cn.html#paddle.fluid.layers.conv2d_transpose)
``` python
paddle.fluid.layers.conv2d_transpose(
    input, 
    num_filters, 
    output_size=None, 
    filter_size=None, 
    padding=0, 
    stride=1, 
    dilation=1, 
    groups=None, 
    param_attr=None, 
    bias_attr=None, 
    use_cudnn=True, 
    act=None, 
    name=None
)
```

### 功能差异：

#### 数据格式

TensorFlow: 默认且目前主流tensorflow模型的输入数据格式为`NHWC`，即表示`(batch，height, width, in_channels)`；
对应输出格式为`(batch, height, width, filters_num)`；卷积核的格式则为`(filter_height, filter_width, in_channels, filters_num)`  
PaddlePaddle：输入数据格式为`NCHW`；输出格式`(batch, filters_num, height, width)`；卷积核格式`(filters_num, in_channels, filter_height, filter_width)`

#### Padding机制
TensorFlow: `SAME`和`VALID`两种选项。当为`SAME`时，padding的计算方式如下所示
```python
# 计算在width上的padding size
# height上的padding计算方式同理
ceil_size = ceil(input_width / stride_width)
pad_size = (ceil_size - 1) * stride_width + filter_width - input_width
pad_left = ceil(pad_size / 2)
pad_right = pad_size - pad_left
```
PaddlePaddle：`padding`参数表示在输入图像四周padding的size大小

## paddlepaddle示例:
```python
# 结合pad2d，实现SAME方式的padding
# 输入Shape：(None, 3, 200, 200)
# 输出Shape：(None, 5， 67， 67）
# 卷积核Shape: (5, 3, 4, 4)
inputs = paddle.fluid.layers.data(dtype='float32', shape=[3, 200, 200], name='inputs)
pad_inputs = paddle.fluid.layers.pad2d(inputs, paddings=[1, 2, 1, 2])
outputs = paddle.fluid.layers.conv2d(pad_inputs, 5, [4, 4], (1, 1))
