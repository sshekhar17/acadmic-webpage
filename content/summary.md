+++
widget = "blank"
title = "Summary of Research"

+++


My research interests mainly lie  in the general area of <span style="color:blue">sequential decision making under uncertainty</span>, where an agent interacts sequentially with an unknown environment in order to maximize some specified reward. As the environment is unknown, the agent is faced with the dilemma between <span style="color:blue"> exploitation and exploration</span>, i.e., acting optimally based on current knowledge of the environment or selecting actions which are most informative about the environment. The goal here is to design appropriate strategies for the agent which have low <span style="color:blue">regret</span>, i.e., sub-optimality w.r.t. a hypothetical agent which acts optimally with full knowledge of the environment.

I have worked on the design and analysis of information acquisition strategies for the following problems which lie within the general framework described above:
1. <span style="color:DarkRed"> Sequential Model Based Optimization</span>
2. <span style="color:DarkRed">Active Learning  </span>
3. <span style="color:DarkRed"> Adaptive Resource Allocation for Statistical Estimation</span>

Besides these, I have also worked on some other problems such as phylogenetic reconstruction and control of parallel queues which are described in the <span style="color:DarkRed"> "Other Results"</span> section below. 


### 1. Sequential Model Based Optimization (SMBO).
In SMBO, the goal of an agent is to design an adaptive strategy to query a noisy and expensive black-box function $f:\mathcal{X}=[0,1]^d\mapsto \mathbb{R}$,   guided by a surrogate model to efficiently learn about its maximizer. 
Most algorithms in this area use Gaussian Processes~(GPs) as surrogates, and  are analyzed either in the fully Bayesian framework~(Bayesian Optimization) or in the frequentist setting~(Kernelized Bandits).
_In my research in this area, I have proposed new algorithms with the best-known theoretical guarantees and lower computational complexity and also derived   algorithm-independent impossibility results characterizing the fundamental performance limits_. 
* [Bayesian Optimization~(BO):](/project/bayesian-optimization) In <span style="color:green">(Shekhar and Javidi, 2018)</span>[^sj2018], we proposed an algorithm which adaptively partitions the input space and zooms into the near-optimal regions.     The main technical result underlying this adaptive partitioning was a  bound on the supremum of a  class of GPs in terms of the radius of their index sets.
The proposed algorithm has lower comlexity and better regret bounds than existing baselines, and can also be extended to deal with _contextual bandits_.
    
* [Kernelized Bandits:](/project/rkhs-function-optimization) Here, $f$ is assumed to be a fixed but unknown element of the RKHS (Reproducing Kernel Hilbert Space) of a given kernel $K$. In <span style="color:green">(Shekhar and Javidi, 2020a)</span> [^sj2020a], we proposed an algorithm which  exploits the embedding of certain RKHS into Holder spaces, to  augment the global GP surrogate with local estimators over an adaptively constructed partition to guide the querying strategy.
The proposed algorithm again achieves improved, and in some cases even minimax near-optimal regret bounds and was also shown to outperform several baselines in empirical benchmarking tasks. 
    
    
* __Incorporating Gradient Information in BO.__
Most prior works  in BO literature only use the _zeroth-order_ information about the unknown function $f$. However, in practice, the agent often has access to the noisy gradient (i.e., first-order) information as well. 
In <span style="color:green">(Shekhar and Javidi, 2020b)</span>[^sj2020b], we  _provided a precise characterization of the  benefits of incorporating gradient information in BO_  by
    1. deriving information theoretic lower bound of $\Omega(\sqrt{2^d n})$ for any zeroth-order algorithm, and
    2. proposing a first-order algorithm which, under some conditions, achieves a $\mathcal{O}(d (\log n)^2 )$ regret.



### 2. Non-parametric Active Learning

The general ideas of using adaptive partitioning and local estimators introduced in our BO and kernelized bandits work is quite versatile, and it can also be utilized  in several related problems with appropriate low-level technical modifications. In <span style="color:green"> (Shekhar and Javidi, 2019) </span>[^sj2019] and 
<span style="color:green"> (Shekhar, Ghavamzadeh and Javidi, 2020) </span>[^sgj2020],    we showed that these ideas are  well suited to the problems of active non-parametric estimation and classification. 

* [GP Level Set Estimation.](/project/bayesian-optimization)
In the level-set estimation problem~(LSE), given a budget $n$, the goal of an agent is to adaptively query a black-box function $f:\mathcal{X}\mapsto \mathbb{R}$, in order to accurately estimate its 
$\tau-$level set of $f$, i.e., the region of $\mathcal{X}$ where $f-$value is at least $\tau$. 
In <span style="color:green"> (Shekhar and Javidi, 2019) </span>[^sj2019], we proposed an algorithm for the LSE problem, which combines the adaptive partitioning strategy  along with a novel point-selection rule  to _achieve tighter theoretical bound_ than existing results.

* [Active Classification with Abstention.](/project/active-learning-for-classification-with-abstention)
    Classification with abstention refers to the classification problems in which the learner can also abstain from declaring a label, i.e., a *"don't know"* option. It  models  several applications such as  medical diagnostic systems,  voice assistant devices and content filtering. In <span style="color:green"> (Shekhar, Ghavamzadeh and Javidi, 2020) </span>[^sgj2020], we proposed  the first active learning algorithm for this problem and __precisely characterized the benefits of active over passive learning   for this problem__. We first obtained information-theoretic lower bound of $ \Omega(n^{-\beta(\alpha+1)/(2\beta + d + \alpha\beta)})$ for the excess risk of any passive algorithm~(here $\alpha$ and $\beta$ are the _margin_ and _smoothness_ parameters resp.). Then, we showed that the corresponding minmax rate in the active setting is $\Theta\left( n^{-\beta(1+\alpha)/(d+2\beta)}\right)$.


### 2. Adaptive Resource Allocation.

In the next project, I worked on the problem of [adaptive resource allocation](https://arxiv.org/abs/1412.6613) among $K$ probability distributions to estimate all of them uniformly well. 
This is motivated by the problem of constructing a uniformly accurate model of the transition structure of an unknown Markov Decision Process (MDP), given a finite exploration budget. 
We studied this problem in two settings:

* [Learning probability distributions with bandit feedback.](/project/adaptive-sampling-for-estimating-probability-distributions/)
In <span style="color:green"> (Shekhar, Javidi and Ghavamzadeh, 2020) </span>[^sjg2020], we worked under the simplifying assumption that the agent can transition between any pair of the $K$ distributions and provided a general treatment for various distance measures such as _total-variation_, _KL-divergence_ and _separation distace_.
Our result greatly expands the scope of this problem, referred to as _active learning in bandits_, as the prior work was restricted to learning the means of $K$ distribution in squared-error sense. 
Additionally, we also proved the optimality of our proposed allocation scheme by deriving information-theoretic lower bounds. 

*    [Estimating Transition Structure of MDPs.](/project/adaptive-sampling-for-estimating-probability-distributions/) In  <span style="color:green"> (Tarbouriech et al, 2020) </span>[^ts+2020], we relaxed the assumption of access to generative model, and proposed an adaptive non-stationary policy to estimate the transition structure of an unknown MDP~(i.e., $K= SA$) in $\ell_1$ distance. Since, here we cannot sample from arbitrary distributions (i.e, the $(s,a)$ pair), the key idea was to implement policies which spend an _appropriate_ fraction of time in the different states. 


### 4. Other Results
Besides my work on sequential learning and optimization described above, I have also worked on the following problems: 

* [Sample Complexity of Species-Tree Estimation](/project/sample-complexity-of-species-tree-estimation/). In <span style="color:green"> (Shekhar, Roch and Mirarab, 2018) </span> [^srm2018] we showed that $\Theta (f^{-2} \log n)$ gene trees are both necessary and sufficient for efficiently reconstructing the underlying species tree for the popular reconstruction algorithm ASTRAL. Here $f$ is the length of the shortest branch and $n$ is the number of leaves (i.e., extant species). 

* [Control of Parallel Queues with Observation Delay.](/Queues.pdf) In <span style="color:green"> (Shekhar, 2017) </span> [^S], we obtained the optimal policy for a system of parallel queues with one server under a fixed observation delay $D>0$. The optimal policy is the one which allocates the server to the queue whose occupancy stochastically dominates that of all other queues. This result generalizes the Longest Connected First (LCF) policy of Tassiulas and Ephreimedes~(1993) to the case of delayed observations. 




---
#### Related Publications
[^sj2018]: Shekhar and Javidi, (2018): Gaussian Process Bandits with Adaptive Discretization. _Electronic Journal of Statistics_ [link](https://projecteuclid.org/euclid.ejs/1543892564)
[^sj2020a]: Shekhar and Javidi, (2020): Multi-scale zero order optimization of smooth functions in an RKHS. _preprint_ [link](https://arxiv.org/abs/2005.04832)
[^sj2020b]: Shekhar and Javidi, (2020): Significance of Gradient Information in Bayesian Optimization. _in preparation_
[^sj2019]: Shekhar and Javidi, (2019): Multiscale Gaussian Process Level Set Estimation._AISTATS_ [link](https://arxiv.org/abs/1902.09682) 
[^sgj2020]: Shekhar, Ghavamzadeh and Javidi, (2020): Active Learning for Classification with Abstention. _ISIT_ [link](https://ieeexplore.ieee.org/abstract/document/9174242)
[^sjg2020]: Shekhar, Javidi and Ghavamzadeh, (2020): Adaptive Sampling for Learning Probability Distributions. _ICML_ [link](https://arxiv.org/abs/1910.12406)
[^ts+2020]: Tarbouriech, Shekhar, Pirotta, Ghavamzadeh and Lazaric, (2020): Active Model Estimation in MDPs. _UAI_ [link](https://arxiv.org/abs/2003.03297)
[^srm2018]: Shekhar, Roch and Mirarab, (2018): Species tree estimation using ASTAL: how many genes are enough? _IEEE TCBB_ [link](https://arxiv.org/abs/1704.06831)
[^S]: Shekhar: Dynamic Server Allocation with Observation Delays. _unpublished_ [link](/Queues.pdf)




