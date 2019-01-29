---
layout:     post
title:      "Visual Studio 2017 에서 Xamarin 안드로이드 에뮬레이터 설치"
subtitle:   "Visual Studio Emulator for Android"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin,  Visual Studio, C#, Mobile, Android]
category:   tech
---
<blockquote>
<a href="{{ site.baseurl }}/tech/2017/11/15/xamarin-setup/">영문 버전</a>
</blockquote>
<p>
C# 을 주로 사용해 왔기 때문에 C# 을 이용해 모바일 앱 개발을 할 수 있게 해 주는 Xamarin 을 최근에 배우기 시작했습니다. 
Xamarin 의 컨셉인 "한 번의 작성으로 모든 곳에서 작동되게 한다." 가 꽤 매력적으로 들렸기 때문입니다.
</p>
<p>
우선 맨 처음으로 해야 했던 건 Xamain 개발 환경을 구축하는 것이었습니다. 
Visual Studio 2017 커뮤니티 버전을 사용하기로 했는데 iOS 버전을 배포하기 위해서는 맥이나 맥북을 사용해야 한다고 합니다. 
나는 윈도우 PC 밖에 없기 때문에 우선 안드로이드 버전만 해보기로 하고 iOS 버전은 
<a href="https://www.xamarin.com/live" target="_blank">Xamarin Live Player</a>* 앱으로 테스트 하기로 했습니다. 
이 Live Player 앱은 실제 아이폰에 이 앱을 설치하면 개발 중인 iOS 버전 앱을 배포할 수 있게 해주는 기능을 가진 앱 입니다. _(* 이 기능은 2018년 12월 현재 안드로이드 기기에서 테스트를 할 수 있는 기능으로 변경되었네요. iOS 는 여전히 Mac에 연결해서 해야 합니다. [링크](https://docs.microsoft.com/ko-kr/xamarin/tools/live-player/))_
</p>
<p>
Visual Studio 2017 과 Xamarin 개발 툴은 설치가 간단합니다. 
아래와 같이 Visual Studio 2017 설치 시에 내가 설치하고 싶은 툴들을 선택하여 설치하면 됩니다.
</p>
<a class="popupImg">
    <img src="https://developer.xamarin.com/guides/cross-platform/troubleshooting/questions/visualstudio-2017-rc/Images/install1-orig.png" alt="Visual Studio 2017 인스톨러 워크로드 화면">
</a>
<span class="caption text-muted">Visual Studio 2017 인스톨러 워크로드 화면</span>
<p>
문제는 안드로이드 프로젝트를 에뮬레이터에 배포할 때였습니다. 
이를 위해 두 가지 종류의 에뮬레이터가 있다는 것 알았는데, 
하나는 기존 안드로이드 개발할 때 사용하는 안드로이드 SDK 용 에뮬레이터이고 
다른 하나는 Visual Studio 에서 제공하는 Visual Studio Emulator for Android 였습니다. 
한 번 살펴보니 Visual Studio Emulator for Android 가 훨씬 빠르다고 하여 이를 설치하기로 했습니다. _(*현재 Marshmallow 이후 버전은 지원되지 않고 있고 웹사이트를 보면 최신 버전이 필요할 경우 구글 에뮬레이터를 사용하라고 나옵니다.[링크](https://visualstudio.microsoft.com/ko/vs/msft-android-emulator/))_
이 에뮬레이터는 아래와 같이 Visual Studio 2017 설치시 개별 컴포넌트 탭의 에뮬레이터 항목에서 선택 설치 가능합니다.
</p>
<a class="popupImg">
    <img src="https://social.msdn.microsoft.com/Forums/getfile/1012756" alt="Visual Studio 인스톨러 개별 컴포넌트 화면">
</a>
<span class="caption text-muted">에뮬레이터 밑에 Visual Studio Emulator for Android 를 선택</span>
<p>
설치 후 다시 안드로이드 버전을 배포해 보는데 되질 않았습니다. 
이번에는 특별한 문제가 없어보이는데도 에뮬레이터에 앱이 실행되지 않았습니다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup1.jpg" alt="디버깅 실행 화면">
</a>
<span class="caption text-muted">문제가 없어 보이네요.</span>
<p>
그래서 뭐가 문제인지 찾다가 다음 링크에서 해결할 수 있었습니다.
</p>
<blockquote><a href="https://forums.xamarin.com/discussion/62307/xamarin-android-projects-failed-to-deploy-in-visual-studio-emulator-for-android" target="_blank">https://forums.xamarin.com/discussion/62307/xamarin-android-projects-failed-to-deploy-in-visual-studio-emulator-for-android</a></blockquote>
<p>
제 경우는 CPU 호환성과 레지스트리 둘 다 문제였습니다.
</p>
<p>
제 CPU 는 인텔 i7-6600U 이고 이것의 코드명이 스카이레이크인데 이 코드명을 가진 CPU 들이 
Visual Studio Emulator for Android 에서 사용하는 Hyper-V 라는 기능과 문제가 있었던 것입니다. 
이 문제는 다음과 같은 방법으로 해결되었습니다.
</p>
<ol>
    <li>Hyper-V 매니저를 열고 가상 머신의 설정 화면을 연다.</li>
    <a class="popupImg">
        <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup2.jpg" alt="Hyper-V 매니저 메인 화면">
    </a>
    <span class="caption text-muted">설정을 변경할 에뮬레이터를 선택 후 마우스 오른쪽 버튼 클릭하여 설정 선택</span>
    <li>프로세서 > 호환성 메뉴에서 Migrate to a physical computer with a different processor version 항목 체크를 해제한다.</li>
    <a class="popupImg">
        <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup3.jpg" alt="Hyper-V 매니저 프로세서 호환성 설정 화면">
    </a>
</ol>
<p>
그리고 두번째 문제인 안드로이드 SDK 툴 경로 레지스트리 문제는 다음과 같이 레지스트리에 Android SDK Tools 키를 추가해 줬습니다.
<blockquote>HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\</blockquote> 
다른 사람들하곤 다르게 해당 키가 없었기 때문에 “Path” 라는 항목을 추가하고 안드로이드 SDK Tools 전체 경로를 값으로 설정해 줬습니다. 
이 안드로이드 SDK Tools 전체 경로는 아래에서 찾을 수 있습니다.
<blockquote>Visual Studio > 툴 > 옵션 > Xamarin > 안드로이드 설정 > 안드로이드 SDK 경로</blockquote>
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup4.jpg" alt="Visual Studio 툴 옵션 화면">
</a>
<span class="caption text-muted">레지스트리에 복사 붙여넣기</span>
<p>
마침내, 디버깅 했을 때 output 윈도우에 다른게 보였고 에뮬레이터에서 앱이 정상적으로 실행되었습니다.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup5.jpg" alt="디버깅 실행 화면2">
</a>
<span class="caption text-muted">배포 성공!!</span>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>