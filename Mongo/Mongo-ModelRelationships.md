# Mongo Model Relationships

- One-to-One Relationships with Embedded Documents

  - Embedded Document Pattern
    - Document 안에 embedded documents 를 저장하여 one-to-one 관계를 형성하는 방식.
      - 단점: 이렇게 지속되면, 한 document의 사이즈가 커지게 되고 서버가 필요하지 않은 데이터들도 같이 불러오게 되면서 read operation 을 느려지게 할 수 있다.
  - Subset Pattern
    - 메인과 서브를 각각 Collection 으로 빼고, 메인이 되는 Collection 의 id 값을 서브의 Collection 에 reference 할 수있게 field를 추가한다.
      - 장점
        - 대부분의 요청에서 적은 데이터를 읽을수 있어서 read performace 증가
        - 더 자주 접근하는 데이터를 가진 smaller documents 를 사용하는것은 working set 의 전체 사이즈를 감소 시키고 그로 인해 read performance 가 증가되고, 메모리 가용성이 높아짐.
      - 단점
        - 데이터를 너무 많은 Collections 으로 잘못 나누게 되면 your application will often need to make multiple trips to the database (정확하게 이해를 못함)
        - 그리고 필요한 데이터를 위해 JOIN operations ($lookup, $graphqlLookup 등등)에 기대야 할 수밖에 없어진다.
        - 데이터를 많은 작은 Collections 으로 나누는건 필요한 database maintenance (디비 유지)가 증가할수 있고, 그로 인해, 데이터가 어떤 Collection 에 저장되어 있는지 track 하기가 어려워 질 수 있다.

- One-to-Many Relationships with Embedded Documents
  - Embedded Document Pattern
    - Document 안의 array 에 embedded documents 를 저장하여 one-to-many 관계를 형성하는 방식.
      - 단점: 이렇게 지속되면, 한 document의 사이즈가 굉장히 커지게 되고 그로인해 working set 의 전체 사이즈가 늘어나면 read performance 에 영향.
  - Subset Pattern
    - Many 에 해당 되는 부분을 Collection 으로 빼고, One 에는 가장 자주 사용되고 가장 먼저 불러와야 할 documents를 Embedded Documents 로 저장. (ex: Top10, 최근 10개 등등)
      - 장점: working set 의 전체 사이즈를 감소시킴으로써 read performace 증가
      - 단점: 데이터 중복이 생김. One 의 Embedded Documents 들과 Many 의 Documents 의 데이터 일관성을 유지하기위해, 각 collection 들을 업데이트 하는 로직을 Application 단에서 해야함. 즉 최소 두번의 업데이트가 필요.
- One-to-Many Relationships with Document References
  - Pattern
    - Many 에 해당 되는 Collection 의 Document 에 One 의 id 값을 reference 로 추가한다.
