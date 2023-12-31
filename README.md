# GraphsFor9Class

## Что это такое?
Граф - это модель, состоящая из множетсва вершин и соеденяющих их рёбер.
Например графом можно назвать пещеру с тонелями в другие пещеры. Либо пример из реальной жизни - дороги, где перекрестки - это вершины, а сами дороги - рёбра.

Рёбра могут иметь вес, например в примере с дорогами - они могут быть загружены пробками.
Также графы могут быть ориентированными, в этом случае по одному ребру можно пройти только в одном направлении.

Последней характеристикой графа это то, что они могут быть связанными - между любой парой вершин есть минимум один путь, и не связанными - когда хотя бы между одной парой вершин путь отсутствует.

## Как обычно вводится данные о графе
Пускай этими данными будет двумерный массив состоящий из строк, которые состоят из вершины от которой исходит ребро, вершины к которой ведет это ребро и веса ребра.
Наша задача каким либо образом разместить эти данные, образовав из них граф.
```
2 3 1
1 3 4
1 2 3
```

## Двумерный массив ребер
Фактически мы оставим вводимые данные в таком виде, в котором получали.
```
  |0 |1 |2   первая строка и столбец - индексы
--|--|--|--
0 | 2| 3| 1
--|--|--|--
1 | 1| 3| 4
--|--|--|--
2 | 1| 2| 3
```

## Матрица смежности
Это все также двумерный массив, но теперь в качестве вершин будут выступать индексы массива, а в значениях будет лежать 1 - если есть связь и 0 - если нет. Вместо 1 можно хранить вес ребра.
```
  |0 |1 |2
--|--|--|--
0 | 0| 3| 4
--|--|--|--
1 | 3| 0| 1
--|--|--|--
2 | 4| 1| 0
```
*Реализация заполнения на python:*
```python
n = int(input())
adj = [[0]*n for _ in range(n)]
 
for it in range(n):
    r, c, w = map(int, input().split())
    adj[r-1][c-1] = adj[c-1][r-1] = w
 
print(adj)
```

## Список смежности
Представлен массивом, в котором хранятся смежные вершины для вершины соответствующей индексу. Минусом является то, что нельзя хранить взвешенные графы.
```
 0       2       3 
[[2, 3], [0, 3], [0, 2]]
```

## Обход в глубину (DFS - Depsh First Search)
Обходом (поиском) в глубину или эйлеровым обходом называется рекурсивный алгоритм обхода корневого дерева или графа, начинающий в корневой вершине (в случае графа может быть выбрана произвольная вершина) и рекурсивно обходящий весь граф, посещая каждую вершину ровно один раз.
```python
g = [[1, 2], [0, 2], [0, 1]]

visited = []

def dfs(v):
  visited[v] = true
  for el in g[v]:
    if !visited[el]:
      dfs(el)
```
