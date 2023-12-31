# OS (Operating System), 운영체제
- 대표적인 예: Windows, Linux, Mac OS
- CPU의 성능이 낮고 메모리 크기도 작은 시스템에 내장하도록 만든 OS를 `임베디드 운영체제` 또는 `임베디드 시스템`이라고 한다.
(ex. 스마트폰, 스마트TV, 자동차, 가전제품 등)
  - 임베디드 운영체제가 있는 기기와 없는 기기의 차이: 임베디드 운영체제가 있는 기기는 응용 프로그램 설치 등을 하면서 기능을 계속 
  향상시킬 수 있지만 임베디드 운영체제가 없는 기기는 기기를 구매한 후에는 기능을 향상시킬 수 없다.
- 초기의 컴퓨터는 정해진 계산만 수행했기 때문에 특별한 사용 규칙이 필요 없었으나 현재의 컴퓨터는 여러 사용자가 동시에 사용하고, 
여러 프로그램이 동시에 실행되기 때문에 사용 규칙이 필요하다. 그 사용 규칙을 정의하고, 컴퓨터 하드웨어와 응용 프로그램을 관리하는 소프트웨어가 운영체제이다.
- 운영체제를 소프트웨어와 하드웨어의 결합 형태인 `펌웨어`라고도 한다.

## OS - 역할 및 목표
- 자원 관리: 컴퓨터로 문서를 작성하거나 음악을 듣고, 인터넷 서핑을 한다. 이때 키보드, 네트워크카드, 스피커, 모니터 등의 하드웨어를 사용하는데
운영체제는 이러한 자원을 응용 프로그램에게 적당한 순서로 분배하고 회수한다.
  - 목표 - 효율성: 효율적으로 자원을 관리하는 것 (ex. 응용 프로그램이 자원을 사용하는 시간을 최대한 줄이는 것, 운영체제의 크기를 최소화하는 것, 운영체제가 사용하는 코드의 최적화 등)
- 자원 보호: 악의적인 사용자나 미숙한 사용자로부터 자원을 보호하는 것도 운영체제의 역할 중 하나다. 
  - 목표 - 안정성: 운영체제는 하드웨어와, 응용 프로그램을 관리하는 소프트웨어이기 때문에 안정성이 중요하다. 
- 하드웨어 인터페이스 제공: 운영체제는 응용 프로그램이 일관된 방법으로 하드웨어를 사용할 수 있도록 하드웨어 인터페이스를 제공한다.
  - 목표 - 확장성: 운영체제는 하드웨어의 종류에 상관없이 응용 프로그램이 일관된 방법으로 하드웨어를 사용할 수 있도록 하드웨어 인터페이스를 제공한다.
- 사용자 인터페이스(GUI) 제공: 사용자가 운영체제를 편리하게 사용할 수 있도록 사용자 인터페이스를 제공한다. 
  - 목표 - 편리성: 사용자가 운영체제, 컴퓨터를 편리하게 사용할 수 있도록 사용자 인터페이스, 기능 등을 제공한다.

## 시분할 시스템 (다중 작업) - 1960년대 후반
- 시분할 시스템은 여러 응용 프로그램이 동시에 실행되는 것처럼 보이도록 하는 시스템이다. 예를들어 A, B, C 3개의 응용 프로그램이 있고, 각 0.1초씩 실행되고 있다면
0.1초마다 A, B, C가 번갈아가면서 실행되는 것처럼 보인다. 
  - 이때 잘게 나뉜 시간 한 조각을 0.1초를 `타임 슬라이스` 혹은 `타임 퀀텀`이라고 한다.
  - 시분할 시스템의 단점은 여러 작업을 동시에 처리하기 위한 추가 작업이 필요하고, 시스템 내의 많은 양의 작업이 공존할 경우, 중요한 작업이 일정 시간 안에 끝나는 것을 보장하지 못한다는 것이다.
  이와 반대로 일정 시간 안에 작업이 처리되도록 보장하는 `실시간 시스템`을 사용하기도 한다.
  - 시분할 시스템에서 동시에 실행되는 작업의 개수를 멀티프로그래밍 수준 또는 정도라고 한다. 일괄 작업 시스템은 멀티프로그래밍 수준이 1이고, 3개의 작업을 시분할 시스템으로 실행하면 멀티프로그래밍 수준은 3이다.\

## 분산 시스템 - 1970년대 후반
- 개인용 컴퓨터가 많이 보급이 되던 시대, 값이 싸고 크키가 작은 컴퓨터들을 하나로 묶어 대형 컴퓨터에 버금가는 시스템을 만들게 되는데 이를 `분산 시스템`이라고 부른다.

## 클라이언트-서버 시스템 - 1990년대 ~ 현재
- 분산 시스템은 시스템에 참가하는 모든 컴퓨터가 동일한 지위이기 때문에 컴퓨터가 고장 나거나 추가되면 작업을 분배하고 결과를 모으기가 쉽지 않다.
클라이언트/서버 시스템은 이러한 문제점을 해결하는 기술로, 모든 컴퓨터의 컴퓨터의 지위가 동일한 분산 시스템과 달리 작업을 요청하는 `클라이언트`와 거기에 응답하여 요청받은
작업을 처리하는 `서버`의 이중구조로 나뉜다.
  - 클라이언트/서버 시스템의 단점 중 하나는 `서버 과부하`를 뽑을 수 있다. 모든 요청이 서버로 집중되기 때문에 과부하를 주의해야 한다.

## P2P 시스템 - 2000년대 초반 ~ 현재
- 서버의 부하를 줄일 수 있는 시스템으로 peer는 말단 노드, 즉 사용자의 컴퓨터를 가리키며 P2P는 서버를 거치지 않고 사용자와 사용자를 직접 연결한다는 의미이다.
  - 서버가 있는 P2P 시스템: 메신저는 사용자 인증과 출석 정보, 과거 데이터 보관 등을 위해 서버가 있다.
  - 서버가 없는 P2P 시스템: 비트코인, 블록체인 등은 따로 서버가 없다.

## 그리드 컴퓨팅 - 2000년대 초반 ~ 현재
- 서로 다른 기종의 컴퓨터들을 묶어 대용량의 컴퓨터 풀을 구성하고 해당 자원을 필요한 만큼 구매하여 사용하는 환경을 그리드 컴퓨팅이라고 부른다.

## 클라우드 컴퓨팅
- SaaS와 그리드 컴퓨팅을 합쳐놓은 형태다. 언제 어디서나 응용 프로그램과 데이터를 자유롭게 사용할 수 있다.