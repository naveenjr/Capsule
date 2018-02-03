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

Average and standard deviation are calculated by 5 runs.

@NVIDIA TESLA K40m

| System | Accuracy | w/o conf | w/ conf |
|------|:----:|:----:|:----:|
| Normal_CNN (Tensorflow)| 99.46% (99.444±0.016) | 41.47% | 9.97% |
| Normal_CNN (Theano)| 99.45% (99.416±0.026) | 44.83% | 6.94% |
| CapsNet (Tensorflow) - routings 3 | 99.47% (99.438±0.024) | 95.96% | 95.82% |
| CapsNet (Tensorflow) - routings 2 | 99.49% (99.470±0.021) | 96.48% | 96.29% |
| CapsNet (Tensorflow) - routings 1 | 99.55% (99.524±0.016)| 97.43% | 97.32% |
| CapsNet (Theano) - routings 3 | **99.62% (99.578±0.037)** | 91.68% | 91.46% |
| CapsNet (Theano) - routings 2 | 99.61% (99.566±0.034) | 94.54% | 94.34% |
| CapsNet (Theano) - routings 1 | 99.56% (99.534±0.028) | 91.64% | 91.57% |


-----------

The following descriptions are forked from original source: https://github.com/bojone/Capsule

# Capsule

1、相比之前实现的版本：https://github.com/XifengGuo/CapsNet-Keras ，我的版本是纯Keras实现的(原来是半Keras半tensorflow)；

2、通过K.local_conv1d函数替代了K.map_fn提升了好几倍的速度，这是因为K.map_fn并不会自动并行，要并行的话需要想办法整合到一个矩阵运算；

3、其次我通过K.conv1d实现了共享参数版的；

4、代码要在Keras 2.1.0以上版本运行。

http://kexue.fm/archives/4819/
