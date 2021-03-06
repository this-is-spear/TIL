# Inside Out & Outside In

## Classist vs Mockist

**Classist 와 Mockist 차이**

단위 테스트를 바라보는 두 관점, Classist vs Mockist

- 작은 코드 단위를 검증한다.
- 빠르게 수행이 가능해야 한다.
- **격리된 방식으로 처리한다.**

**Classist vs Mockist 관점은 격리된 방식을 처리하는 관점이 다르다.**

테스트 대상과 협력 객체 간의 격리인지 테스트와 테스트간의 격리인지 차이가 있다.

**Classist의 단위 테스트**

- 테스트를 격리해야 하는 대상은 코드가 아니라 또 다른 테스트
- 테스트 간의 공유하는 의존성이 아니라면 실제 객체를 사용

**Mockist의 단위 테스트**

- 테스트 대상을 협력 객체로 부터 격리하기 위해 테스트 대상이 의존하는 모든 것이 가짜 객체로 대체
- 따라서 객체들이 모두 잘 동작하는지 검증한다는 것은 단위와 단위의 통합이 잘 동작하는지 검증하는 것이다.

## Classical TDD vs Mockist TDD

### Inside Out

- 상향식으로 도메인 레이어부터 구현하는 방법이다.
- 실제 객체를 다뤄야 하기 때문에 도메인 모델부터 시작해야 한다.
- 의존하는 협력 객체가 실존해야 테스트를 작성할 수 있다.
- 프로덕션 코드에 덜 의존적인 테스트가 작성이 된다.

### OutSide In

- 하향식으로 프레젠테이션 레이어부터 구현하는 방법이다.
- 상위 레벨 테스트부터 시작한다.
- 테스트 더블을 활용해 테스트 대상이 의존하는 협력 객체를 테스트 대상으로 한다.
- 상대적으로 프로덕션 코드에 의존적인 테스트가 작성이 된다.

## 테스트를 작성하는 방법

### 아는 것에서 모르는 것으로

상향식, 하향식 둘 다 TDD의 프로세스를 효과적으로 설명할 수 없다. 만약 어떤 방향성을 가질 필요가 있는지 고민해야 한다면 아는 것에서 모르는 것(known-to-unknown)으로 진행하는 것이 좋다. 왜냐하면 우리가 어느 정도의 지식과 경험을 가지고 시작한다는 점, 개발하는 중에 새로운 것을 배루게 될 것임을 예상한다는 점을 암시하기 때문이다.

### 추천하는 방법

- To[-Down으로 방향을 잡고, Bottom-Up으로 구현하기
- 인수 테스트 작성을 통해 요구사항과 기능 전반에 대한 이해를 선행
- 내부 구현에 대한 설계 흐름을 구상
- 설계가 끝나면 도메인부터 차근차근 TDD로 기능 구현
- 만약 도메인이 복잡하거나 설계가 어려울 경우 이해하고 있는 부분부터 기능 구현