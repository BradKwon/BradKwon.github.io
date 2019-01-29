---
layout:     post
title:      "XAML in Xamarin (한글)"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin, C#, Mobile]
category:   tech
---
<blockquote>
<a href="{{ site.baseurl }}/tech/2017/12/10/xaml-in-xamarin/">영문 버전</a>
</blockquote>
<p>
<u><small>이 글은 저도 Xamarin 을 배우는 입장에서 공부한 내용을 정리해 놓은 글이기 때문에 혹시 틀린 내용이 있으면 지적해 주시면 감사하겠습니다.</small></u>
</p>
<p>
XAML 이란? eXtensible Application Markup Language 의 약자로 Xamarin.Forms 에서는 UI 와 동작을 분리하기 위해 사용되어진다. 화면에 보여지게 될 컨트롤들은 C# 코드단에서도 생성하고 화면에 추가가 가능하지만 이 C# 코드단에는 해당 컨트롤들의 동작을 나타내는 코드들 또한 표시되므로 UI 와 동작이 한 파일안에 존재하게 되어 화면 디자인과 동작 로직을 나눠 작업하기가 어려워진다는 단점이 있다. (물론 동적으로 컨트롤들을 다뤄야할 경우엔 이 경우로 할 수 밖에 없는 경우가 많기는 하다)
</p>
<p>
현재 많이 사용되어지고 있는 MVC, MVVM, DI 등을 보면 핵심은 각각 역할 또는 관심별로 코드를 분리시켜 부품화하여 하나의 독립적인 부품을 만든 후 다른 부품들과 조립하여 하나의 제품을 만들어내는 일종의 기계 조립과정과도 비슷하다고 할 수 있을 것이다. 얘기가 조금 장황해졌지만 이로 인해 얻는 장점들이 많기 때문에 이렇게 분리를 하므로 UI 와 동작 역시 분리되는 게 맞다는 생각이 들지만 상황에 맞게 잘 쓰면 될 것 같다.
</p>
<p>
우선, 아래 그림과 같이 UI 단 코드는 아래와 같이 매핑이 된다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171210/2.png" alt="UI 코드와 XAML 코드 매핑">
</a>
<span class="caption text-muted">UI 코드와 XAML 코드 매핑</span>
<p>
XAML 은 WPF, 실버라이트, UWP, Windows Workflow 에서도 쓰이는데 Xamarin.Forms 에서 쓰이는 XAML 은 이들과 같은 문법을 쓰지만 고유의 문법이 존재하므로 같다고 볼 순 없다. 여기선 간단히 XAML 이 저런 데도 쓰이는 기술이다 까지만 알고 넘어가면 될 듯하다.
</p>
<p>
HTML 태그와 마찬가지로 아래와 같이 각 컨트롤 태그에 Event Handler 를 설정해 줄 수 있다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171210/03.png" alt="XAML 코드에 이벤트 핸들러 추가">
</a>
<span class="caption text-muted">XAML 코드에 이벤트 핸들러 추가</span>
<p>
Xamarin.Forms XAML 에서는 UI 컨트롤들의 값을 유연하게 설정할 수 있도록 Markup Extension 을 지원하고, 모바일 플랫폼별로 설정을 할 수 있도록 Device.OS 프로퍼티를 지원하며, 기존 Winforms 의 User Control 처럼 (ASP.Net MVC 의 경우 PartialView) 특정 UI 컨트롤들을 ContentView 라는 컴포넌트로 만들어 여러 화면에서 재사용 가능하도록 하는 기능도 지원한다. 여기에 대해서는 <a href="https://university.xamarin.com/welcome" target="_blank">Xamarin University</a> 를 통해 확인해 보는 것이 좋을 듯 하다.
</p>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>