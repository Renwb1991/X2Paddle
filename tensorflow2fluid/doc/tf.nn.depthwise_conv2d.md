### tf.nn.depthwise_conv2d

#### [tf.nn.depthwise_conv2d](https://www.tensorflow.org/api_docs/python/tf/nn/depthwise_conv2d)

```python
tf.nn.depthwise_conv2d(
    input,
    filter,
    strides,
    padding,
    rate=None,
    name=None,
    data_format=None
)
```

#### [paddle.fluid.layers.conv2d](http://paddlepaddle.org/documentation/docs/zh/1.3/api_cn/layers_cn.html#paddle.fluid.layers.conv2d)

```python
paddle.fluid.layers.conv2d(
    input,
    num_filters,
    filter_size,
    stride=1,
    padding=0,
    dilation=1,
    groups=None,
    param_attr=None,
    bias_attr=None,
    use_cudnn=True,
    act=None,
    name=None
)
```


#### 功能差异


#### 数据格式

TensorFlow：默认输入数据格式为`NHWC`，表示`(batch, height, width, in_channels)`， 同时也将`data_format`参数设为`channels_first`，支持`NCHW`格式的数据输入。其中输入、输出、卷积核对应关系如下表所示，

| 输入 | 卷积核 | 输出 |
|--------------------|-------------------|------------------|
|NHWC | (kernel_h, kernel_w, in_channels, channel_multiplier)| (batch, out_h, out_w, in_channel*channel_multiplier)|
|NCHW | (kernel_h, kernel_w, in_channels, channel_multiplier) | (batch, in_channel*channel_multiplier, out_h, out_w)|

PaddlePaddle: 只支持输入数据格式为`NCHW`，且**卷积核格式**与TensorFlow不同，其中输入、输出、卷积核对应关系如下表所示，

| 输入 | 卷积核 | 输出 |
|--------------------|-------------------|------------------|
|NCHW | (filters_num, in_channels/groups, kernel_h, kernel_w) | (batch, filters_num, out_h, out_w)|

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

#### 参数差异
Tensorflow：普通2维卷积使用`tf.layers.conv2d`  
PaddlePaddle：仍使用本接口，可参考在文档[tf.layers.conv2d](https://github.com/PaddlePaddle/X2Paddle/blob/doc/tensorflow2fluid/doc/tf.layers.conv2d.md)中
