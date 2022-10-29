---
sidebar_position: 18
sidebar_label: 17. Main 분석
---

# 🌈 Chapter 17: Main 분석

## 📚 고찰

### 🎈 점진적인 아키텍처
- 포트와 어댑터 아키텍처에 해당하는 구조를 만들었다.
- 브리지 역할을 하는 코드란 기술과 관련된 코드를 구동하거나 거기에 응답하는 코드를 말한다.
- Main인데, Main은 진입점이자 도메인 모델과 기반 구조가 함께 묶이는 부분에 해당한다. 이 예제의 목적상 중요한 바는 기능을 추가하고 반복해서 경험을 따르는 식으로 이러한 설계에 점진적으로 도달했다는 점이다. 경험에 의지해 의사 결정을 내리지만 코드를 이해하고 깔끔하게 유지하는 것만으로 이러한 해법에 거의 저절로 도달했다.

### 🎈 3지점의 원리
- 다음으로 뭘 해야 할지 확실하지 않거나 거기에 어떻게 도달할지 가늠할 수 없을 경우 여기에 대처하는 한 가지 방법은 켄트 벡이 보여준 것처럼 개발 변경 사항의 규모를 줄이는 것이다.
- 반복해서 코드상의 국부적인 문제를 해결함으로써 설계를 안전하게 탐사하고 있고 동작하는 코드에서 조금 벗어나지 않을 수 있다. 보통 이렇게만 하면 더 나은 설계로 향하기에 충분할 뿐 아니라 설계가 잘 동작하지 않는다면 언제든지 되돌아와서 다른 길로 나아갈 수 있다.
- 리팩터링을 하는 데 걸린 시간은 리팩터링 과정을 읽는 데 걸리는 시간보다 그렇게 길지 않았다. 이 점이 관심사를 명확하게 분리하는 데 대한 충분한 보상이라 생각한다. 경험을 토대로 좀 더 최단 거리에 가까운 길을 취할 수 있게 코드 상의 문제를 인식하는 것도 배웠다.

### 🎈 동적 설계와 정적 설계
- 코드를 리팩터링할 때 한 가지 이상의 시각을 고려해야 한다.
- 결국 리팩터링은 설계 활동이며, 우리가 배운 기술이 여전히 모두 필요하다는 의미이다. 리팩터링은 정적 구조(클래스와 인터페이스)에 초점을 맞추고 있어 애플리케이션의 동적(인스턴스와 스레드) 구조에 관한 시각을 잃어버리기 십상이다.
- 때문에 상호 작용 다이어그램이 필요할 때가 있다.