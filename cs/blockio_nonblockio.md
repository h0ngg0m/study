## Block I/O
I/O 작업을 요청한 프로세스/스레드는 요청이 완료될 때까지 블락됨.

## Block I/O 예시 - file read
t: thread / k: kernel
1. t: read 시스템콜 요청 (커널 모드로 전환)
2. k: read 시스템콜 처리
3. k: read 시스템콜 처리 완료 
4. k: t에게 I/O 제어권 반환 (유저 모드로 전환)
- 결과적으로 커널이 I/O 제어권을 가지고 작업을 처리하는 동안 프로세스/스레드는 블락됨.

## Block I/O 예시 - socket read, write
sa: socket A / sb: socket B
- 서로 연결된 두 소켓 sa, sb를 가정.
- 각 소켓은 send_buffer, recv_buffer를 가짐.

case1.
1. sa: sb의 데이터를 read 시스템 콜 요청
2. sa: sb의 데이터를 recv_buffer에 저장 (recv_buffer에 데이터가 없으면 데이터가 입력될 때까지 블락됨)

case2.
1. sb: sa에게 데이터를 넘겨주는 write 시스템 콜 요청
2. sb: 만약 sb의 send_buffer가 가득차서 데이터를 넘겨줄 수 없다면, send_buffer가 비워질 때까지 write 시스템 콜 요청을 블락시킨다.
 


## Non-Block I/O
I/O 작업을 요청한 프로세스/스레드는 요청이 완료되지 않아도 커널이 바로 return 처리하여 블락되지 않고 다른 작업을 수행할 수 있음.

## Non-Block I/O 예시 - file read
t: thread / k: kernel
1. t: read 시스템콜 요청 (커널 모드로 전환)
2. k: read 시스템콜과 동시에 t에게 I/O 제어권 반환 (return / 유저 모드로 전환)
3. t: 다른 작업을 수행할 수 있음 (동시에 k는 read 시스템콜 처리)
4. t: k에게 read 시스템콜 처리 완료 여부를 확인하고, 처리 완료되지 않았다면 다른 작업을 수행할 수 있음 (동시에 k는 read 시스템콜 처리)

## Non-Block I/O 예시 - socket read, write

case1.
1. sa: sb의 데이터를 read 시스템 콜 요청
2. sa: sb의 데이터를 recv_buffer에 저장 (recv_buffer에 데이터가 없으면 데이터가 입력될 때까지 블락되는 것이 아니라 바로 적절한 에러와 함께 return됨)

case2.
1. sb: sa에게 데이터를 넘겨주는 write 시스템 콜 요청
2. sb: 만약 sb의 send_buffer가 가득차서 데이터를 넘겨줄 수 없다면, send_buffer가 비워질 때까지 write 시스템 콜 요청을 블락시키는 것이 아니라 바로 적절한 에러와 함께 return됨.

## Non-Block I/O 이슈
I/O 작업의 완료 여부를 어떻게 확인할 것인가?

### Polling
I/O 작업의 완료 여부를 주기적으로 확인
- 완료된 시간과 완료를 확인한 시간 사이의 갭으로 인해 처리 속도가 느려질 수 있다.
- 완료됐는지 반복저으로 확인하는 것은 CPU 리소스 낭비.

### I/O Multiplexing
관심있는 I/O 작업들을 동시에 모니터링하고 그중에 완료된 I/O 작업들을 한 번에 알려줌

### Callback / Signal

## Non-Block I/O 핵심
Non-Block I/O를 통해 I/O 요청 완료 전에도 다른 일을 할 수 있다는 것.