### 인수검사(Acceptance Testing)

**인수검사**

**인수검사**(Acceptance Testing)는 정보시스템 검사 중 하나로, 시스템이 실제 운영 환경에서 사용될 준비가 되었는지 최종적으로 확인하는 단계이다. 시스템 검사는 사용자가 평가하고 관리자가 점검한다. 모든 관계자가 새로운 시스템을 만족하면 시스템은 설치를 위해 정식으로 인수된다.

> 💡 인수 테스트는 작업을 종료 시켜도 되는지 검증하는 테스트이다.

**테스트 주도 개발에서 인수 테스트**

보통 마지막 단계에서 수행하는 테스트를 의미하지만 ATDD에서는 기능을 구현할 때, 만들고자 하는 기능을 수행하는 인수 테스트를 작성하는 것으로 시작한다. 인수 테스트가 실패하는 동안은 시스템이 아직 그 기능을 구현하지 않고 있다는 것을 보여준다. 인수 테스트가 통과되면, 기능 구현은 끝이다.

### **ATDD의 특징**

**사용자의 관점**에서 올바르게 작동하는지 테스트이며 인수 조건은 기술(혹은 개발) 용어가 사용되지 않고 (개발자가 아닌) 일반 사용자들이 이해할 수 있는 단어를 사용하는 것이 특징이다.

### **ATDD는 테스트 의도에 따라 구현 방법이 달라진다.**

테스트하려는 의도가 사용자의 시나리오를 통해 요청부터 응답 값을 검증하고 싶으면 인수 테스트에서 E2E 테스트를 진행한다고 보면 된다.

<aside>
💡 인수 테스트의 개념은 테스트 의도에 따라 정해지는 것이지 테스트를 어떻게 구현하는지에 따라 정해지는 것이 아니다. 유닛 레벨이나 통합 레벨, 사용자 인터페이스 레벨에서 인수 테스트를 적용할 수 있다.

</aside>

**인수 검사를 E2E(**End Point to End Point**)로 구현**

사용자 시나리오를 End Point만 검사한다. 해당 인수 검사는 블랙 박스 테스트로 진행하게 된다.

**인수 검사를 단위 테스트로 구현**

사용자 시나리오를 단위 테스트로 구현한다. → 어떻게 보면 TDD처럼 보이지만, TDD는 요구사항 중 하나의 기능에 대한 검증 테스트를 통해 구현하는 방법이다.

**인수 검사를 통합 테스트로 구현**

사용자 시나리오의 처음부터 끝까지 검사한다. 해당 인수 검사는 그레이 박스 테스트로 진행하게 된다.

**ATDD를 이용해서 하는 방법이란**

인수 테스트를 유닛이나 컴포넌트가 의도한 동작을 하는지 확인하는 설계 검증 테스트로 사용할 수 도 있다. 어떤 경우든 인수 테스트는 사용자에게 애플리케이션이 인도될 수 있는 지를 확인한다.

해당 과정에서 **진행하려는 ATDD**

1. 백엔드 개발자가 단독적으로 적용해서 실천해볼 수 있는 범위로 진행하고 고객은 프론트엔드 개발자 혹은 API 활용하는 사람을 대상으로 진행한다.
2. API 접점에서 검증하는 E2E 테스트이며 Request와 Response 정보 이외 내부 정보는 최대한 가리는 블랙
박스 형식의 테스트로 진행한다.

### ATDD 요약

클라이언트가 의뢰했던 소프트웨어를 인수 받을 때, 미리 전달했던 요구사항이 충족되었는지를 확인하는 테스트이다.