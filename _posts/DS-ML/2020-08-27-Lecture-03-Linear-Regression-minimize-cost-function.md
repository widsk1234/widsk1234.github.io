---
title: "Lecture 03 Linear Regression minimize cost function"
date: 2020-08-26 08:00:57 -0400
categories: MachineLearning
category: [DS/ML]
comments: true
---

Lecture 03 Linear Regression의 cost 최소화 알고리즘
==================================================

![matrix](/assets/images/MLyoutube/12.PNG)
w에 따라서 cost가 달라진다. 이때 cost를 최소화 해야한다.

![matrix](/assets/images/MLyoutube/13.PNG)
cost function은 이렇게 생기게 되는데 
이때 cost의 최소값(0)을 찾기 위해 gradient descent algoritm 을 이용하게 된다. 경사를 타고 내려간다.

아무점에서 시작해서 W,b 를 조금 바꾼후 cost를 줄이고 경사도를 따라 내려감(미분이용)

![matrix](/assets/images/MLyoutube/14.PNG)
2를 나눠준다(계산을 편하게 하기 위해서)

![matrix](/assets/images/MLyoutube/15.PNG)
alpha는 learning rate, 기존 W의 값에 cost를 미분한 값의 -방향으로 간다.

![matrix](/assets/images/MLyoutube/16.PNG)
Gradient descent algorithm 

![matrix](/assets/images/MLyoutube/17.PNG)
cost function의 형태가 convex function 일 때만 항상 값을 정확하게 구해낼 수 있다.