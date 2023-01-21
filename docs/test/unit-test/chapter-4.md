---
sidebar_position: 5
sidebar_label: 4. 좋은 단위 테스트의 4대 요소
---

# 🐤 Chapter 4. 좋은 단위 테스트의 4대 요소

## 🥕 좋은 단위 테스트의 4대 요소 자세히 살펴보기
좋은 단위 테스트에는 다음 네 가지 특성이 있다.
- 회귀 방직
- 리팩터링 내성
- 빠른 피드백
- 유지 보수성

이 네 가지 특성이 기본이다. 이 특성으로 어떤 자동화된 테스트도 분석할 수 있다.

### 🎈 첫 번째 요소: 회귀 방지
회귀는 소프트웨어 버그다. 코드를 수정한 후 기능이 의도한 대로 작동하지 않는 경우다.   

회귀 방지 지표에 대한 테스트 점수가 얼마나 잘 나오는지 평가하려면 다음 사항을 고려해야 한다.
- 테스트 중에 실행되는 코드의 양
- 코드 복잡도
- 코드의 도메인 유의성

일반적으로 실행되는 코드가 많을 수록 테스트에서 회귀가 나타날 가능성이 높다.   
코드의 양뿐만 아니라 복잡도와 도메인 유의성도 중요하다. 복잡한 비즈니스 로직을 나타내는 코드가 보일러플레이트 코드보다 훨씬 더 중요하다. 비즈니스에 중요한 기능에서 발생한 버그가 가장 큰 피해를 입히기 때문이다.   
반면에 단순한 코드를 테스트하는 것은 가치가 거의 없다. 이러한 코드는 짧고, 비즈니스 로직을 많이 담고 있지도 않다. 단순한 코드를 다루는 테스트는 실수할 여지가 많지 않기 때문에 회귀 오류가 많이 생기지 않는다. 단순한 코드의 예로 다음과 같이 속성 한 줄이 있다.

```cs
public class User {
  public string Name { get; set; }
}
```

게다가 여러분의 코드 외에 작성하지 않은 코드도 중요하다. 이 코드는 작성한 코드만큼이나 소프트웨어 작동에 영향을 미친다. 최상의 보호를 위해서는 테스트가 해당 라이브러리, 프레임워크, 외부 시스템을 테스트 범주에 포함시켜서 소프트웨어가 이러한 의존성에 대해 검증이 올바른지 확인한다.

### 🎈 두 번째 요소: 리팩터링 내성
좋은 단위 테스트의 두 번째 특성은 리팩터링 내성이다. 이는 테스트를 빨간색(실패)으로 바꾸지 않고 기본 애플리케이션 코드를 리팩터링할 수 있는지에 대한 척도다.   

리팩터링으로 정확히 무엇이 고장 났는지를 자세히 살펴봤지만, 알고 보니 아무것도 고장 나지 않았다. 기능은 예전과 같이 완벽하게 작동한다. 문제는 기반 코드를 수정하면 테스트가 빨간색으로 바뀌게끔 작성됐다는 것이다. 그리고 실제로 기능이 작동하지 않는지는 상관없다.   

이러한 상황을 거짓 양성이라고 한다. 거짓 양성은 허위 경보다. 실제로 기능이 의도한 대로 작동하지만 테스트는 실패를 나타내는 결과다. 이러한 거짓 양성은 일반적으로 코드를 리팩터링할 때, 즉 구현을 수정하지만 식별할 수 있는 동작은 유지할 때 발생한다.   

리팩터링 내성 지표에서 테스트 점수가 얼마나 잘 나오는지 평가하려면 테스트에서 얼마나 많이 거짓 양성이 발생하는지 살펴봐야 한다. 적을수록 좋다.   
단위 테스트의 목표는 프로젝트 성장을 지속 가능하게 하는 것이다. 테스트가 지속 가능한 성장을 하게 하는 메커니즘은 회귀 없이 주기적으로 리팩터링하고 새로운 기능을 추가할 수 있는 것이다. 어기에는 두 가지 장점이 있다.
- 기존 기능이 고장 났을 때 테스트가 조기 경고를 제공한다. 이러한 조기 경고 덕분에 결함이 있는 코드가 운형 환경에 배표되기 훨씬 전에 문제를 해결할 수 있다. 운영 환경이었으면 문제를 처리하는 데 훨씬 더 많은 노력이 필요했을 것이다.
- 코드 변경이 회귀로 이어지지 않을 것이라고 확신하게 된다. 이러한 확신이 없으면 리팩터링을 하는 데 주저하게 되고 코드베이스가 나빠질 가능성이 훨씬 높아진다.

거짓 양성은 이 두 가지 이점을 모두 방해한다.
- 테스트가 타당한 이유 없이 실패하면, 코드 문제에 대응하는 능력과 의지가 희석된다. 시간이 흐르면서 그러한 실패에 익숙해지고 그만큼 신경을 많이 쓰지 않는다.
- 반면에 거짓 양성이 빈번하게 테스트 스위트에 대한 신뢰가 서서히 떨어지며, 더 이상 믿을 만한 안전망으로 인식하지 않는다. 즉, 허위 경보로 인식이 나빠진다. 이렇게 신뢰가 부족해지면 리팩터링이 줄어든다. 회귀를 피하려고 코드 변경을 최소한으로 하기 때문이다.

### 🎈 무엇이 거짓 양성의 원인인가?
테스트에서 발생하는 거짓 양성의 수는 테스트 구성 방식과 직접적인 관련이 있다. 테스트와 테스트 대상 시스템의 구현 세부 사항이 많이 결합할수록 허위 경보가 더 많이 생긴다. 거짓 양성이 생길 가능성을 줄이는 방법은 해당 구현 세부 사항에서 테스트를 분리하는 것뿐이다. 테스트를 통해 SUT가 제공하는 최종 결과를 검증하는지 확인해야 한다. 테스트는 최종 사용자의 관점에서 SUT를 검증해야 하고 최종 사용자에게 의미 있는 결과만 확인해야 한다. 다른 모든 것은 무시해야 한다.   

테스트를 구성하기에 가장 좋은 방법은 문제 영역에 대해 이야기하는 것이다. 이러한 테스트가 실패하면, 이야기와 실제 애플리케이션 동작이 서로 거리가 멀어진 것을 의미한다. 이는 테스트 실패 유형 중 유일하게 도움이 되는 유형이다.   

다음 예를 살펴보자. 여기서 `MessageRenderer` 클래스는 머리글, 본문, 바닥글을 포함하는 메시지의 HTML 표현을 생성한다.

```cs
public class Message {
  public string Header { get; set; }
  public string Body { get; set; }
  public string Footer { get; set; }
}

public interface IRenderer {
  string Render(Message message);
}

public class MessageRenderer : IRenderer {
  public IReadOnlyList<IRenderer> SubRenderers { get; }
  public MessageRenderer() {
    SubRenderers = new List<IRenderer> {
      new HeaderRenderer(),
      new BodyRenderer(),
      new FooterRenderer(),
    };
  }

  public string Render(Message message) {
    return SubRenderers
      .Select(x => x.Render(message))
      .Aggregate("", (str1, str2) => str1 + str2);
  }
}
```

`MessageRenderer`를 어떻게 테스트할 수 있을까? 한 가지 가능한 방법은 이 클래스가 따르는 알고리즘을 분석하는 것이다.

```cs
[Fact]
public void MessageRenderer_uses_correct_sub_renderers() {
  var sut = new MessageRenderer();

  IReadOnlyList<IRenderer> renderers = sut.SubRenderers;

  Assert.Equal(3, renderers.Count);
  Assert.IsAssignableFrom<HeaderRenderer>(renderers[0]);
  Assert.IsAssignableFrom<BodyRenderer>(renderers[1]);
  Assert.IsAssignableFrom<FooterRenderer>(renderers[2]);
}
```

이 테스트는 하위 렌더링 클래스가 예상하는 모든 유형이고 올바른 순서로 나타나는지 여부를 확인한다.   

최종 결과가 바뀌지 않을지라도, 테스트를 수행하면 빨간색으로 변할 것이다. 이는 테스트가 SUT가 생성한 결과가 아니라 SUT의 구현 세부 사항과 결합했기 때문이다. 이 테스트는 똑같이 적용할 수 있는 다른 구현을 고려하지 않고 특정 구현만 예상해서 알고리즘을 검사한다.   

`MessageRenderer` 클래스의 상당 부분을 리팩터링하면 테스트가 실패한다. 말하자면, 리팩터링 과정은 애플리케이션의 식별할 수 있는 동작에 영향을 주지 않으면서 구현을 변경하는 것이다. 그리고 변경할 때마다 빨간색으로 변하는 것은 발호 테스트가 구현 세부 사항에 관계돼 있기 때문이다.   
이러한 테스트는 앞에서 설명한 모든 단점을 보여준다.
- 회귀 발생 시 조기 경고를 제공하지 않는다.
- 리팩터링에 대한 능력과 의지를 방해한다.

### 🎈 구현 세부 사항 대신 최종 결과를 목표로 하기
테스트를 깨지지 않고 리팩터링 내성을 높이는 방법은 SUT의 구현 세부 사항과 테스트 간의 결합도를 낮추는 것뿐이다. 즉, 코드의 내부 작업과 테스트 사이의 가능한 한 멀리 떨어뜨리고 최종 결과를 목표로 하는 것이다.   

먼저 다음 사항을 확인해야 한다. `MessageRenderer`에서 얻은 최종 결과는 무엇인가? 메시지의 HTML 표현이다. 그리고 클래스에서 얻을 수 있는 관찰 가능한 결과이기 때문에 이를 확인하는 것이 마땅하다. 이 HTML 표현이 그대로 유지되는 한 정확히 어떻게 생성되는지는 걱정할 필요가 없다. 이러한 구현 세부 사항은 상관없다. 다음 코드는 테스트의 새 버전이다.

```cs
[Fact]
public void Rendering_a_message() {
  var sut = new MessageRenderer();
  var message = new Message {
    Header = "h",
    Body = "b",
    Footer = "f"
  };
  string html = sut.Render(message);
  Assert.Equal("<h1><h</h1><b>b</b><i>f</i>", html);
}
```

이 테스트는 `MessageRenderer`를 블랙박스로 취급하고 식별할 수 있는 동작에만 신경 쓴다. 결과적으로 테스트는 리팩터링 내성이 부쩍 늘었다. 즉 HTML 출력을 똑같이 지키는 한, SUT의 변경 사항은 테스트에 영향을 미치지 않는다.   

이 테스트는 원래 버전보다 크게 개선됐다. 최종 사용자에게 의미 있는 유일한 결과, 즉 브라우저에 메시지가 표시되는 방식을 검증해 비즈니스 요구 사항에 들어맞는다. 이 테스트는 항상 적시에 실패하고 고객에게 영향을 줄 수 있는 애플리케이션 동작의 변경을 알려주므로 개발자가 주의를 기울여야 한다. 이 테스트에 거짓 양성은 거의 없을 것이다.