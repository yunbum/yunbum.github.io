---
layout: post
read_time: true
show_date: true
title:  GPS/GNSS Test 
date:   2021-02-10 13:32:20 -0600
description: 다양한 제조사의 GPS 제품들을 테스트 하여 비교평가 중.
img: posts/20210210/GNSS_test.jpg
tags: [coding, python]
author: Ybbaek
github: amaynez/GameOfLife/
---
## 다양한 GPS/GNSS 모둘 비교테스트
I am lately trying to take on coding again. It had always been a part of my life since my early years when 

<img src="./assets/img/posts/20210210/300px-TRS-80_Color_Computer_3.jpg" alt="Tandy Color Computer TRS80 III"/><small>Tandy Color Computer TRS80 III</small>

<p>For one of my starter quick programming tasks, I&nbsp;decided to code Conway's Game of Life, a very simple cellular automata that basically plays itself.</p>

<ul><li>If a cell has less than 2 neighbors, meaning contiguous alive cells, the cell will die of loneliness</li><li>If a cell has more than 3 neighbors, it will die of overpopulation</li><li>If an empty block has exactly 3 contiguous alive neighbors, a new cell will be born in that spot</li><li>If an alive cell has 2 or 3 alive neighbors, it continues to live</li></ul>

<img src="./assets/img/posts/20210210/GameOfLife.gif" alt="Conway's rules for the Game of Life"/><small>Conway's rules for the Game of Life</small>

<p>In the end the algorithm ended up as follows:</p>

<ol><li>Iterate through all the alive cells and get all of their neighbors</li></ol>

```python
def get_neighbors(self, cell):
    neighbors = []

    for x in range(-1, 2, 1):
        for y in range(-1, 2, 1):
            if not (x == 0 and y == 0):
                if (0 &lt;= (cell[0] + x) &lt;= self.size_x) and (0 &lt;= (cell[1] + y) &lt;= self.size_y):
                    neighbors.append((cell[0] + x, cell[1] + y))
    return neighbors
```

<ol start="2"><li>Mark all the neighboring blocks as having +1 neighbor each time a particular cell is encountered. This way, for each neighboring alive cell the counter of the particular block will increase, and in the end it will contain the total number of live cells which are contiguous to it.</li></ol>

```python
for cell in alive_neighbors:
    if alive_neighbors[cell] &lt; 2 or alive_neighbors[cell] > 3:
        self.alive_cells.discard(cell)
    
    elif alive_neighbors[cell] == 3:
        self.alive_cells.add(cell)
```
<p>I&nbsp;found it very interesting to implement the Game of Life like this, it was quite a refreshing challenge and I am beginning to feel my coding skills ramping up again.</p>