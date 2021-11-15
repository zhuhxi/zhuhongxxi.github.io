# actor-critic--Asynchronous advantage actor-critic（A3C）

## review policy gradient

$\triangledown \approx \frac{1}{N}\sum\limits^N_{n=1}\sum\limits^{T_n}_{t=1}(\sum^{T_n}_{t^{'}=t}\gamma^{t^{'}-t }r^n_{t^{'}}-b)\triangledown\log p_\theta(a^n_t|s^n_t)$ 采取sample的方式导致$G^n_t$非常不稳定，有极大的variance，如何估测G的期望值？

- state value function $V^\pi(s)$
- state-action value function $Q^{\pi}(s,a)$

## advantage actor-critic

$Q^{\pi}(s_t^n,a_t^n)-V^\pi(s_t^n)$，会带来一定的方差，但只用确定一个网络

- ### tips

  - the parameters of actor $\pi(s)$ and critic $V^\pi(s)$可以共享一部分浅层网络参数
  - use output entropy as regularization for $\pi(s)$

## asynchronous advantage actor-critic(A3C)

鸣人影分身，多个worker进行学习

## pathwise derivative policy gradient

不仅对策略进行打分，并且直接告知应该采取什么行动才是好的
