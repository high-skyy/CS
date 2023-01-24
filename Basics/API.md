# API

## What is API
-API(Application Programming interface)
애플리케이션 소프츠웨어를 빌드하고 통합하기 위한 정의 및 프로토콜 세트인 애플리케이션 프로그래밍 인터페이스
> 어떤 서버의 특정한 부분에 접속해서 그 안에 있는 데이터오 서비스를 이용할 수 있게 해주는 소프트웨어 도구

## 장점
- API를 사용하면 구현 방식을 알지 못하는 제품 또는 서비스와도 통신할 수 있으며 애플리케이션 개발을 간소화 하여 시간과 비용을 절약할 수 있다.
- API는 리소스에 대한 액세스 범위를 넓히는 동시에 보안과 제어를 유지할 수 있도록 한다. 액세스 권한을 어떻게, 누구에게 제공할 지 여부만 결정하면 됩니다.

## Rest API (Representational State Transfer)
네트워크를 통해서 컴퓨터들끼리 통신할 수 있게 해주는 아키텍처 스타일이다. 인터넷 식별자(URI)와 HTTP 프로토콜을 기반으로 한다. 데이터 포맷으로는 브라우저 간 호환성이 좋은 제이슨(Json)을 사용합니다.

REST API는 클라이언트와 서버 사이에서 통신할 수 있게 하고, 아키텍처를 만들 수 있게 해줍니다.
> 클라이언트는 다른 프로그램에게 서비스를 요청하는 프로그램, 서버는 그 요청에 대한 응답을 해주는 프로그램

REST는 웹에 최적화되어 있고, 데이터 포맷이 JSON이기 때문에 브라우저들 간에 호환성이 좋습니다.

### REST API 규칙
1. URI는 정보의 자원을 표현해야 한다.
2. 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE 등)으로 표현한다.

## SOAP API
SOAP(Simple Object Access Protocol)는 그 자체로 프로토콜이며, 보안이나 메시지 전송 등에 있어서 REST보다 더 많은 표준들이 정해져있기 때문에 조금 더 복잡하다.

보안 수준이 엄격하여 은행용 모바일 앱 등에서 선호가 된다.

### 차이점
![SOAP REST 차ㅣ](https://user-images.githubusercontent.com/105041834/188277928-f5fbac4b-2e9f-4a68-8e8e-bde5e5a85483.JPG)




## References
[Reference](https://www.redhat.com/ko/topics/api/what-are-application-programming-interfaces)
[Reference](https://blog.wishket.com/soap-api-vs-rest-api-%EB%91%90-%EB%B0%A9%EC%8B%9D%EC%9D%98-%EA%B0%80%EC%9E%A5-%ED%81%B0-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%80/#:~:text=%27SOAP%20REST%20%EC%B0%A8%EC%9D%B4%27%20%3A%20%ED%95%B5%EC%8B%AC,%EB%A5%BC%20%EC%9D%B4%EC%9A%A9%ED%95%B4%EC%84%9C%20%EC%A0%91%EA%B7%BC%ED%95%A9%EB%8B%88%EB%8B%A4.)
[Reference](http://www.terms.co.kr/clientserver.htm#:~:text=%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8%2F%EC%84%9C%EB%B2%84%EB%8A%94%20%EB%91%90%20%EA%B0%9C%EC%9D%98,%EC%9D%91%EB%8B%B5%EC%9D%84%20%ED%95%B4%EC%A3%BC%EB%8A%94%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8%EC%9D%B4%EB%8B%A4.)
[Reference](https://poiemaweb.com/js-rest-api#:~:text=%233.-,REST%20API%EC%9D%98%20%EA%B5%AC%EC%84%B1,%EC%9A%94%EC%B2%AD%EC%9D%84%20%EC%9D%B4%ED%95%B4%ED%95%A0%20%EC%88%98%20%EC%9E%88%EB%8B%A4.)
