###1. connect() vs createConnection()
`connect()`는 `poolSize` 옵션에 설정되어 있는 값만큼 소켓/커넥션을 가지는 단일 풀을 생성한다. 그래서 여러 커넥션을 가지는건 가능하나 하나의 풀 안에 존재한다.
그러나 `createConnection()`은 여러 커넥션풀을 생성한다. 그래서 여러 DB에 커넥션을 연결해야 할 때 쓰일 수 있다.

간단한 프로젝트 일 때에는 `connect()` 만으로 충분하지만, slave/replication 같이 여러 DB를 구축해야 할 때는 `createConnection()` 이 필수이다

여기서 생기는 차이점이, `connnect()`는 connection object를 리턴하여서 `mongoose.model(...)`로 model에 접근이 가능한데, `createConnection()`은 그렇지 않아 코드상에서 db object 를 확실하게 `db.model(...)`로 접근해야한다.

하나 주의해야 할 점은, `createConnection()` 과 `mongoose.model(...)` 의 조합에서 에러가 나지 않고 계속 hang 되어 있는 버그가 있어서 주의하여야한다.

Link: [참조](https://stackoverflow.com/questions/22786374/queries-hang-when-using-mongoose-createconnection-vs-mongoose-connect/22838614#22838614)
