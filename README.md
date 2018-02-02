# Capsule Implementation with Keras (Theano backend)

(Probably) Fixed a `Runtime Error` with Theano backend.

Also report some numbers with both original code and the fixed code.

Note: There is no guarantee that the code is exactly what the original author thinks.

Enjoy :)

**Original source: https://github.com/bojone/Capsule**

## Note

If you use Keras + Tensorflow: 

- use original code (only work with tf now): https://github.com/bojone/Capsule

- or use `Capsule_TF` layer in `Capsule_Keras.py`

If you use Keras + Theano: use `Capsule_TH` layer in `Capsule_Keras.py`

You should use Keras >= 2.1.0


## Some results (on MNIST)

**TODO: Average and standard deviation will be reported (5 runs).**



-----------

The following descriptions are forked from original source: https://github.com/bojone/Capsule

# Capsule

1、相比之前实现的版本：https://github.com/XifengGuo/CapsNet-Keras ，我的版本是纯Keras实现的(原来是半Keras半tensorflow)；

2、通过K.local_conv1d函数替代了K.map_fn提升了好几倍的速度，这是因为K.map_fn并不会自动并行，要并行的话需要想办法整合到一个矩阵运算；

3、其次我通过K.conv1d实现了共享参数版的；

4、代码要在Keras 2.1.0以上版本运行。

http://kexue.fm/archives/4819/
