---
sidebar_position: 16
---

# 🌈 Chapter 15: 디자인 패턴과 프레임워크

- 소프트웨어 설계에서 반복적으로 발생하는 문제에 대해 반복적으로 적용할 수 있는 해결 방법을 **디자인 패턴**이라고 부른다. 디자인 패턴의 목적은 설계를 재사용하는 것이다.
- **프레임워크**는 설계와 코드를 함께 재사용하기 위한 것이다. 프레임워크가 제공하는 아키텍처가 요구사항에 적합하다면 다양한 환경에서 테스트를 거친 견고한 구현 코드를 쉽고 빠르게 재사용할 수 있다. 프레임워크는 각 애플리케이션의 요구에 따라 적절하게 커스터마이징할 수 있는 확장 포인트를 제공한다.
- 디자인 패턴은 특정한 번경을 일관성 있게 다룰 수 이쓴ㄴ 협력 템플릿을 제공한다. 프레임워크는 특정한 변경을 일관성 있게 다룰 수 있는 확장 가능한 코드 템플릿을 제공한다.
- 디자인 패턴이 일관성 있게 만들기 위해 재사용할 수 있는 설계의 묶음이라면, 프레임워크는 일관성 있는 협력을 제공하는 확장 가능한 코드라고 할 수 있다.

## 📚 디자인 패턴과 설계 재사용

### 🎈 소프트웨어 패턴

> 패턴 정의는 하나의 실무 컨텍스트에서 유용하게 새용해 왔고 다른 실무 컨텍스트에서도 유용할 것이라고 예상되는 아이디어다. - 마틴 파울러

- 패턴이 지닌 가장 큰 가치는 경험을 통해 축적된 실무 지식을 효과적으로 요약하고 전달할 수 있다는 점이다. 패턴은 경험의 산물이다. 따라서 실무경험이 적어도 패턴을 익히고 반복적으로 적용하는 과정 속에서 유연하고 품질 높은 소프트웨어를 개발하는 방법을 익힐 수 있게 된다.
- 패턴은 지식 전달과 커뮤니케이션의 수단으로 활용할 수 있기 때문에 패턴에서 가장 중요한 요소는 패턴의 이름이다. 예를 들어 *인터페이스를 하나 추가하고 이 인터페이스를 구체화하는 쿨래스를 만든 후 객체의 생성자나 `setter` 메서드에 할당해서 런타임 시에 알고리즘을 바꿀 수 있게 하자*는 STRATEGY 패턴을 적용하자라는 단순한 대화로 바뀐다.
- 패턴은 홀로 존재하지 않는다. 특정 패턴 내에 포함된 컴포넌트와 컴포넌트 간의 관계는 더 작은 패턴에 의해 서술될 수 있으며, 패턴들을 포함하는 더 큰 패턴 내에 통합될 수 있다. 이러한 연관된 패턴들의 집합들이 모여 하나의 **패턴 언어**를 구상한다고 정의한다.
- 패턴 언어는 연관된 패턴 카테고리뿐만 아니라 패턴의 생성 규칙과 함께 패턴 언어에 속한 다른 패턴과의 관계 및 협력 규칙을 포함한다.

### 🎈 패턴 분류
- 패턴을 분류하는 가장 일반적인 방법은 패턴의 범위나 적용 단계에 따라 **아키텍처 패턴**, **분석 패턴**, **디자인 패턴**. **이디엄**의 4가지로 분류하는 것이다.
- 가장 널리 알려진 디자인 패턴은 특정 정황 내에서 일반적인 설계 문제를 해결하며, 협력하는 컴포넌트들 사이에서 반복적으로 발생하는 구조를 서술한다. 디자인 패턴은 중간 규모의 패턴으로, 특정한 설계 문제를 해결하는 것을 목적으로 하며, 프로그래밍 언어나 프로그래밍 패러다임에 독립적이다.
- 디자인 패턴의 상위에는 소프트웨어의 전체적인 구조를 결정하기 위해 사용할 수 있는 **아키텍처 패턴**이 위치한다. 아키텍처 패턴은 미리 정의된 서브시스템들을 제공하고, 각 서브시스템들의 책임을 정의하며, 서브시스템들 사이의 관계를 조직화하는 규칙과 가이드라인을 포함한다.
- 디자인 패턴의 하위에는 **이디엄**이 위치한다. 이디엄운 특정 프로그래밍 언어에만 국한된 하위 레벨 패턴으로, 주어진 언어의 기능을 사용해 컴포넌트, 혹은 컴포넌트 간의 특정 측면을 구현하는 방법을 서술한다.
- 아키텍처, 디자인, 이디엄이 주로 기술적인 문제를 해결하는 데 초점을 맞추고 있다면 **분석 패턴**은 도메인 내의 개념적인 문제를 해결하는 데 초점을 맞춘다. 분석 패턴은 업무 모델링 시에 발견되는 공통적인 구조를 표현하는 개념들의 집합이다.

### 🎈 패턴과 책임-주도 설계
- 책임과 협력을 결정하는 작업이 대부분의 경우에는 훌륭한 품질의 설계를 얻기 위해 많은 시간과 노력을 들여야만 한다.
- 패턴은 공통으로 사용할 수 있는 역할, 책임, 협력의 템플릿이다. 패턴은 반복적으로 발생하는 문제를 해결하기 위해 사용할 수 있는 공통적인 역할과 책임, 협력의 훌륭한 예제를 제공한다.
- 패턴을 따르면 특정한 상황에 적용할 수 있는 설계를 쉽고 빠르게 떠올릴 수 있다. 특정한 상황에 적용 가능한 패턴을 잘 알고 있다면 책임 주도 설계의 절차를 하나하나 따르지 않고도 시스템 안에 구현할 객체들의 역할과 책임, 협력 관계를 빠르고 손쉽게 구성할 수 있다.
- 디자인 패턴의 구성요소가 클래스와 메서드가 아니라 역할과 책임이라는 사실을 이해하는 것이 중요하다. 디자인 패턴은 단지 역할과 책임, 협력의 템플릿을 제안할 뿐 구체적인 구현 방법에 대해서는 제한을 두지 않는다.

### 🎈 캡슐화와 디자인 패턴
- 상속 계층을 합성 관계로 유지해야 하는 다양한 설계 원칙과 이유에 대한 설계는 `STRATEGY` 패턴이다. `STRATEGY` 패턴의 목적은 알고리즘의 변경을 캡슐화하는 것이고 이를 구현하기 위해 객체 합성을 이용한다.
- 알고리즘을 캡슐화하기 위해 합성 관계가 아닌 상속 관계를 사용하는 것을 `TEMPLATE METHOD` 패턴이라고 부른다. `TEMPLATE METHOD` 패턴은 부모 클래스가 알고리즘의 기본 구조를 정의하고 구체적인 단계는 자식 클래스에서 정의하게 함으로써 변경을 캡슐화할 수 있는 디자인 패턴이다.
- `DECORATOR` 패턴은 객체의 행동을 동적으로 추가할 수 있게 해주는 패턴으로서 기본적으로 객체의 행동을 결합하기 위해 객체 합성을 사용한다. 또한, 선택적인 행동의 개수와 순서에 대한 변경을 캡슐화할 수 있다.
- 대부분의 디자인 패턴의 목적은 특정한 변경을 캡슐화함으로써 유연하고 일관성 있는 협력을 설계할 수 있는 경험을 공유하는 것이다.

### 🎈 패턴은 출발점이다
- 패턴은 설계의 목표가 돼서는 안 된다. 패턴은 단지 목표로 하는 설계에 이를 수 있는 방향을 제시하는 나침반에 불과하다.
- 디자인 패턴이 현재의 요구사항이나 적용 기술, 프레임워크에 적합하지 않다면 패턴을 그대로 따르지 말고 목적에 맞게 패턴을 수정해야 한다.
- 패턴을 적용할 때 컨텍스트의 적절성은 무시한 채 패턴의 구조에만 초점을 맞춰서는 안된다. 정당한 이유 없이 사용된 모든 패턴은 설계를 복잡하게 만드는 장애물이다.
- 패턴을 적용할 떄는 항상 설계를 좀 더 단순하고 명화갛게 만들 수 있느 방법이 없는지를 고민해야 한다. 또한 코드를 공유하는 모든 사람들이 적용된 패턴을 알고 있어야 한다.
- 패턴을 가장 효과적으로 적용하는 방법은 패턴을 지향하거나 패턴을 목표로 리팩터링하는 것이다.

## 📚 프레임워크와 코드 재사용

### 🎈 코드 재사용 대 설계 재사용
- 디자인 패턴은 프로그래밍 언어에 독립적으로 재사용 가능한 설계 아이디어를 제공하는 것을 목적으로 하기 때문에 언어에 종속적인 구현 코드를 정의하지 않는다. 그렇기에 디자인 패턴을 적용하기 위해서는 설계 아이디어를 프로그래밍 언어의 특성에 맞춰 가공해야 하고 매번 구현 코드를 재작성해야 한다는 단점이 있다.
- **프레임워크**란 추상 클래스나 인터페이스를 정의하고 인스턴스 사이의 상호작용을 통해 시스템 전체 혹은 일부를 구현해 놓은 재사용 가능한 설계 또는 애플리케이션 개발자가 현재의 요구사항에 맞게 커스터마이징할 수 있는 애플리케이션의 골격을 의미한다.
- 프레임워크는 코드를 재사용함으로써 설계 아이디어를 재사용한다. 프레임워크는 애플리케이션의 아키텍처를 제공하며 문제 해결에 필요한 설계 결정과 이에 필요한 기반 코드를 함께 포함한다.

### 🎈 상위 정책과 하위 정책으로 패키지 분리하기
- 프레임워크의 핵심은 추상 클래스나 인터페이스와 같은 추상화라고 할 수 있다.
- 프레임워크는 여러 애플리케이션에 걸쳐 재사용 가능해야 하기 때문에 변하는 것과 변하지 않는 것들을 서로 다른 주기로 배폴할 수 있도록 별도의 배포 단위로 분리해야 한다. 의존성 역전 원칙에 따라 추상화에만 의존하도록 의존성의 방향을 조정하고 추상화를 경계로 패치지를 분리해야 한다.
- 상위 정책을 구현하고 있는 패키지가 충분히 안정적이고 성숙했다면 하위 정책 패키지로부터 완벽히 분리해서 별도의 배포 단위로 만들 수 있다. 상위 정책 패키지와 하위 정책 패키지를 물리적으로 완전히 분리하고 나면 상위 정책 패키지를 여러 애플리케이션에서 재사용할 수 있는 기반이 마련된 것이다. 다시 말해 재사용 가능한 프레임워크가 만들어진 것이다.
- 프레임워크는 여러 애플리케이션에 걸쳐 일관성 있는 협력을 구현할 수 있게 해준다. 우리는 동일한 프레임워크를 사용하는 여러 애플리케이션에 걸쳐 일관성 있게 코드를 설계하고 구현할 수 있다.

### 🎈 제어 역전 원리
- 의존성 역전 원리는 전통적인 설계 방법과 객체지향을 구분하는 가장 핵심적인 원리다. 의존성 역전 원리에 따라 구축되지 않은 시스템은 협력 흐름을 재사용할 수도 없으며 변경에 유연하게 대처할 수도 없다.
- 의존성 역전 원리는 프레임워크의 가장 기본적인 설계 메커니즘이다.
- 의존성을 역전시킨 객체지향 구조에서는 반대로 프레임워크가 애플리케이션에 속하는 서브클래스의 메서드를 호출한다. 따라서 프레임워크를 사용할 경우 개별 애플리케이션에서 프레임워크로 제어 흐름의 주체가 이동된다. 즉, 의존성을 역전시키면 제어 흐름의 주체 역시 역전된다. 이를 **제어 역전 원리**, 또는 **할리우드 원리**라고 한다.
- 프레임워크에서는 일반적인 해결책만 제공하고 애플리케이션에 따라 달라질 수 있는 특정한 동작은 비워둔다. 그리고 이렇게 완성되지 않은 채로 남겨진 동작을 훅(Hook)이라고 부른다. 훅의 구현 방식은 애플리케이션의 컨텍스트에 따라 달라진다. 재정의된 훅은 제어 역전 원리에 따라 프레임워크가 원하는 시점에 호출된다.
- 여기서 협력을 제어하는 것은 프레임워크다. 우리는 프레임워크가 적절한 시점에 실행할 것으로 예상되는 코드를 작성할 뿐이다. 제어가 우리에게서 프레임워크로 넘어가 버린 것이다. 다시 말해서 제어가 역전된 것이다.