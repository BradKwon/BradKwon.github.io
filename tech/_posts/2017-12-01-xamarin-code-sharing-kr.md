---
layout:     post
title:      "Xamarin 코드 공유"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin,  Visual Studio, C#, Mobile]
---
<blockquote>
<a href="{{ site.baseurl }}/tech/2017/12/01/xamarin-code-sharing/">영문 버전</a>
</blockquote>
<p>
<u><small>이 글은 저도 Xamarin 을 배우는 입장에서 공부한 내용을 정리해 놓은 글이기 때문에 혹시 틀린 내용이 있으면 지적해 주시면 감사하겠습니다.</small></u>
</p>
<p>
Xamarin 이 지향하는 게 동일한 기능을 안드로이드, 아이폰, 윈도우폰과 같은 각각의 플랫폼에 맞게 다시 작성하는 게 아닌 
한 번 작성된 코드로 위 세 플랫폼 모두에서 동작할 수 있도록 하는 것이지만 현실적으로는 이게 불가능하다. 
그래서 나오게 된 솔루션이 플랫폼 제한적인 코드를 제외한 공통적인 코드들을 재사용하기 위한 방법으로 나온 Code Sharing 방식이다. 
여기에는 크게 두 가지 방식이 있는데 첫째는 Shared Projects 이고 다른 하나는 Shared Compiled Binaries 이다. 
</p>
<p>
Xamarin University 강의 중 Xamarin 을 사용하는 이유에 대한 설명이 있어 옮겨와 번역을 해 보았다.
</p>
<blockquote>
One of the reasons you are probably either using or evaluating Xamarin is because it allows you to write your core logic 
once in a familiar .NET language and then share it across all the popular mobile platforms. This means we fix bugs once, 
implement new features once and reduce our maintenance and testable surfaces because we have less code to maintain
</blockquote>
<blockquote>
아마 당신이 Xamarin 을 사용하거나 고려하고 있는 이유들 중 하나는 핵심 로직을 익숙한 .Net 언어로 한 번만 작성한 뒤 주요 모바일 플랫폼들에서 
사용할 수 있다는 것일 것이다. 이 말은 버그를 한 번만 고치면 되고, 새로운 기능을 한 번만 만들면 되므로 적은 양의 코드를 가지게 되어 유지보수 
및 테스트할 부분이 줄어든다는 것이다.
</blockquote>
<p>
구체적인 구현 방법은 <a href="https://university.xamarin.com/welcome" target="_blank">Xamarin University</a>에 가면 
따라해 볼 수 있는 강의가 있으니 직접 강의를 보고 구현해 보는게 좋을 듯 하여 여기서는 간단히 개념만 정리해 보려고 한다.
</p>
<p>
Shared Projects 방식은, 별도의 Shared Project 를 하나 만들어서 안드로이드나 아이폰, 그리고 윈도우폰과 Universal Windows App(UWP) 
프로젝트들에 프로젝트 참조하여 사용하는 방식이다. 보통은 이렇게 별도의 프로젝트를 만들어서 다른 프로젝트에 참조를 하게 되면 이미 컴파일된 
바이너리 파일인 DLL 라이브러리로 참조가 되어 사용할 수 있는데 반해, 이 Shared Project 는 C# 의 Partial 기능처럼 컴파일 시점에 각각의 
참조된 플랫폼 프로젝트에 Shared Project 소스가 포함되서 컴파일이 된다는 점이다. 웹으로 치면 Include 와 동일하다. 
간단한 그림을 강의에서 캡쳐해서 나타내 보았다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171201/3.png" alt="Shared 프로젝트 개념">
</a>
<p>
Shared Compiled Binaries 방식은, 기존 방식처럼 별도의 라이브러리 프로젝트를 DLL 로 참조하는 것이다. 
여기에는 두 가지 방법이 있는데 첫째는, Portable Class Library (PCL) 프로젝트를 만들어 바이너리로 참조하게 하는 것이다. 
각각 플랫폼들에서 공통적으로 실행되기 때문에 실행될 플랫폼들의 프로파일을 설정해 줘야 한다. 
예를 들면, .Net Framework 4.5, Windows Universal 10.0, Windows Phone 8.1, Xamarin.Android, Xamarin.iOS, Xamarin.iOS (Classic) 과 
같은 것들을 말이다.
</p>
<p>
두번째는, .Net Standard Library 프로젝트를 만들어 바이너리로 참조하게 하는 것이다. 이건 모든 닷넷 플랫폼에서 공통적으로 사용할 수 있는 .Net API 라이브러리인데 1.0, 1.1, 1.2 … 현재 2.0 까지 버전이 나왔고 버전이 낮아질수록 사용할 수 있는 API 가 적어진다. 프로젝트 속성에서 버전을 선택할 수 있다. 
</p>
<p>
두 가지 방식 모두 장단점이 있기 때문에 개발환경에 맞게 선택해서 사용하면 되며, Shared Projects 방식은 같은 솔루션에 포함되어야 하기에 작은 규모의 앱이나 개발팀에 적합하며, 규모가 크거나 컴포넌트 형식으로 관리되어야 한다면 Shared Compiled Libraries 방식이 적합할 것이다.

역시 Xamarin University 강의에 각각 방식의 장단점을 정리해 놓은게 있어 옮겨와 번역을 해 보았다.
</p>
<p>
    <span><b>Shared Projects</b></span>
    <table class="table table-bordered table-condensed">
    <thead>
        <th width="50%" style="text-align:center;">Pros</th>
        <th width="50%" style="text-align:center;">Cons</th>
    </thead>
    <tbody>
    <tr>
        <td>모든 API 사용가능</td>
        <td>스파게티 소스가 될 가능성</td>
    </tr>
    <tr>
        <td>플랫폼 제한적인 로직 직접 추가 가능</td>
        <td>플랫폼 제한적인 로직 유닛 테스팅 어려움</td>
    </tr>
    <tr>
        <td>모든 파일 종류 공유 가능</td>
        <td>반드시 소스 형식으로 제공되어야 함</td>
    </tr>
    <tr>
        <td>작은 패키지 크기/플랫폼별 최적화</td>
        <td></td>
    </tr>
    </tbody>
    </table>
</p>
<p>
    <span><b>Shared Compiled Binaries</b></span>
    <table class="table table-bordered table-condensed">
    <thead>
        <th width="50%" style="text-align:center;">Pros</th>
        <th width="50%" style="text-align:center;">Cons</th>
    </thead>
    <tbody>
    <tr>
        <td>구조적 디자인 강제</td>
        <td>제한적인 API</td>
    </tr>
    <tr>
        <td>독립적으로 유닛 테스팅 가능</td>
        <td>코드성 파일외 공유의 어려움</td>
    </tr>
    <tr>
        <td>바이너리 형식으로 배포 가능 (NuGet)</td>
        <td>제한된 타겟 플랫폼 또는 API</td>
    </tr>
    <tr>
        <td></td>
        <td>플랫폼 제한적인 코드 통합에 추가 작업 필요</td>
    </tr>
    </tbody>
    </table>
</p>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>