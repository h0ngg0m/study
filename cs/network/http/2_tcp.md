## TCP 커넥션 (TCP/IP)
- HTTP는 어플리케이션 계층 프로토콜이다. HTTP는 네트워크 통신의 핵심적인 세부사항에 대해서 신경 쓰지 않는다. 대신 
대중적이고 신뢰성 있는 인터넷 전송 프로토콜인 TCP/IP에게 맡긴다.
- TCP가 제공하는 것:
  - 오류 없는 데이터 전송
  - 순서에 맞는 전달(데이터는 언제나 보낸 순서대로 도착한다)
  - 조각나지 않는 데이터 스트림(언제든 어떤 크기로든 보낼 수 있다)

## 접속, IP 주소, 포트 번호
- HTTP 클라이언트가 서버에 메시지를 전송할 수 있게 되기 전에, IP 주소와 포트번호를 사용해 클라이언트와 서버 사이에 TCP/IP 커넥션을 맺어야 한다.
- HTTP 서버의 IP 주소와 포트번호를 알아내는 방법:
  - URL을 이용하면 된다. URL에는 서버의 IP 주소와 포트번호가 포함되어 있다. 
  - ex: `http://www.joes-hardware.com:80/index.html`
    - `www.joes-hardware.com`은 서버의 인터넷 주소를 나타낸다.
    - `80`은 서버의 포트번호를 나타낸다. (만약 생략되면, 기본 포트번호인 80이 사용된다, 80은 HTTP 서버의 표준 포트번호이다)
- 웹 브라우저가 서버의 HTML 리소스를 사용자에게 보여주는 순서
  - 웹브라우저는 서버의 URL에서 호스트명을 추출한다.
  - 웹브라우저는 서버의 호스트명을 IP 주소로 변환한다.
  - 웹브라우저는 URL에서 포트번호(있다면)를 추출한다.
  - 웹브라우저는 서버와 TCP 커넥션을 맺는다.
  - 웹브라우저는 서버에 HTTP 요청 메시지를 보낸다.
  - 서버는 웹브라우저에 HTTP 응답 메시지를 보낸다.
  - 커넥션이 닫히면, 웹브라우저는 HTML 문서를 보여준다.