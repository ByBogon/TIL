# 연결 리스트 (Linked List)

### 추상적 자료구조 (Abstract Data Structures)

> - 자료구조의 내부구현은 숨겨두고 밖에서 보이는 것들 두가지만 제공하는것
> - Data

    - 예: 정수, 문자열, 레코드, ....

> - A set of operations (연산들)

    - 삽입, 삭제, 순회,....
    - 정렬, 탐색, ....

### 기본적 연결 리스트

- 선형적으로 이루어진 데이터

![..src/images/linked_list1.png](..src/images/linked_list1.png)

- 각 노드안에 데이터와 다음 노드가 어떤건지 가리키는 링크도 담고있음

![..src/images/linked_list2.png](..src/images/linked_list2.png)

- 노드 내의 데이터는 다른구조로 이루어질 수 있음
  - 예: 문자열, 레코드, 또 다른 연결 리스트 등등
- 리스트의 맨 앞은 알아야함, 맨 끝도 알면 좋은점이 나중에 리스트의 맨 끝에 데이터를 추가할때 끝 뒤에 바로 붙일수 있어서 유리함, 맨끝을 모르면 앞에서부터 찾아가야함.

![..src/images/linked_list3.png](..src/images/linked_list3.png)

- Head, Tail, node 갯수 을 일반적으로 세팅하고, 이 연결 리스트에 사용될 연산들을 다 저장해 놓으면 이게 연결리스트의 추상적 자료구조가 됨.

### 자료구조 정의

- 최초에 Node 가 생성될때 다음 노드를 가리키는 링크가 없으므로 None 으로 선언

![..src/images/linked_list4.png](..src/images/linked_list4.png)

- 연결 리스트

![..src/images/linked_list5.png](..src/images/linked_list5.png)

- 추상적 자료구조에 사용될 연산 정의

  1. 특정원소 참조(k 번째)
  2. 리스트 순회
  3. 길이 얻어내기
  4. 특정 위치의 원소 삽입
  5. 특정 위치의 원소 삭제
  6. 두 리스트 합치기

- 특정 원소 참조

  - 0은 나중을 위해 시작을 1부터 하기로 정함
    ![..src/images/linked_list6.png](..src/images/linked_list6.png)
    ![..src/images/linked_list7.png](..src/images/linked_list7.png)

- 배열과 비교한 연결 리스트
  ![..src/images/linked_list8.png](..src/images/linked_list8.png)

- 연결리스트가 메모리에 저장될때 임의의 위치에 저장 될 수 있다는건, 각 노드를 메모리에 각각 저장할수 있어서, 메모리 공간적 최적화가 가능함 (내부 단편화 )
  - 내부 단편화 - 메모리를 할당 할때 프로세스가 필요한 양 보다 더 큰 메모리가 할당되어서 프로세스에서 사용하는 메모리 공간이 낭비되는 상황
  - 외부 단편화
    - 메모리가 할당되고 해제되는 작업이 반복될 때, 작은 메모리가 중간중간 존재함. 이때, 중간중간에 생긴 사용하지 않는 메모리가 많이 존재하게되어, 총 메모리 공간은 충분하지만, 실제로는 할당할 수 없는 상황
    - 연습문제 - 리스트 순회
      - 마지막 노드의 next 가 None 인가 확인하기. Head 에서부터 다음다음을 찾아나가게 구현
