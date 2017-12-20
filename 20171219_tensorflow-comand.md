## tensorflow 命令学习（一）

1、[tf.truncate_normal](http://blog.csdn.net/fireflychh/article/details/73692183)

	tf.truncated_normal(shape, mean=0.0, stddev=1.0, dtype=tf.float32, seed=None, name=None)

2、[TensorFlow：tf.nn.max_pool实现池化操作](https://www.2cto.com/kf/201612/572952.html)

第一个参数value：需要池化的输入，一般池化层接在卷积层后面，所以输入通常是feature map，依然是[batch, height, width, channels]这样的shape

第二个参数ksize：池化窗口的大小，取一个四维向量，一般是[1, height, width, 1]，因为我们不想在batch和channels上做池化，所以这两个维度设为了1

第三个参数strides：和卷积类似，窗口在每一个维度上滑动的步长，一般也是[1, stride,stride, 1]

第四个参数padding：和卷积类似，可以取'VALID' 或者'SAME'

3、[TensorFlow的reshape操作 tf.reshape](http://blog.csdn.net/lxg0807/article/details/53021859)

	tf.reshape(tensor, shape, name=None) 