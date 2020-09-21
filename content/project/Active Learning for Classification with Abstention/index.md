---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Active Learning for Classification With Abstention"
summary: "A minimax near-optimal active learning algorithm for classification with abstention."
authors: []
tags: ["minmax", "abstention", "classification"]
categories: ["Active Learning", "Learning Theory"]
date: 2020-06-22T02:08:54-07:00
weight: 40

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Histogram of the samples queried by our proposed algorithm for simple 1D functions. See the slides above for further details of this example."
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: ""
url_pdf: "https://arxiv.org/pdf/1906.00303.pdf"
url_slides: "https://drive.google.com/file/d/128rYUGvQym92Ejn0ie3BKCMFQBl1akl9/view?usp=sharing"
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

Classification with abstention refers to the classification problems in which the learner can also abstain from declaring a label, i.e., a *"don't know"* option.
It  models  several applications such as  medical diagnostic systems,  voice assistant devices and content filtering.
In [<span style="color:blue">(Shekhar et al., 2019)</span>](https://arxiv.org/abs/1906.00303), we proposed and analyzed the first active learning algorithm for this problem  motivated by the  approach used in our GP bandits work [<span style="color:blue">(Shekhar and Javidi, 2018)</span>](https://projecteuclid.org/euclid.ejs/1543892564).
The  scheme works for two abstention models: *fixed-cost* and *bounded-rate* and is general enough to work under several active learning paradigms (pool-based, stream-based and membership query). 
The algorithm proposed in [<span style="color:blue">(Shekhar et al., 2019)</span>](https://arxiv.org/abs/1906.00303) performs better than prior passive methods, both theoretically and in experiments. 
Furthermore, we also demonstrate the optimality of our algorithm by deriving *matching  lower bounds* on excess risk. 

