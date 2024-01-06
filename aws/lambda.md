# AWS Lambda

## 서버리스(Serverless) 특징
- 인프라를 프로비저닝 하거나 관리할 필요가 없다.
- 사용량에 따른 자동 스케일링이 가능하다.
- 사용한 만큼만 비용을 지불한다.
- 높은 가용성과 안정성을 보장한다.

## AWS Lambda 특징
- 서버리스 어플리케이션을 만들 수 있게 해주는 대표적인 서비스
- Function-as-a-Service(FaaS) 서비스
- Run code without provisioning or managing servers
- Pay only for the compute time you consume
- Automatically runs your code with high availability
- Scale with usage

## AWS Lambda 기능
- Load Balancing
- Auto Scaling
- Handling failures
- Security isolation
- OS management
- and many other things for you

## Lambda 함수를 작성할 수 있는 언어
- Node.js
- Java
- Python
- 등등.. 혹은 직접 Runtime API를 사용하여 언어를 지원할 수 있다.

## Lambda 함수를 실행하는 방법
- Event source로부터 실행
  - 데이터의 변화를 감지하여 실행
  - 엔드포인트로 요청이 들어왔을 때
  - 리소스의 상태가 변화됐을 때
  - 등등...
- 실행되면 여타 다른 서비스와 연동하여 추가적인 작업을 수행할 수 있다.

## Anatomy of a Lambda function
- Handler() function: Function to be executed upon invocation
- Event object: Data send during lambda function invocation
- Context object: Methods available to interact with runtime information (e.g. request ID, log group, more)
```python
import json

def lambda_handler(event, context):
    # TODO implement
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from Lambda!')
    }
```
- Lambda are run inside execution environments. We try to reuse these
- Concurrent invocations are run in separate execution environments
- Declaration outside handler() will only run once
  - 리소스를 초기화(DB 커넥션 등)의 로직은 handler() 밖에서 실행하게 해서 리소스를 재사용할 수 있게 해야한다.(그래야 빠르다)
- Connections made outside handler() will be reused

## Lambda Execution Models
- Synchronous
  - API Gateway 등등 
- Asynchronous
  - S3, SNS, CloudWatch Events 등등
- Stream-based
  - Kinesis, DynamoDB 

## Lambda의 단점, 한계
- 리소스 제한: 람다는 메모리(최대 10GB), 처리시간(최대 15분)에 제한이 있다.
- Stateless: 람다는 함수가 호출되면 새로운 컨테이너를 띄우는 방식이기 때문에 별도의 상태를 저장하지 않는다. 이는 람다 함수가 이벤트에 의해 트리거 도리 때마다 완전히 새로운 환경에서 호출되는 것이고 그렇기 때문에
db connection pool 등을 사용할 수 없다.
- Cold start: 람다는 리소스를 효율적으로 사용하기 위해서 오랫동안 사용하지 않고 있을 경우 컴퓨팅 파워를 꺼둔다. 
그래서 다시 사용하려고 하면 람다 컨테이너를 띄우기 위해 서버가 켜지고 실행환경을 구성하기 위해 약간의 딜레이가 생긴다.

## Cold start 해결 방법
- 람다 함수를 주기적으로 실행시켜서 컨테이너를 미리 띄워둔다. (추가적인 비용이 듬)
- 람다의 메모리를 늘린다. 메모리가 늘어나면 컴퓨팅 파워가 늘어나기 때문에 컨테이너를 띄우는 시간이 줄어든다. (추가적인 비용이 듬)
- 프로비저닝된 동시성 활성화: 람다 함수를 실행할 때 미리 컨테이너를 띄워두고 사용한다. 람다 함수가 실행되면 미리 띄워둔 컨테이너에서 실행된다. (추가적인 비용이 듬)