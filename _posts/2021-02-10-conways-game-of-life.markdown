---
layout: post
read_time: true
show_date: true
title:  GPS/GNSS 모듈 비교평가 테스트 / GPS quality test 
date:   2021-02-10 13:32:20 -0600
description: 다양한 제조사의 GPS 제품들을 테스트 하여 비교평가 중.
img: posts/20210210/GNSS_test.jpg
tags: [coding, python]
author: Ybbaek
github: yunbum
---
## 다양한 GPS/GNSS 모둘 비교테스트
현재 다양한 종류의 GPS 모듈, 환경에 따른 차이, RTK mode 안정성, 가성비에 따른 효율, 이동중 특성 등의 다양한 성능을 평가하고 모바일 로봇에 반영하고 있습니다. 

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
<p>현재까지도 다양한 GPS/GNSS 모듈들을 테스트 하여 성능,안정성,편의성 등에 대한 비교평가도 지속적으로 진행 중입니다.</p>