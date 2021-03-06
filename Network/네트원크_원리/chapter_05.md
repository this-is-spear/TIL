# 서버측의 LAN에는 무엇이 있는가?

1. 웹 서버의 설치 장소
    - 요약
        - 사내의 LAN에 서버를 설치하고 인터넷에서 직접 액세스하는 경우
            
            이전에는 이런 형태가 많았지만 IP 주소 부족으로 인해 주류에서 밀려났다. 그리고 서버가 노출 상태에 있어 보안상의 문제가 있다.
            
        - **방화벽을 두고 액세스 하는 경우**
            
            방화벽이 관문 역할을 해 특정 서버에서 동작하는 특정 애플리케이션에 액세스하는 패킷만 통과시키고 그 외 패킷을 차단하는 역할을 한다. 
            
        - 데이터센터에 웹 서버를 설치하는 경우
            
            프로바이더 등이 운영하는 데이터센터라는 시설에 서버를 가지고 들어가 설치하거나 프로바이더가 소유하는 서버를 빌려쓰는 형태로 운영하는 경우도 있다.
            
        - 웹 서버가 데이터센터에 설치된 경우에는 인터넷 중심 부분에서 데이터 센터로 패킷이 흘러가고 서버 머신에 도착한다. 데이터센터에 방화벽 등이 설치되었으면 점검을 받고 나서 서버에 도착한다.
    - 내용
        
        - [웹 서버의 설치 장소](https://www.notion.so/4d25b1c37fde401a97c764739432554c)
        
2. 방화벽의 원리와 동작
    - 요약
        - 방화벽의 기본이 되는 개념은  특정 서버와 해당 서버 안의 특정 애플리케이션에 액세스하는 패킷만 통과시키고 그 외 패킷을 차단한다.
        - 어느 방법으로도 방화벽의 목적을 수행할 수 있지만, 성능, 가격, 사용 편의성 등의 이유로 지금은 패킷 필터링형이 가장 많이 보급되었다.
        - 패킷의 헤더에는 통신 동작을 제어하는 제어 정보가 들어있어서 제어 정보를 조사해 패킷 필터링을 진행할 수 있다.
        - 패킷 필터링 조건은 설정할 때는 먼저 패킷의 흐름에 착안한다. 그리고 수신처 IP 주소와 송신처 IP 주소에 따라 시점과 종점을 판단한다.
        - 인터넷과 웹 서버 사이 흐르는 패킷은 전부 통과하면 위험한 상태가 된다. 그래서 필요한 애플리케이션 외으 애플리케이션 패킷을 전부 차단하는 쪽이 좋다. 이와 같이 애플리케이션을 한정할 때는 TCP 헤더나 UDP 헤더에 기록되어 있는 포트 번호를 조건으로 추가한다.
    - 내용
        
       - [방화벽의 원리와 동작](https://www.notion.so/56c553681b974148a2e78e0bbf5daa46)
        
3. 복수 서버에 리퀘스트를 분배한 서버의 부하 분산
    - 요약
        - 복수의 서버를 사용하여 처리를 분담하는 방법으로 서버 한 대당 처리량을 줄이는 것이 효과적이다. 이러한 처리 방법을 통틀어 분산 처리라 한다.
        - 가장 간단한 방법은 단순히 여러 대 웹 서버를 설치하고 한 대가 담당하는 사용자 수를 줄이는 방법이다. 구체적인 방법 중 하나는 DNS이다.
        - 로드 밸런서는 웹 서버와 정기적으로 정보를 교환해 CPU나 메모리 사용률 등을 수집하고 이 내용을 바탕으로 부하를 판단해 분산시킨다.
        - 프록시를 사용하면 리퀘스트의 송신처 IP 주소가 프록시의 IP 주소로 되어 실제 리퀘스트를 보낸 클라이언트가 누군지 모르게 된다.
    - 내용
        
        - [복수 서버에 리퀘스트를 분배한 서버의 부하 분산](https://www.notion.so/6fbd222654a04eec999ed898aaa99433)
        
4. 캐시 서버를 이용한 서버의 부하 분산
    - 요약
        - 여러 대의 웹 서버를 설치하는 밥법이 있고, 데이터베이스 서버와 웹 서버를 나누듯이 역할에 따라 서버를 나누는 방법이 있다. 이러한 역할별 분산 처리 방법 중 하나가 캐시 서버를 이용하는 방법이다.
        - 캐시 서버에서 이용하는 프록시 구조는 원래 클라이언트측에 두는 방법에서 시작되었고, 포워드 프록시라 한다.
        - 프록시를 사용하면 브라우저에 설정이 필요한 점은 번거로움과 장애의 원인뿐만 아니라 인터넷에 공개하는 웹 서버는 누가 액세스하는지 알 수 없고, 브라우저에 프록시를 설정할 수 없기 떄문에 웹 서버 앞에 프록시를 두는 방법을 선택하지 않는다.
        - 프록시의 대안으로 리버스 프록시가 있다.
        - 트랜스페어런트 프록시를 사용하면 사용자가 프록시의 존재를 알아차릴 필요가 없다.
    - 내용
        
        - [캐시 서버를 이용한 서버의 부하 분산](https://www.notion.so/8bf323bddac34b889de1c0723b4961cd)
        
5. 콘텐츠 배포 서비스
    - 요약
        - 캐시 서버는 서버측에 두는 경우와 클라리언트측에 두는 경우가 이용 효과면에서 차이가 난다.
        - 캐시 서버는 높는 장소에 따라 장점과 단점이 있지만 양쪽의 좋은 점만 취한 방법도 있다. 프로바이더와 계약하여 웹 서버 운영자가 제어할 수 있는 캐시 서버를 클라이언트측의 프로바이더에 두는 방법이고 이 방법이 콘텐츠 배포 서비스이다.
        - 캐시 서버를 설치하고 웹 서버 운영자에게 대출하는 서비스를 제공하는 사업자가 등장했는데, 이 종류의 서비스를 콘텐츠 배포 서비스라 한다.
        - 캐시 서버를 효율적으로 갱신하려면 서버가 갱신할 경우 즉시 캐시 서버에 반영해야 한다. 그리고 캐시 서버를 동적으로 변하는 데이터는 캐시 서버에 데이터를 저장하면 안된다. 페이지에서 내용이 달라지는 부분과 달라지지 않는 부분을 구분하고 변하지 않는 부분만 캐시에 저장해야 한다.
    - 내용
        
        - [콘텐츠 배포 서비스](https://www.notion.so/3f194a35cc4b42f0bb12adfd6a5e7433)
