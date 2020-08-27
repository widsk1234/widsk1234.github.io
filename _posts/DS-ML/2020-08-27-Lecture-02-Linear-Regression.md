---
title: "Lecture 02 Linear Regression"
date: 2020-08-26 05:30:28 -0400
categories: MachineLearning
category: [DS/ML]
---


Lecture 02 Linear Regression
=======================================

acknowledge
![matrix](/assets/images/MLyoutube/7.PNG)

Supervised learning시(데이터를 가지고 다음 예측을 할때)
EX) 몇시간을 공부해서 몇점을 맞을지 예상할 때
데이터를 학습시키며(training). 그 데이터를 training data라고 한다.

시험을 치기 전에 몇점을 맞을 수 있을 지 알려달라고 할 때 regression model 에 입력(시간)을 넣으면 된다.

![matrix](/assets/images/MLyoutube/8.PNG)

![matrix](/assets/images/MLyoutube/9.PNG)
이렇게 여러가지 선을 그어서 어떤 선이 가장 알맞은지 찾는 것이 학습(learning)

H(x) = Wx + b
H(x) 는 가설 함수 (Hypothesis) , W,b 에 따라 선이 정해진다.

![matrix](/assets/images/MLyoutube/10.PNG)
Cost function
우리가 만들어낸 가설 함수와 실제 데이터와의 차이가 얼마나 나는 가? 를 cost function 이라고 한다.
보통 distance를 찾기 위해 (H(x)-y)^2

![matrix](/assets/images/MLyoutube/11.PNG)
Linear regression 에서는 cost의 값이 가장 작게하는 W,b를 찾는 것이 중요하다.


LAB 02 Tensorflow로 linear regression 구현
============================================
reduce_mean > 평균값 반환

TF ver 1
```python
import numpy as np
import tensorflow as tf


x_train = [1,2,3,4]
y_train = [0, -1, -2, -3]

W = tf.Variable(tf.random_normal([1]), name='weight')
b = tf.Variable(tf.random_normal([1]), name= 'bias')

hypothesis = x_train * W +b

cost = tf.reduce_mean(tf.square(hypothesis- y_train))

optimizer = tf.train.GradientDescentOptimizer(learning_rate = 0.01)
train = optimizer.minimize(cost)

sess = tf.Session()
sess.run(tf.global_variables_initializer())
for step in range(2001):
    sess.run(train)
    if step % 20 == 0:
        print(step, sess.run(cost), sess.run(W), sess.run(b))
```

TF ver 2

```python
import numpy as np
import tensorflow as tf

x_train = [1, 2, 3, 4]
y_train = [0, -1, -2, -3]

tf.model = tf.keras.Sequential()
# units == output shape, input_dim == input shape
tf.model.add(tf.keras.layers.Dense(units=1, input_dim=1))

sgd = tf.keras.optimizers.SGD(lr=0.1)  # SGD == standard gradient descendent, lr == learning rate
tf.model.compile(loss='mse', optimizer=sgd)  # mse == mean_squared_error, 1/m * sig (y'-y)^2

# prints summary of the model to the terminal
tf.model.summary()

# fit() executes training
tf.model.fit(x_train, y_train, epochs=200)

# predict() returns predicted value
y_predict = tf.model.predict(np.array([1, 2]))
print(y_predict)
```
