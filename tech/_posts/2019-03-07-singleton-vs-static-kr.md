---
layout:     post
title:      "싱글턴 패턴 VS Static 클래스 in C#"
header-img: "img/tech-bg.jpg"
tags:       [C#, Singleton, Static, Design Pattern]
category:   tech
---
<p>
몇일에 걸쳐 이 두가지 방법 중 정확히 어떤 걸 어떤 용도로 써야 하는지 이해를 하려고 노력했습니다.

이해한 내용 중 큰 특징들만 간단히 정리하자면,
</p>
<p>
공통점:
<ul>
    <li>
    Static 클래스/멤버는 특수한 메모리 영역인 High-Frequency Heap 에 저장되고 이 영역은 Garbage Collector(이하 GC) 의 청소 대상이 아니다.  싱글턴 패턴을 구현한 클래스(이하 싱글턴 클래스) 역시 static 멤버를 가지고 있으므로 GC 의 청소 대상이 아니다. 따라서, 해당 프로세스나 AppDomain 이 종료될 때 해제된다.
    </li>
    <br />
    <li>
    둘 다 객체를 생성할 수 없고 하나의 레퍼런스만을 앱 전체에서 공유한다.
    </li>
</ul>
</p>
<p>
차이점:
<ul>
    <li>
    Static 클래스는 인터페이스 구현 및 클래스 상속이 안 된다. 싱글턴 클래스는 된다.
    </li>
    <br />
    <li>
    싱글턴 클래스는 레퍼런스 생성 시점을 컨트롤 할 수 있다 (구현 방법에 따라 Laziness 조절 가능). Static 클래스는 Common Language Runtime (CLR) 에 의존적이다.
    </li>
    <br />
    <li>
    싱글턴 클래스는 Thread-Unsafe 하게 작성할 수도 있다. (즉, 개발자가 이를 컨트롤 해줘야 한다.)
    </li>
</ul>
</p>
<p>
구글링을 하다보니 싱글턴 클래스를 쓰는 게 성능 입장에서는 좋지 않다. 라는 얘기도 있고 Static 클래스가 성능 입장에서 좋지 않다. 라는 글도 있고 해서 명확하게 딱 이거다! 라고 할 만한 답을 찾지는 못했습니다만, 이해한 바를 토대로 아래와 같이 쓰면 되겠다는 결론을 내렸습니다.
</p>
<p>
싱글턴 클래스를 쓰는 경우:
<ul>
    <li>
    상식적으로 생각했을 때, 하나의 인스턴스만 있어야 하는 경우 (로깅, 캐싱, DB 커넥션 풀, 카메라, 센서 등 하드웨어 관련 작업 클래스)
    </li>
</ul>
</p>
<p>
Static 클래스를 쓰는 경우: 
<ul>
    <li>
    간단하게 Utility 용도로 사용되는 함수나 글로벌 변수, 팩토리 패턴 중 생성 클래스 등등.. 주로 Static 만으로 간단히 해결할 수 있는 것들
    </li>
</ul>
</p>
<p>
참고 자료:
</p>
[Singleton VS Static class in C#](https://dotnettutorials.net/lesson/singleton-vs-static-class/)
<br />
[Implementing the Singleton Pattern in C#](http://csharpindepth.com/articles/Singleton)
<br />
[Implementing Singleton in C#](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/ff650316(v%3dpandp.10))
<br />
[C# and beforefieldinit](http://csharpindepth.com/articles/BeforeFieldInit)
<br />
[TYPE INITIALIZATION CHANGES IN .NET 4.0](https://codeblog.jonskeet.uk/2010/01/26/type-initialization-changes-in-net-4-0/)
<br />
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>