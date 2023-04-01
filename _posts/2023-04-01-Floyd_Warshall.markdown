---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: Floyd_Warshall
title: Floyd_Warshall

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
# author: Mr. Green's Workshop
# multiple category is not supported
category: 코딩테스트
# multiple tag entries are possible
tags: [백준, 그래프, Floyd_Warshall]
# thumbnail image for post
img: ""
# disable comments on this page
#comments_disable: true

# publish date
# date: "`r format(Sys.Date())`"  => 오류
date: 2023-04-01 21:00:00 +0900

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-02-10 08:11:06 +0900
# check the meta_common_description in _data/owner/[language].yml
#meta_description: ""

# optional
# please use the "image_viewer_on" below to enable image viewer for individual pages or posts (_posts/ or [language]/_posts folders).
# image viewer can be enabled or disabled for all posts using the "image_viewer_posts: true" setting in _data/conf/main.yml.
#image_viewer_on: true
# please use the "image_lazy_loader_on" below to enable image lazy loader for individual pages or posts (_posts/ or [language]/_posts folders).
# image lazy loader can be enabled or disabled for all posts using the "image_lazy_loader_posts: true" setting in _data/conf/main.yml.
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
#published: false
---

<!-- outline-start -->

Floyd_Warshall : 백준 11404번

<!-- outline-end -->

# Floyd_Warshall
n개의 정점과 m개의 방향이 있는 edge가 있을 때, 각 정점 i에서 j로의 최단 거리를 모두 구하는 문제이다.

i에서 j로 가는 비용을 n*n 배열로 나타내고, i에서 j로 바로 가는 경우와 i에서 k를 거쳐 j로 가는 비용 중 더 작은 것으로 갱신해주는 것을 n번 반복하면 된다.

시간복잡도는 O(n^3)이 된다.

# 백준 11404 플로이드
## 문제
n(2 ≤ n ≤ 100)개의 도시가 있다. 그리고 한 도시에서 출발하여 다른 도시에 도착하는 m(1 ≤ m ≤ 100,000)개의 버스가 있다. 각 버스는 한 번 사용할 때 필요한 비용이 있다. 모든 도시의 쌍 (A, B)에 대해서 도시 A에서 B로 가는데 필요한 비용의 최솟값을 구하는 프로그램을 작성하시오.
## 입력
첫째 줄에 도시의 개수 n이 주어지고 둘째 줄에는 버스의 개수 m이 주어진다. 그리고 셋째 줄부터 m+2줄까지 다음과 같은 버스의 정보가 주어진다. 먼저 처음에는 그 버스의 출발 도시의 번호가 주어진다. 버스의 정보는 버스의 시작 도시 a, 도착 도시 b, 한 번 타는데 필요한 비용 c로 이루어져 있다. 시작 도시와 도착 도시가 같은 경우는 없다. 비용은 100,000보다 작거나 같은 자연수이다. 시작 도시와 도착 도시를 연결하는 노선은 하나가 아닐 수 있다.
## 출력
n개의 줄을 출력해야 한다. i번째 줄에 출력하는 j번째 숫자는 도시 i에서 j로 가는데 필요한 최소 비용이다. 만약, i에서 j로 갈 수 없는 경우에는 그 자리에 0을 출력한다.
## 예제입력1
```
5
14
1 2 2
1 3 3
1 4 1
1 5 10
2 4 2
3 4 1
3 5 1
4 5 3
3 5 10
3 1 8
1 4 2
5 1 7
3 4 2
5 2 4
```
## 예제출력1
```
0 2 3 1 4
12 0 15 2 5
8 5 0 1 1
10 7 13 0 3
7 4 10 6 0
```

이 문제를 보면 `시작 도시와 도착 도시를 연결하는 노선은 하나가 아닐 수 있다.`라는 문장이 있기 때문에 예제입력1의 경우 1에서 4로 가는 경우 비용이 1인 것도 있고 2인 것도 있기 때문에 min함수를 이용해서 가장 작은 비용의 경로만 생각하면 다음과 같이 된다. 당장 도달할 수 없는 곳은 비용을 inf라고 설정하였다. 배열을 알아보기 쉽게 하기 위해 다음과 같이 표기하였다.
```
  0   2   3   1  10
inf   0 inf   2 inf
  8 inf   0   1   1
inf inf inf   0   3
  7   4 inf inf   0
```
이 때, 1에서 4를 거쳐 5를 가는 경우를 생각해보자. `1에서 5로 이동하는 비용` = 10이다. 하지만 `1에서 4로 가는 비용` + `4에서 5로 가는 비용` = 1 + 3 = 4이다. 10보다 4가 더 작으므로 `1에서 5로 가는 비용`을 4로 갱신하면 다음과 같이 된다.
```
  0   2   3   1   4
inf   0 inf   2 inf
  8 inf   0   1   1
inf inf inf   0   3
  7   4 inf inf   0
```
이 때, 2에서 4를 거쳐 5를 가는 경우를 생각해보자. `2에서 5로 이동하는 비용` = inf이다. 하지만 `2에서 4로 가는 비용` + `4에서 5로 가는 비용` = 2 + 3 = 5이다. inf보다 7이 더 작으므로 `2에서 5로 가는 비용`을 7로 갱신하면 다음과 같이 된다.
```
  0   2   3   1   4
inf   0 inf   2   5
  8 inf   0   1   1
inf inf inf   0   3
  7   4 inf inf   0
```
자기자신에서 출발하여 자기자신으로 가는 경우를 제외하고, i에서 j로 도착하는 경로와, i에서 k를 거쳐 j로 도착하는 경우에 대해 더 작은 비용으로 갱신을 해주면 된다. 모든 i, j, k에 대해서 계산을 해주어야한다. 중요한 점은 k에 대해서 가장 크게 반복문을 돌려주어야한다. k를 거치는 경로 (i, j)에 대해 계산을 해주어야하기 때문이다.
```python
for k in range(n):              # 거치는 도시
    for i in range(n):          # 출발 도시
        for j in range(n):      # 도착 도시
            if(city[i][k]+city[k][j] < city[i][j]):
                city[i][j] = city[i][k]+city[k][j]
```
최종 출력은 다음과 같이 나오게 된다.
```
0 2 3 1 4
12 0 15 2 5
8 5 0 1 1
10 7 13 0 3
7 4 10 6 0
```

이 때 주의해야할 사항은, 아예 도달하지 못하는 곳이 존재하게 되면 inf로 남아있을 수 있기 때문에 마지막에 inf를 0으로 바꿔서 도달하지 못하는 곳을 표현해주면된다.

## 전체코드
```python
import sys
n = int(sys.stdin.readline())
m = int(sys.stdin.readline())
inf = 10000001

city = [[inf for _ in range(n)]for _ in range(n)]  # (i, j) 비용 inf로 설정
for i in range(n):              # (i, i) 비용 0으로 설정
    city[i][i] = 0

for _ in range(m):              # 입력 값 채우기
    x, y, v = map(int, sys.stdin.readline().split())
    city[x-1][y-1] = min(v, city[x-1][y-1])  # 중복 경로는 적은 비용으로 설정


for k in range(n):              # 거치는 도시
    for i in range(n):          # 출발 도시
        for j in range(n):      # 도착 도시
            if(city[i][k]+city[k][j] < city[i][j]):
                city[i][j] = city[i][k]+city[k][j]

for i in city:                  # inf값을 갖고 있다면 0으로 변환한 후 출력
    for j in i:
        if(j==inf):
            print(0, end=" ")
        else:
            print(j, end=" ")
    print()
```