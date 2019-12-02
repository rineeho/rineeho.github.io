---
title: "Prototypical Networks for Few-shot Leanrning"

use_math: true
---


### Notation


$S={(x_1,y_1),...,(X_N, y_n)}$

$x_i\in R^D$ : D-dimension feature vector 

$y_i \in {1,...,K}$ : corresponding label

$S_k$: class label이 K인 example set


### Model 


Prototypical Network는 M 차원의 representation $c$를 계산한다. 
embedding function $f_\phi:R^D \rightarrow R^M$ 을 통해 각 class별로 그 class를 대표하는 representation (or prototype) 을 학습한다. 여기서 학습되는 값은 $\phi$이다. 
각 prototype은 결국 각 class에 속하는 데이터 샘플들의 mean vector이다. 

class $C$에 대한 prototype은 다음과 같이 표현된다. 


$$c_{k}=\frac{1}{\left|S_{k}\right|}\sum_{(x_{i},y_{i}) \in S_{ k } }^{  }{ { f }_{ \phi  }({ x }_{ i }) }$$


\begin{align}
\\c_{ k }=\frac { 1 }{ \left| S_{ k } \right|  } \sum _{ (x_{ i },y_{ i })\in S_{ k } }^{  }{ { f }_{ \phi  }({ x }_{ i }) }
\end{align}

\begin{equation}
p_{ \phi  }(y=k|x)\quad =\quad \frac { exp(−d(f_{ \phi  }(x),c_{ k })) }{ \sum _{ k' }{ exp(−d(f_{ \phi  }(x),c_{ k }')) }  }
\end{equation}