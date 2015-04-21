## About this

密码学第三次作业，第一部分，图像加密与秘密共享

使用pycrypto模块，先散列后AES加密。

## 大致思路

对N位用户，创建N个密钥。对于第i个密钥Ki，生成方式如下：

1.  构建一个一元i-1次多项式
2.  将i个系数拼接为字符串，通过MD5散列至128bit的值H
3.  以H为基础，生成一个AES密钥Ki(本程序取Ki = H)
  
加密过程中，随机选取N个密钥中的Ki, 并将选取结果存入`key_sequence.txt`中。将每个用户的
密钥碎片存入`keystore_i`中。

##使用方法

运行shareSecrete.py

***TODO 暂时密钥空间是10bit，虽然python是支持128bit的，但是numpy模块的矩阵运算部分对高精度整数的支持比较混乱时间仓促没有弄好***

***希望有大神抽出时间加以贡献完善。提示：需要重新实现key_util.key_restore中的`np.linalg.solve()`方法***
