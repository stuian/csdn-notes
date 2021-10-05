## tensorflow学习 ##

[tensorflow入门](https://www.tensorflow.org/get_started/get_started)


### tensors ###

    [1., 2., 3.] # a rank 1 tensor; a vector with shape [3]
	[[1., 2., 3.], [4., 5., 6.]] # a rank 2 tensor; a matrix with shape [2, 3]
	[[[1., 2., 3.]], [[7., 8., 9.]]] # a rank 3 tensor with shape [2, 1, 3]

### TensorFlow Core tutorial ###

- 导入tensorflow
- 流程图
	- 设置参数（Variable如W和b）
	- 设置输入和输出,可从外部输入（placeholder）
	- 设置模型结构
	- 设置误差计算和优化方式
	- 训练数据
	- 训练循环
	- （打印）误差分析
	- **别忘了初始化和session运行**


### Complete program ###

    import tensorflow as tf
    
    # Model parameters
    W = tf.Variable([.3], dtype=tf.float32)
    b = tf.Variable([-.3], dtype=tf.float32)
    # Model input and output
    x = tf.placeholder(tf.float32)
    linear_model = W*x + b
    y = tf.placeholder(tf.float32)
    
    # loss
    loss = tf.reduce_sum(tf.square(linear_model - y)) # sum of the squares
    # optimizer
    optimizer = tf.train.GradientDescentOptimizer(0.01)
    train = optimizer.minimize(loss)
    
    # training data
    x_train = [1, 2, 3, 4]
    y_train = [0, -1, -2, -3]
    # training loop
    init = tf.global_variables_initializer()
    sess = tf.Session()
    sess.run(init) # reset values to wrong
    for i in range(1000):
      sess.run(train, {x: x_train, y: y_train})
    
    # evaluate training accuracy
    curr_W, curr_b, curr_loss = sess.run([W, b, loss], {x: x_train, y: y_train})
    print("W: %s b: %s loss: %s"%(curr_W, curr_b, curr_loss))

![](https://www.tensorflow.org/images/getting_started_final.png)

### tf.estimator ###
- running training loops
- running evaluation loops
- managing data sets

> 让模型更容易