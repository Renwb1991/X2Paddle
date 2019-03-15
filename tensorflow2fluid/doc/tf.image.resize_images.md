
### tf.image.resize_images

#### [tf.image.resize_images](https://www.tensorflow.org/api_docs/python/tf/image/resize_images)
``` python
tf.image.resize_images(
    images,
    size,
    method=ResizeMethod.BILINEAR,
    align_corners=False,
    preserve_aspect_ratio=False
)
```

#### [paddle.fluid.layers.image_resize](http://paddlepaddle.org/documentation/docs/zh/1.3/api_cn/layers_cn.html#paddle.fluid.layers.image_resize)
``` python
paddle.fluid.layers.image_resize(
    input, 
    out_shape=None, 
    scale=None, 
    name=None, 
    resample='BILINEAR', 
    actual_shape=None, 
    align_corners=True, 
    align_mode=1
)
```

#### 功能差异：
##### 参数种类：
tensorflow：支持`BILINEAR`,`NEAREST`,`BICUBIC`, `AREA`四种方式；`preserve_aspect_ratio`设为True后，输入的图像大小长宽比与输入保持一致  
paddlepaddle：支持`BILINEAR`和`NEAREST`两种方式， `align_mode`是`BILINEAR`的可选项，当为1的时候，与TensorFlow功能一致

#### paddlepaddle示例:
```python
# 输
# 输入 tensor t 的 shape 为[3, 4]
```

