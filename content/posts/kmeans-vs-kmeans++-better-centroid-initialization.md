---
title: "K-Means vs K-Means++: Smarter Centroids, Better Clusters"
date: 2025-06-30
tags: ["machine learning", "unsupervised learning", "clustering", "kmeans"]
description: "K-Means++ improves K-Means by choosing better initial centroids using a distance-aware probability distribution. A couple of thoughts on it as I read through this again today."
math: true
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
---

K-Means++ is a clever upgrade to K-Means that fixes its biggest flaw: random initialization.

Instead of picking all *k* centroids at random, K-Means++:

1. Picks the first centroid randomly from the data points.
2. For each remaining point \( x \), compute its shortest distance \( D(x) \) to the nearest chosen centroid.
3. Choose the next centroid from the dataset with probability proportional to \( D(x)^2 \).
4. Repeat until \( k \) centroids are selected.

This spreads centroids out more effectively and leads to:

- Faster convergence  
- Better clustering quality  
- Fewer bad runs

---

![K-Means++ Advantages of Careful Seeding by David Arthur & Sergei Vassilvitskii](/images/blog/k-means++.png)

### 📐 Theoretical Works

Let:

- ```j_opt``` = the optimal value of the K-Means objective function  
- ```j_init``` = the expected value after K-Means++ initialization  

Then:

```E[j_init] ≤ 8(log k + 2) · j_opt```

This means K-Means++ gives a solution not too far from what we would like and of coruse far better than random seeding.

> For the full math, read *"k-means++: The Advantages of Careful Seeding"* by Arthur and Vassilvitskii (2007).

If you're clustering anything important try and skip random. Start with ++ and then see where it takes you.
