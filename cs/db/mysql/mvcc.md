# MVCC (Multi Version Concurrency Control)
- MVCC의 목적: 잠금을 사용하지 않는 일관된 읽기를 제공
  - InnoDB는 언두 로그를 이용해 이 기능을 구현한다.
- 멀티 버전이라 함은 하나의 레코드에 대해 여러 개의 버전이 동시에 관리된다는 의미다.