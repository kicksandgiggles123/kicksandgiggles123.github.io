---
title: "Sierpiński Triangle"
layout: post
categories: blog
---

Before the in-depth study of fractal geometry, artists in 16th-century such as lace-makers and stone-carvers created repeating self-similar patterns and created artwork with it. A notable example is the Sierpinski's Triangle:

[source](https://www.formulas.it/formulog/wp-content/uploads/2014/12/sierpinski-aplimat.pdf)

![Sierpinski triangle pattern in 11th centry](/assets/images/Sierpinski Triangle in stone 0.png)
![Sierpinski triangle pattern in 13th centry](/assets/images/Sierpinski Triangle in stone 1.png)

Interestingly, the Sierpinski's triangle also appears naturally:
![Sierpinski triangle pattern in seashell](/assets/images/Sierpinski triangle pattern in seashell.jpg)



<div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;width:100%;max-width:1200px;margin:1em auto;">
  <iframe 
    style="position:absolute;top:0;left:0;width:100%;height:100%;" 
    src="https://www.youtube.com/embed/Fgu5-3ihVVI" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
  </iframe>
</div>


In 1915, the Polish mathematician [Sierpiński](https://en.wikipedia.org/wiki/Sierpi%C5%84ski_triangle) gave this shape its official math name, building on ideas from Georg Cantor’s work on “strange” sets that are everywhere yet take up zero space.
Nowadays folks discovered a playful way to “draw” it by randomly hopping halfway to triangle corners.

You can also play the “Chaos Game”:
- Pick the three corners of a triangle on paper.
- Randomly choose a starting point anywhere inside.
- Repeat: randomly pick one of the three corners, then move halfway from your current point toward that corner, and put a dot.
- Keep doing this thousands of times.
  

Play it in my [google colab](https://colab.research.google.com/drive/1nmMQXP5_PlsqR2GiE97NOby6FYsn4U_y#scrollTo=_b_xyx-hQ8JN) page.

-n=100 
![simulate Sierpinski Triangle n=100](/assets/images/Sierpinski Triangle when n=100.png)

-n=1000
![simulate Sierpinski Triangle n=1000](/assets/images/Sierpinski Triangle when n=1000.png)

-n=10000
![simulate Sierpinski Triangle n=10000](/assets/images/Sierpinski Triangle when n=10000.png)

Another way to create the Sierpinski's triangle is to start with a non-filled equilateral triangle. Then, draw a filled equilateral triangle where each vertex is located at the midpoint of the non-filled triangle. Create filled triangles in this fashion by using the midpoints of the non-filled equilateral triangles. This process will create Sierpinski's triangle.

<p align="center">
  <img
    src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Animated_construction_of_Sierpinski_Triangle.gif/800px-Animated_construction_of_Sierpinski_Triangle.gif"
    style="max-width:100%; height:auto;"
  />
</p>

The self-similarity of the triangle is also intruiging: 

<p align="center">
  <img
    src="https://upload.wikimedia.org/wikipedia/commons/6/6b/Sierpinski_zoom_2.gif"
    style="max-width:100%; height:auto;"
  />
</p>

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
# Demo of piraling Through the Collatz Conjecture
# Description: Plot each term of a Collatz sequence in polar coordinates, and show the result
# of a swirling spiral
# Author: Daniel Ge
# Date:   2025-04-26

import random
import matplotlib.pyplot as plt

def sierpinski_triangle(n):

  A = (0,0); B = (1,0); C = (0.5, 0.866)
  x, y = 0.3, 0.4  # starting point
  points = []
    
  for _ in range(n):
      vertex = random.choice([A, B, C])
      x = (x + vertex[0]) / 2
      y = (y + vertex[1]) / 2
      points.append((x,y))

  xs, ys = zip(*points)
  plt.scatter(xs, ys, s=0.1)
  plt.axis('off')
  plt.show()

n = 100
#n = 1000
#n = 10000
sierpinski_triangle(n)
```
