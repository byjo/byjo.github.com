## nosql
#### concept
- 배경 
    + big data와 cloud computing이 등장하면서 기존 rdb 패러다임에 제약이 많이 생김
    + rdb는 시스템 확장시 scale up(기존 시스템의 성능을 높여서)
    + scale up으로는 진짜 큰 data(big data)를 다루기 힘들어
    + 기존 rdb 디자인을 버리자. 
- nosql
    + not Only SQL : query language로 sql을 사용하지 않음
    + 분산 환경 by scale out : partitioning(sharding), replication
    + flexible : 고정 스키마 없음, 조인 없음 

#### 장단점
- To scale for lots of users and lots of data
    + NoSQL tech. can offer more scalability than RDBs
    + Often lose some benefits of RDBs, e.g., database-wide transactions
- To work better with different data format, e.g., JSON
    + Avoiding object/relational mapping makes code easier to write
    + Limited BI tools; persistent data designed for a single appl. is harder to share
- To work with data in a more flexible way
    + NoSQL tech. don’t have fixed schemas
    + Fixed schemas help prevent errors

#### CAP Theorem
- consistency
- availability
- partitions
- 셋 중 최대 2개는 만족 시킬 수 있어 
- nosql은 partition을 하니(scale out), consistency나 availability 둘 중 하나 선택(주로 availability) 
- 