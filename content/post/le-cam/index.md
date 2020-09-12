---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Lower Bound for Active Learning in Bandits via Le Cam's method"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-08-26T23:36:19-07:00
lastmod: 2020-08-26T23:36:19-07:00
featured: false
draft: false
header-includes:
    - \usepackage{bbm}

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

**Summary:** _<span style="color:#586199">
We introduce  LeCam's method for obtaining minimax lower bounds for statistical estimation 
problems, which proceeds by relating the probabililty of error of a binary hypothesis testing problem to the total-variation distance between the two distributions. Then, as a novel application,  we use this technique to derive lower bound on the problem of 
active learning in bandits which shows the near optimality of the existing algorithms 
due to Antos et al. (2008) and Carpentier et al. (2011). </span>_

---

Consider the following setting: 
* Suppose $\mathcal{P}$ denotes a class of probability distributions, 
* $(\mathcal{D}, d)$ is a metric space[^1], 
* $\theta: \mathcal{P} \mapsto \mathcal{D}$ represents some $\mathcal{D}$-valued functional, 
* $\mathcal{D}_1, \mathcal{D}_2$ represent two disjoint and $2\delta$ separated subsets of $\mathcal{D}$, for some $\delta>0$, 
* $\mathcal{P}_i = \theta^{-1}(\mathcal{D}_i )$ for $i=1,2$ are non-empty disjoint subsets of $\mathcal{P}$.

Suppose we are given a sample $X \sim P$ taking values in some set $\mathcal{X}$  for  $P \in \mathcal{P}$, and let $\hat{\theta}: \mathcal{X} \mapsto \mathcal{D}$ denote an estimator of $\theta(P)$. Then for any estimator $\hat{\theta}$ we can obtain the following lower bound on the maximum expected error: 

> __Lemma 1 (Le Cam).__ With the definitions introduced above, we have 
$$
\sup_{P \in \mathcal{P}} \mathbb{E}_P \left[ d \left( \hat{\theta}, \, \theta(P) \right) \right] \geq 
\delta \max_{P_i \in \mathcal{P}_i} \left(1 - d_{TV}\left(P_1, P_2 \right) \right). 
$$

In the above display, $d_{TV}$ denotes the [total variation distance](https://en.wikipedia.org/wiki/Total_variation_distance_of_probability_measures)  between two distributions, defined as $d_{TV}(P, Q) = \sup_{E } P(E) - Q(E)$ where the supremum is over all measurable sets $E$. 
The result above implies that the minmax lower bound for a particular estimation problem is 
large if there exist two distributions $P_1$ and $P_2$ which (i) are 'well-separated' in terms of the $d-$metric, and 
(ii) are statistically 'close' in terms of $d_{TV}(\cdot, \cdot)$. Due to their opposing nature, 
obtaining the best lower bound requires finding the right balance between these two requirements. 


The statement of the above result and its proof are based on the statement and proof of Lemma~1 in <span style="color:blue">
(Yu, 1997)[^5]</span>. 
#### Proof of the Lemma

First, we select arbitrary $P_i \in \mathcal{P}_i$ for $i=1,2$ and lower-bound the supremum over all $P \in \mathcal{P}$ with a simple average over these two distributions. 

$$
\sup_{P \in \mathcal{P}}\\;\mathbb{E}_P \left[ d \left( \hat{\theta}, \, \theta(P) \right) \right]  
\geq \frac{1}{2} \left(  \mathbb{E}_{P_1} \left[ d \left( \hat{\theta}, \, \theta(P_1) \right) \right] + 
 \mathbb{E}_{P_2} \left[ d \left( \hat{\theta}, \, \theta(P_2) \right) \right]\right ) 
$$
Next, with the notation $\theta_i = \theta(P_i)$, we observe[^2] the following: for any 
$\theta \in \mathcal{D}$ such that $d(\theta, \theta_1)< \delta$, we must have $d(\theta, \theta_2)>\delta$. 
Similarly, if $d(\theta, \theta_2)<\delta$ then $d(\theta, \theta_1)>\delta$. Both these results 
follow from the fact that $d$ satisfies the triangle inequality and that $d(\theta_1, \theta_2) \geq 2\delta$. 
Now,  we define the set $E = \left \\{x \in \mathcal{X}\\;:\\; d\left( \hat{\theta}(x), \theta_1 \right) < d\left( \hat{\theta}(x), \theta_2 \right) \right \\}$. Clearly, if $X \in E$, then $d(\hat{\theta}(X), \theta_2) \geq \delta$ and if $X \in E^c$ then 
$d(\hat{\theta}, \theta_1) \geq \delta$.  Together, these results imply that $d(\hat{\theta}, \theta_1)
\geq \delta 1_{E^c}$ and $d(\hat{\theta}, \theta_2) \geq \delta 1_E$ where $1_E$ denotes the indicator function 
associated with a set $E$. 
Thus we have 
$$
\begin{aligned}
\sup_{P \in \mathcal{P}}\\;\mathbb{E}_P \left[ d \left( \hat{\theta}, \\, \theta(P) \right) \right] & 
\geq \frac{1}{2} \left(  \mathbb{E}_{P_1} \left[ d \left( \hat{\theta}, \\, \theta(P_1) \right) \right] + 
 \mathbb{E}_{P_2} \left[ d \left( \hat{\theta}, \\, \theta(P_2) \right) \right]\right ) \\\\
 & \geq \frac{1}{2} \left( \mathbb{E}_{P_1}[\delta 1_{E^c}  ]  + \mathbb{E}_{P_2}[\delta 1_{E}]\right) \\; = \\; 
  \frac{\delta}{2} \left( P_1(E^c) + P_2(E)  \right) \\\\
 & \geq \frac{\delta}{2} \left( 1 - \left(P_1(E) - P_2(E) \right)  \right) \\\\
 & \geq \frac{\delta}{2} \left( 1 - \sup_{E \subset \mathcal{X}}\left(P_1(E) - P_2(E) \right)  \right) \\\\
 & = \frac{\delta}{2} \left( 1 - d_{TV}(P_1, P_2)  \right) \\\\
\end{aligned}
$$

Finally, the result follows by noting the fact that the distributions $P_i \in \mathcal{P}_i$ 
were chosen arbitrarily, and hence we can take a supremum over all such $P_i$.

--- 

### Application to Active Learning in Bandits.

We first describe the problem of active learning in $K$-armed bandits.  A [multi-armed bandit (MAB)](https://en.wikipedia.org/wiki/Multi-armed_bandit)
problem~(with $K$ arms) consists of $K$ distributions $(P_1, \ldots, P_K)$ which can be individually 
sampled by an agent. 
In the problem of *active learning in bandits*, given a total sampling budget of $n$,
the goal of an agent is to allocate these $n$ samples among 
these $K$ distributions, in order to learn their means uniformly well. More specifically, suppose 
the agent allocates $T_i \geq 1$ samples to distribution $P_i$, with $\sum_{i=1}^K T_i = n$ 
and constructs the empirical estimate of the mean of $P_i$, $\hat{\mu}_i(T_i) = \frac{1}{T_i}\sum_{j=1}^{T_i}X_{i,j}$. 
Then the goal is to find the allocation $(T_1, \ldots, T_K)$ which solves 

$$
\begin{aligned}
\min_{T_1, \ldots, T_K: \sum_{i=1}^K T_i = n} \\;\max_{1 \leq i \leq K} \\; \mathbb{E} \left[ |\hat{\mu_i}(T_i) - \mu_i|^2\right] = \left( \max_{1 \leq i \leq K}\frac{ \sigma_i^2}{T_i} \right ) \stackrel{\text{def}}{=}\mathcal{L}(T_1, \ldots, T_K)
\end{aligned}
$$
Allowing, for $T_i$ to take real values, the optimal allocation for this above problem is 
given by $T_i^* = \frac{ \sigma_i^2 n}{\Sigma}$ where $\Sigma = \sum_{i=1}^K \sigma_i^2$. 
Clearly, the optimal allocation $(T_1^*, \ldots, T_K^*)$ depends on the variance of the 
distributions $(P_i)_{i=1}^K$ which are unknown to the agent, and the task  
is to design an adaptive sampling strategy which appropriately addresses this [explore-exploit dilemma](https://journals.plos.org/plosone/article/file?id=10.1371/journal.pone.0095693&type=printable) 
and  ends up with an allocation $(T_1, \ldots, T_K)$ which is close to the optimal. 


#### Lower bound construction
Consider two Bernoulli distributions $U \sim \text{Ber(u)}$ and $V \sim \text{Ber}(v)$ with $1/2 < v < u <1$ and 
let $\mathcal{M} = (U, V)$ and $\mathcal{N} = (V, U)$ be two two-armed bandit problems. Suppose an allocation scheme 
$\mathcal{A}$ is applied on one of these two problems and results in an allocation $(T_1, T_2)$. Then we have the 
following result, which informally says that for $u, v$ close enough, no algorithm can perform well on both the 
problems. 

> __Proposition 2.__ We have the following:
$$
\inf_{\mathcal{A}}\\; \max_{\mathcal{M}, \mathcal{N}}\\; \max_{i =1, 2}\\; \mathbb{E}\left[ |T_i - T_i^*| \right] = \Omega (\sqrt{n}).
$$


*Proof of Proposition 2.* Together with the MAB instance (i.e., either $\mathcal{M}$ or $\mathcal{N}$), 
the allocation scheme $\mathcal{A}$ induces a probability distribution on the space of action-observation 
sequences $(a_1, X_1, a_2, X_2, \ldots, a_n, X_n)$ where each action $a_t \in \\{1,2\\}$ and the observations 
$X_t$ lie in $\\{0, 1\\}$ since the distributions $U$ and $V$ are Bernoulli.  We will denote the two resulting 
probability distributions by $P_1$ and $P_2$, corresponding to MABs $\mathcal{M}$ and $\mathcal{N}$ respectively. 

We also introduce the notations $T_U^* = \frac{\sigma_U^2 n}{\sigma_U^2 + \sigma_V^2}$ and 
$T_V^* = \frac{\sigma_V^2 n}{\sigma_U^2 + \sigma_V^2}$. Then under the MAB $\mathcal{M}$ the 
optimal allocations are $(T_1^*, T_2^*) =(T_U^*, T_V^*)$, while they are flipped for the MAB 
$\mathcal{N}$. Since we have assumed that $u>v$, we must have $\sigma_U^2 < \sigma_V^2$ which 
implies that $T_U^* < n/2 < T_V^*$. 

To apply Lemma~1 to this problem, we introduce the following notations keeping the algorithm $\mathcal{A}$ fixed.
* We choose $\mathcal{P}$ to be the set $\\{P_1, P_2\\}$ where $P_i$ for $i\in \\{1,2\\}$ were defined earlier. Since there are only two elements in $\mathcal{P}$, we trivially have $\mathcal{P}_i = \\{P_i\\}$ for $i \in \\{1,2\\}$. 

* We define $\theta:\mathcal{P} \mapsto \mathbb{R}$ as as the mapping from $P \in \mathcal{P}$ to the corresponding $T_1^* $. That is, $\theta(P_1) = T_U^* $ and $\theta(P_2) = T_V^* $. The metric $d$ is chosen as $d(t_1, t_2) = |t_1 - t_2|$. 


* The estimate $\hat{\theta}$ is the allocation value $T_1$ resulting from the scheme $\mathcal{A}$. Note that since $T_1 + T_2 = n$, we have $|T_1^* - T_1| = |T_2^* - T_2|$. Therefore, we always have $\mathbb{E} [ |T_1-T_1^*| ] = \max_{i = 1,2} \mathbb{E}
[|T_i - T_i^*|]$. 

* Finally, we introduce the notation $\delta = |T_U^* - T_V^*|/2$. 

Within this setting, a direct application of Lemma~1 gives us 
$$
\max_{\mathcal{M}, \mathcal{N}} \\; \max_{i=1,2} \\; \mathbb{E}[|T_i^*-T_i|] \geq 
\delta \left( 1- d_{TV}(P_1, P_2) \right).  \qquad (\star)
$$

Next, we need to obtain a lower bound on $\delta$ and an upper bound on $d_{TV}(P_1, P_2)$. 

__Lower bound on $\delta$:__   First we note that $\sigma_U^2 = u(1-u)$ and $\sigma_V^2 = v(1-v)$ and $2\delta = n \frac{\sigma_V^2 - \sigma_U^2}{\sigma_V^2 + \sigma_U^2}$. With the notation $v = u-\epsilon$ and the fact that $1/2 < v < u < 1$, we can show that $\delta \geq n (u-1/2)\epsilon$. By choosing $u=3/4$, we get $\delta \geq \frac{n\epsilon}{4}$. 

__Upper bound on__ $(d_{TV}(P_1, P_2)):$ To bound $d_{TV}(P_1, P_2)$ we proceed in the following steps: 
$$
\begin{aligned}
d_{TV}(P_1, P_2) & \stackrel{(i)}{\leq} \sqrt{\frac{D_{KL}(P_1, P_2)}{2}} 
\stackrel{(ii)}{=} \sqrt{ \frac{ \mathbb{E}[T_1]d_{KL}(u,v) + \mathbb{E}[T_2]d_{kl}(v,u)}{2} } \\\\
& \stackrel{(iii)}{\leq } 4(u-v) \sqrt{ \frac{ \mathbb{E}[T_1] + \mathbb{E}[T_2] }{6} } = \epsilon \sqrt{\frac{8n}{3} }
\end{aligned}
$$
In the above display, 
* __(i)__ follows from an application of [Pinsker's inequality](https://en.wikipedia.org/wiki/Pinsker%27s_inequality), 
* __(ii)__ follows from the decomposition lemma for KL-divergence for bandits (see Eq.(5) [here](https://banditalgs.com/2016/09/28/more-information-theory-and-minimax-lower-bounds/)), and
* __(iii)__ uses the fact that the bound on KL-divergence for Bernoulli random variables $d_{KL}(u, v) \leq \frac{(u-v)^2}{v(1-v)}$.

Thus plugging these two inequalities back into the inequality $(\star)$, and 
choosing $\epsilon = \sqrt{ \frac{3}{32n} }$ gives us 
$$
\begin{aligned}
\max_{\mathcal{M}, \mathcal{N}} \\; \max_{i=1,2} \\; \mathbb{E}[|T_i^*-T_i|] &\geq 
\frac{n \epsilon}{4} \left(1 - \epsilon \sqrt{\frac{8n}{3}} \right) \\\\
& = \frac{1}{32} \sqrt{ \frac{3n}{2} } = \Omega ( \sqrt{n} )
\end{aligned}
$$

 <div style="text-align: right">$\blacksquare$ </div>

Note that this $\Omega(\sqrt{n})$ lower bound on the deviation of $(T_i)_{i=1}^K$ from 
the optimal allocation $(T_i^*)_{i=1}^K$ complements the corresponding $\mathcal{O} \left( \sqrt{n \log n} \right)$ 
upper bound derived in Theorem~1 of <span style="color:blue"> (Antos et a. 2008)</span>[^3] for their GAFS-MAX algorithm.
A similar upper bound was also obtained by <span style="color:blue"> (Carpentier et al. 2011)[^4] </span> for their UCB-type 
algorithm. Thus our lower bound result demonstrates the near-optimality of these two existing algorithms. 

As a corollary of the above proposition, we can obtain a lower bound on the excess 
loss of any allocation scheme. 

> __Corollary.__ The minimax excess risk for active learning in the case of 2-armed bandit problems satisfies the following:
$$
\inf_{\mathcal{A}}\\; \max_{\mathcal{M}, \mathcal{N}}\\;  \mathbb{E}\left[ \mathcal{L}(T_1, T_2) - 
\mathcal{L}(T_1^*, T_2^*) \right] = \Omega \left( n^{-3/2} \right).
$$

Informally, the proof of the corollary uses the following idea: Since the objective 
function $\mathcal{L}$ at the optimal allocation is equal to $\sigma_i^2/T_i$, the 
deviation from this due to suboptimal allocation $T_i$ is roughly of the order of 
$ (\sigma_i^2/(T_i^*)^2) \times |T_i - T_i^*| = (\Sigma^2/(\sigma_i^2 n^2))\times |T_i^*-T_i|$. The 
result then follows by using the $\Omega(\sqrt{n})$ lower bound on $\max_{i=1,2} \\; |T_i - T_i^*|$ 
from the previous proposition. 



----



[^1]: Note that we only require $d$ to be non-negative, symmetric  and satisfy the triangle inequality for the lemma to work. In fact, as noted in <span style="color:blue"> (Yu, 1997)</span>, even the requirement of triangle inequality can be waived  and the following 'weak'  triangle inequality suffices: for some $A \in (0,1)$ and for any $x,y,z \in \mathcal{D}$, we have $d(x,y ) + d(y, z) \geq A d(x,z)$. 

[^5]:Yu, B. (1997). [Assouad, Fano, and Le Cam.](https://link.springer.com/chapter/10.1007/978-1-4612-1880-7_29) In Festschrift for Lucien Le Cam.

[^2]: It is only at this point that we use the fact that $d$ satisfies the triangle inequality. 

[^3]:  Antos, A., Grover, V., and Szepesvári, C.  '[Active learning in multi-armed bandits.](https://sites.ualberta.ca/~szepesva/papers/Allocation-TCS09.pdf)' *ALT, 2008*

[^4]: Carpentier, A., Lazaric, A., Ghavamzadeh, M., Munos, R., and  Auer, P. '[Upper-confidence-bound algorithms for active learning in multi-armed bandits.](https://arxiv.org/abs/1507.04523)' *ALT, 2011*
