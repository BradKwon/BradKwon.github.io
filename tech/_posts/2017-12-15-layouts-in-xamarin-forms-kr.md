---
layout:     post
title:      "Xamarin.Forms 레이아웃"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin, C#, Mobile]
category:   tech
---
<blockquote>
<a href="{{ site.baseurl }}/tech/2017/12/15/layouts-in-xamarin-forms/">영문 버전</a>
</blockquote>
<p>
<u><small>이 글은 저도 Xamarin 을 배우는 입장에서 공부한 내용을 정리해 놓은 글이기 때문에 혹시 틀린 내용이 있으면 지적해 주시면 감사하겠습니다.</small></u>
</p>
<p>
앱을 제대로 만드려면 화면 크기나 해상도가 다른 여러 기기 모두에서 동일한 디자인을 유지해야 하는데 이를 위해 Xamarin.Forms 에서는 유연한 레이아웃 컨테이너들을 제공한다. 이 컴포넌트들은 UI 컨트롤들의 크기 및 위치를 자동으로 계산해주고, 사용자가 기기를 회전하거나 화면 크기를 변경할 경우 자동 재계산 해준다. 이러한 레이아웃 컨테이너에는 StackLayout, Grid, AbsoluteLayout, RelativeLayout 이 있는데 그 중 StackLayout 과 Grid 이 가장 많이 사용된다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/1.png" alt="레이아웃 컨테이너 종류">
</a>
<span class="caption text-muted">레이아웃 컨테이너 종류</span>
<p>
Xamarin.Forms 에서 제공하는 레이아웃 컨테이너들은 자동 계산이 되기 때문에 각각 UI 컨트롤의 크기를 지정할 때 일반적인 Width, Height 가 아닌 WidthRequest, HeightRequest 속성을 사용하여 크기를 지정하게 된다. 그리고 컨트롤들의 가로, 세로 정렬을 위해 VerticalOptions, HorizontalOptions 속성이 제공된다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/2.png" alt="컨트롤 가로, 세로 속성">
</a>
<span class="caption text-muted">컨트롤 가로, 세로 속성</span>
<p>
플랫폼들마다 사용하는 해상도 처리 방식이 아래와 같이 틀리기 때문에 아래와 같이 WidthRequest, HeightRequest 를 지정하면 화면 비율 및 플랫폼에 따라 크기가 틀려지지만 동일한 디자인을 유지하게 된다.
</p>
해상도 처리방식
<ul>
    <li>윈도우폰 – Effective pixels</li>
    <li>아이폰 – Points</li>
    <li>안드로이드 – Density-independent pixels</li>
</ul>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/4.png" alt="플랫폼별 컨트롤 크기">
</a>
<span class="caption text-muted">플랫폼별 컨트롤 크기</span>
<p>
많이 사용되어지는 StackLayout 과 Grid 에 대해 잠깐 살펴보겠다.
</p>
<p>
StackLayout 은 아래와 같이 UI 컨트롤들을 세로 방향으로 추가해 가는 방식인데 간단하여 프로토타이핑에 많이 사용되어진다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/5.png" alt="StackLayout 방식">
</a>
<span class="caption text-muted">StackLayout 방식</span>
<p>
Grid 는 테이블과 동일하다고 생각하면 될 듯하다. <code>&lt;Grid&gt;</code> 태그 안에 각 행, 열의 크기를 미리 지정할 수도 있고 각 UI 컨트롤이 들어갈 셀의 위치를 Grid.Row, Grid.Column 으로 지정하면 된다. HTML 의 RowSpan, ColumnSpan 등과 같은 속성들을 사용하여 유연하게 컨트롤들을 배치시킬 수 있다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/6.png" alt="Grid 방식">
</a>
<span class="caption text-muted">Grid 방식</span>
<p>
전반적인 레이아웃 컨테이너 및 컨트롤들에 Spacing, Padding, Margin 과 같은 화면 디자인에 필요한 속성들도 사용할 수 있는 걸로 보아 웹 디자인을 간단하게 이해하고 있으면 이해가 더 수월하리라 생각된다.
</p>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>