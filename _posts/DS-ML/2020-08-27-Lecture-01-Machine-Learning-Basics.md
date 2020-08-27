---
title: "Lecture 01 Machine Learning Basics"
date: 2020-08-25 08:26:28 -0400
categories: MachineLearning
category: [DS/ML]
---

Lecture 01 Machine Learning Basics
==================================

## what is ML?

입력을 가지고 확률을 통해 출력을 예상해줌

Supervised learning
- 정해져있는 데이터(labeled examples = training set)를 가지고 학습을 하는 방법
Unsupervised learning
- google news grouping
- word clustering
- training set없이 데이터를 그대로 학습 하는 방법

Supervised learning
- 머신러닝의 일반적인 형태
- Image labeling, Email spam filter, predicting exam score
- training data set이 필수로 있어야 한다.

type of supervised learning

- regression > predicting final exam score based on time spent
- binary classification > pass/non pass based on time spent
- multi - label classification > Letter grade(A,B,C,d AND F)

LAB 1 Tensorflow
=====================================================
google 에서 만든 오픈소스 라이브러리
data flow graphs 를 이용해서 numerical computation하는 라이브러리 이다.

tensorflow 2.0 ver에서는 session 이 없어졌다.

Computational Graph
![matrix](/assets/images/MLyoutube/1.PNG)

Placeholder
![matrix](/assets/images/MLyoutube/2.PNG)
값 node와 더하기 node를 만들어서 파이썬 함수처럼 입력값을 바꿔서 출력값을 마음대로 변경가능 >> 
파이썬의 input 과 같음

tensorflow 2.0 ver에서는 placeholder가 없어졌다.
Variable 을 이용하면 된다.

EX) tf 1.0 ver
```python
import tensorflow as tf
a = tf.placeholder(tf.float32)
b = tf.placeholder(tf.float32)
adder_node = a + b

print(sess.run(adder_node, feed_dict={a:3, b:5}))
print(sess.run(adder_node, feed_dict={a: [1,3], b:[2,4]}))
```

EX)tf 2.0 ver
```python
import tensorflow as tf
a = tf.Variable(1)
b = tf.Variable(2)

@tf.function
def adder(a,b):
    return a + b

result1 = adder(a,b)
print(result1)
```
Tensorflow mechanism
![matrix](/assets/images/MLyoutube/3.PNG)

모든것은 텐서이다. 기본적으로 어레이를 텐서라고 한다.

![matrix](/assets/images/MLyoutube/4.PNG)
RANK 는 몇차 인지, 0차 Scalar, 1차 vector, 2차 matrix 
![matrix](/assets/images/MLyoutube/5.PNG)
Shape은 몇개의 원소가 있는지를 dimension을 가르킨다.
![matrix](/assets/images/MLyoutube/6.PNG)