---
title: "Approximating π by Slicing the Circle - from Liu Hui, an acient Chinese mathmaticians"
layout: post
categories: blog
---

In the 3rd century, Chinese mathematician **Liu Hui** [Wikipeida](https://en.wikipedia.org/wiki/Liu_Hui) approximated π, by inscribing regular polygons in a circle and letting the number of sides double. 

Let’s recreate his method in Python!

![Liu Hui polygon approximation – step 1](/assets/images/Liuhui_pi1.png)
![Liu Hui polygon approximation – step 2](/assets/images/LiuHui_pi2.png)

Play with the code, by changing the "n" variables in the code below, 
either at my [google colab](https://colab.research.google.com/drive/1Y7UxuLUH5x6t0dam55hmH56Ai_K78Lxy?usp=sharing) page.


Leave your comments below!


<section id="comments">
  <script src="https://utteranc.es/client.js"
          repo="harveyge/harveyge.github.io"
          issue-term="pathname"
          theme="github-light"
          crossorigin="anonymous"
          async>
  </script>
</section>



## Python Code

```python
# Demo of Liu Hui’s Inscribed Polygon π-Approximation
# Description: use 6,12,24... polygons to inscribe circle, for pi caluation
# Author: Daniel ge
# Date:   2025-05-11
import numpy as np
import matplotlib.pyplot as plt

def draw_inscribed(n):
    angles = np.linspace(0, 2*np.pi, n+1)
    x, y = np.cos(angles), np.sin(angles)
    plt.plot(x, y, '-o', ms=3, label=f"{str(int(n))}-gon")
    # outline to inscribe circle
    theta = np.linspace(0, 2*np.pi, 300)
    plt.plot(np.cos(theta), np.sin(theta), color='gray')

plt.figure(figsize=(9,6))
for n in [6, 12, 24, 36, 48]:  # 6, 12,24,36,48 side polygons
    draw_inscribed(n)
plt.axis('equal'); plt.axis('off')
plt.title("Inscribed Polygons Approaching the Circle")
plt.legend(loc='lower right')
plt.show()

# Approximation accuracy
ns = [6 * 2**k for k in range(7)]  # [6,12,24,...,1536]
perimeters = [n * 2 * np.sin(np.pi / n) for n in ns]
approximations = [P/2 for P in perimeters]

plt.plot(ns, approximations, 'o-', label="P_n/2")
plt.axhline(np.pi, color='gray', linestyle='--', label="π")
plt.xscale('log', base=2)
plt.xlabel("Number of sides (n)")
plt.ylabel("Approximation of π")
plt.title("Liu Hui’s Inscribed Polygon π-Approximation")
plt.legend()
plt.grid(True, ls='--', alpha=0.5)
plt.show()
```
