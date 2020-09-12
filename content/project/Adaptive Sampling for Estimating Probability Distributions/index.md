---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Active Learning in Bandits and MDPs"
summary: "Optimal scheme for allocating samples to learn $K$ distributions uniformly well."
authors: []
tags: ["Adaptive Sampling", "Bandits"]
categories: ["Active Learning", "Reinforcement Learning"]
date: 2020-06-22T02:09:31-07:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: "Smart"
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: ""
url_pdf: "https://arxiv.org/abs/1910.12406"
url_slides: "https://drive.google.com/file/d/1EacF9bCxDYIaof4e80BtLIimEZnZipf0/view?usp=sharing"
url_video: "https://drive.google.com/file/d/1UwYDrKOwr0e7t5Eag2Xy4JZkvDbtkrya/view?usp=sharing"

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

A $K$-armed bandit problem involves designing a sampling strategy to identify the distribution (i.e., arm) with the largest mean. A related problem, called *active learning in bandits* considers the objective of learning the means of all the $K$ distributions uniformly well in terms of squared error (<span style="color:blue"> (Antos et al., 2008)[^antos2008]</span> and <span style="color:blue"> (Carpentier et al., 2011)[^carpentier2011]</span>. 
 However, in many applications, it is required to learn the entire distribution in terms of some distance metric $D$, and not just the mean.
 For instance, consider the task of constructing an accurate model of an MDP given an exploration budget. 
 This can be framed as the problem of learning the transition probability vectors corresponding to all state-action pairs uniformly well in $\ell_1$ distance. The techniques developed in prior work are not applicable to this problem. 

#### Learning distributions with bandit feedback

In <span style="color:blue"> (Shekhar et al., 2019)[^shekhar2019]</span>, we proposed a general sampling scheme for learning multiple distributions uniformly well in terms of several commonly used distance metrics such as $\ell_2^2$, *total variation*, *$f$-divergence*, and *separation distance*.  Our main contributions were: 

* We began by studying an abstract version of this *tracking* problem, and proposed and analyzed a general optimistic tracking algorithm.   

* Next, we instantiated this algorithm for the specific problem instances arising in the case of the four distance metrics mentioned above, and obtained high probability bounds on the regret.   

* We showed that the allocation performance of our algorithm cannot be improved by deriving matching lower bounds on the allocation performance on any reasonable algorithm.   

* Finally, we showed through empirical evaluation that our proposed scheme works better than *uniform sampling*, *greedy sampling* and *forced exploration sampling* baselines.  


#### Learning MDP models
An obstacle in applying the above ideas to learn MDP models, i.e., the $S \times A$ conditional distributions, is that we cannot  observe arbitrary state-action trasitions in an MDP. This can be addressed by designing policies which spend an appropriate proportion of the time in different state-action pairs, as proposed in <span style="color:blue">(Tarbouriech & Lazaric, 2019)[^tar1]</span>. In <span style="color:blue">(Tarbouriech et al. 2020)[^tar2]</span>, we took this approach and proposed an algorithm and derived sample complexity results of estimating the model of a finite MDP with $\epsilon$ accuracy. Next, we also proposed a heuristic exploration strategy, based on weighted maximum entropy, which outperforms some baselines in experiments. 

### References

[^shekhar2019]: Shekhar, S., Ghavamzadeh, M., & Javidi, T. (2020). Adaptive Sampling for Estimating Multiple Probability Distributions. _ICML_ [link](https://arxiv.org/abs/1910.12406)

[^carpentier2011]: Carpentier, A., Lazaric, A., Ghavamzadeh, M., Munos, R., & Auer, P. (2011). Upper-confidence-bound algorithms for active learning in multi-armed bandits. _ALT_ [link](https://link.springer.com/chapter/10.1007/978-3-642-24412-4_17)

[^antos2008]: Antos, A., Grover, V., & Szepesvári, C. (2008). Active learning in multi-armed bandits._ALT_ [link](https://link.springer.com/chapter/10.1007/978-3-540-87987-9_25)

[^tar1]: Tarbouriech, J., & Lazaric, A. (2019). Active exploration in markov decision processes._AISTATS_. [link](https://arxiv.org/abs/1902.11199)

[^tar2]: Tarbouriech, J., Shekhar, S., Pirotta, M., Ghavamzadeh, M., & Lazaric, A. (2020). Active Model Estimation in Markov Decision Processes. _UAI_.[link](https://arxiv.org/abs/2003.03297)


