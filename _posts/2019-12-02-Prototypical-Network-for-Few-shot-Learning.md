---
title: "Prototypical Networks for Few-shot Leanrning"

use_math: true
---


### Notation

$S=\lbrace \left( x_{ 1 },y_{ 1 } \right) ,...,\left( x_{ n },y_{ n } \right) \rbrace$

$x_i \in R^M$ : D-dimension feature vector 

$y_i \in \lbrace1,...,K \rbrace$ : corresponding label

$S_k$: class label이 K인 example set


### Model 

Prototypical Network는 M 차원의 representation $c$를 계산한다. 
embedding function $f_\phi:R^D \rightarrow R^M$ 을 통해 각 class별로 그 class를 대표하는 representation (or prototype) 을 학습한다. 여기서 학습되는 값은 $\phi$이다. 
각 prototype은 결국 각 class에 속하는 데이터 샘플들의 mean vector이다. 

class $C$에 대한 prototype은 다음과 같이 표현된다. 


$$c_{k}=\frac{1}{\left|S_{k}\right|}\sum_{(x_{i},y_{i}) \in S_{ k } }^{  }{ { f }_{ \phi  }({ x }_{ i }) }$$

$$p_{ \phi  }(y=k|x)\quad =\quad \frac { exp(−d(f_{ \phi  }(x),c_{ k })) }{ \sum _{ k' }{ exp(−d(f_{ \phi  }(x),c_{ k }')) }  }$$


class $K$에 대해 $J(\phi)=\log { { p }_{ \phi  } ( y=k )  $를 최소화 하는 방향으로 학습이 진행된다. 

세부 알고리즘은 다음과 같다. 

![algorithm](../_assets/images/algorithm.png?raw=true)

