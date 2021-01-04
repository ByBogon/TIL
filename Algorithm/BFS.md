# BFS (너비우선탐색, Breadth First Search)

- 프로그래밍에 자주 사용되는 자료구조 중 하나인 그래프를 탐색하는 알고리즘 중 하나 (DFS, BFS)
- 그래프는 정점과 간선으로 이루어져 있는데 간선을 통해서 모든 정점을 방문하는 것을 "탐색한다" 고 한다.

너비우선탐색이란, 트리 혹은 그래프의 루트 노드에서 시작해서 인접한 모든 정점들을 우선 탐색하는 방법이다.

- 시작 정점으로부터 가까운 정점을 먼저 방문하고 멀리 떨어져 있는 정점을 나중에 순회하는 방법
- 즉, 깊게 탐색하기 전에 넓게 탐색하는 것이다.
  > 깊게는 DFS (Depth First Search), 깊이 우선 탐색
- 사용하는 경우: 두 노드 사이의 최단 경로 혹은 임의의 경로를 찾고 싶을 때
- 구현에는 주로 큐 자료구조를 사용

특징

- 직관적이지 않은 면이 있다
  > BFS는 시작 노드에서 시작해서 거리에 따라 단계별로 탐색한다고 볼 수 있다.
- BFS는 재귀적으로 동작하지 않는다.
- 그래프 탐색의 경우 어떤 노드를 방문했었는지를 반드시 검사해야한다
  > 아니면, 무한루프에 빠질 수 있다.
- BFS는 방문한 노드들을 차례로 저장한 후 꺼낼 수 있는 자료구조인 큐를 사용한다
  > FIFO 원칙으로 탐색.

> 일반적으로 큐를 이용해서 반복적 형태로 구현하는 것이 가장 잘 동작