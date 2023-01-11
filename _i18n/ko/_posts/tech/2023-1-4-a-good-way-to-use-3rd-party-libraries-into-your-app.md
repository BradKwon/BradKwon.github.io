---
layout:     post
title:      "외부 라이브러리를 사용하는 좋은 방법"
header-img: "img/home-bg.jpg"
tags:       [Architecture, Design Pattern]
category:   tech
---

모바일 앱 개발을 시작한 이래로 상당히 많은 외부 라이브러리들을 사용하고 있습니다. 이미 많이 사용되어 검증되고 훌륭한 외부 라이브러리를 사용하는 건 분명 엄청난 혜택이고 이젠 개발을 할 때 꼭 필요한 부분이 되었지만 유지보수를 생각하면 무턱대고 그냥 갔다 쓸 수는 없습니다.

제가 외부 라이브러리를 사용하면서 겪게 된 몇 가지 문제들이 있었는데,

1. 구글이나 파이어베이스 같은 서비스 변경으로 외부 라이브러리 버전이 업데이트 되었는데 API 에 변경이 생겼을 때
2. 네이티브 라이브러리가 업데이트 되었는데 외부 바인딩 (Xamarin 용 네이티브 라이브러리 Wrapper. Flutter 전에 사용했습니다. ㅠ.ㅠ) 라이브러리가 업데이트가 안 되어 직접 바인딩 라이브러리를 만들었을 때
3. 유닛 테스트 코드 작성할 때

이런 경우가 발생하면 진짜 이거 해결하느라 머리카락 빠지고 쓸데없이 많은 부분을 건드려야 해서 힘들었습니다. 이럴 때마다 동료들과 제가 생각해 낸 가장 간단하고 쉬운 방법은 중간에 레이어를 두는 것이었습니다. Wrapper 또는 Delegator 라고도 할 수 있겠네요.

예로, 만약 구글 맵 라이브러리를 사용하고자 할 경우, 레이어 구조를

*Main app <- map wrapper <- google map*

요런 식으로 하면 됩니다. 그러면 구글 맵 라이브러리는 map wrapper 와만 연결되므로 메인 앱에서는 구글 맵 라이브러리에 의존하지 않게 됩니다. 그 결과, 구글 맵 라이브러리에 변화가 있더라도 항상 메인 앱에 영향을 주지 않게 되고 유닛 테스트 코드 작성 시에 쉽게 mocking 을 할 수 있으며 나중에 네이버 맵 라이브러리로 교체할 수 있는 유연성이 생기게 됩니다.

><h2>“서드파티 API 를 감싸는 것은 베스트 프랙티스이다. - 로버트 C. 마틴</h2>

저도 로버트 마틴의 생각에 동의하고 적어도 외부 라이브러리를 사용하는 좋은 방법 중의 하나라고 생각합니다. 클린 아키텍처, 클린 코드의 저자인 개발계의 밥 아저씨 로버트 마틴의 이 인용구가 저를 든든하게 합니다.

이 베스트 프랙티스가 데코레이터 디자인 패턴이라는 것도 알게 되었는데 이 데코레이터 디자인 패턴은 Gang of Four 저자 이름으로 오래 전에 소개된 소프트웨어 디자인 패턴들 중 하나입니다. Dependency Injection 할 때 많이 쓰는 패턴이죠.

하지만, 흑백 논리로 이게 무조건 맞고 저게 무조건 틀리다고 하는 식의 접근은 언제나 정답이 아닙니다. 상황에 맞게 적절히 잘 섞어서 써야합니다. 운좋게도 Flutter 세계에서는 나름 유명한 Very Good Ventures 에서 쓴 엄청 좋은 Flutter 레이어 아키텍처 라는 글에서 위 사례에 대한 접근 방법을 소개한 부분이 있어 이를 간단히 요약 해 보았습니다.

>외부 라이브러리를 사용할 때 두 가지 옵션이 있는데,
>- 직접 붙여서 사용하는 방법
>- 외부 라이브러리 wrapper 를 만들어 사용하는 방법
>
>간단명료하거나 테스트가 쉬운 경우 첫번째 방법을, 그 외는 두번째 방법을 쓰는 게 낫습니다.

원문을 보고싶으신 분들은 아래 링크를 보시면 됩니다. 영어 원문이지만 요즘 세상에 번역기 돌리면 내용 파악에는 문제가 없으니 꼭 한 번 보면 좋을 것 같습니다.

- [Very good layered architecture in Flutter by Marcos Sevilla](https://verygood.ventures/blog/very-good-flutter-architecture)

그 외, 이를 뒷받침 해 주는 좋은 글들을 같이 링크합니다. 이 글들을 보시면 좀 더 자세하고 신빙성 있는 자료를 이해하기 쉬운 그림들과 함께 보실 수 있습니다.

- [Bohemian Wrapsody from Dmytro Danylyk](https://proandroiddev.com/bohemian-wrapsody-86a5ac3c910a)

- [Reddit discussion for the above Bohemian Wrapsody article](https://www.reddit.com/r/androiddev/comments/bfn57b/bohemian_wrapsody_wrapping_thirdparty_apis_is_a/)

- [Working with third-party libraries and what to do when you find yourself in a mess from CINQ IT solution company blog](https://www.cinqict.nl/blog/working-with-third-party-libraries-and-what-to-do-when)

><h2 class="section-heading">해피 코딩!</h2>