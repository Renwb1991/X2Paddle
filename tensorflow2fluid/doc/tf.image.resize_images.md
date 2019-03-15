
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
    align_mode=1)
```

#### 功能差异：
##### 参数类型差异：
tensorflow：使用`axis`指定要增加维度的位置，支持负数进行索引，并且`axis`可以是python scalar也可以是`tf.tensor`；  

paddlepaddle：使用`axes`表示要增加维度的位置列表，支持在多个位置同时增加维度，也支持负数进行索引，但是`axes`只能是python list。


#### paddlepaddle示例:
```python
# 输入 tensor t 的 shape 为[3, 4]

# 输出 tensor out 的 shape 为[1, 3, 4]
out = fluid.layers.unsqueeze(t, [0])  

# 输出 tensor out 的 shape 为[3, 4, 1]
out = fluid.layers.unsqueeze(t, [-1])

# 输出 tensor out 的 shape 为[1, 1，3, 4]
out = fluid.layers.unsqueeze(t, [0, 1])  
```

