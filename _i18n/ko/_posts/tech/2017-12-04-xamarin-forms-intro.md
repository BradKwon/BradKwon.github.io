---
layout:     post
title:      "Xamarin.Forms 소개"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin, C#, 모바일]
category:   tech
---
<p>
Xamarin.Forms 는 이전 장인 <a href="{{ site.baseurl }}/tech/2017/12/01/xamarin-code-sharing-kr/" target="_blank">Code Sharing</a> 으로 가능했던 비즈니스 로직 재사용 방법처럼 공통적으로 쓰이는 UI 컴포넌트들을 재사용할 수 있게 해준다. 예를 들면, 페이지, 레이아웃, 입력 상자, 버튼 그리고 라벨과 같은 컴포넌트들은 모든 플랫폼에서 공통적으로 사용할 수 있기 때문에 이를 Xamarin.Forms 에서 모든 플랫폼에 동일하게 생성하여 개발 및 관리를 쉽게 해준다. 
</p>
<p>
Xamarin.Forms 에서 사용가능한 컴포넌트 리스트는 <a href="https://developer.xamarin.com/guides/xamarin-forms/user-interface/controls/views/" target="_blank">이 링크</a>를 통해 확인 가능하다.
</p>
<p>
코드와 화면으로 어떻게 구현이 되는지 한 번 확인해 보면 다음과 같은 하나의 코드로 안드로이드, 아이폰, 윈도우폰에 동일한 컴포넌트, 기능을 구현할 수 있다.
</p>
```csharp
public class MainPage : ContentPage
{
    Entry phoneNumberText;
    Button translateButton;
    Button callButton;
    string translatedNumber;

    public MainPage()
    {
        // Set padding in the page.
        this.Padding = new Thickness(20, 20, 20, 20);

        // Create a layout component for the page with the spacing setup.
        StackLayout panel = new StackLayout { Spacing = 15 };

        // Add a label
        panel.Children.Add(new Label
        {
            Text = "Enter a Phoneword:",
            FontSize = Device.GetNamedSize(NamedSize.Large, typeof(Label))
        });

        // Add a textbox for input
        panel.Children.Add(phoneNumberText = new Entry
        {
            Text = "1-855-XAMARIN"
        });

        // Add the translate button
        panel.Children.Add(translateButton = new Button
        {
            Text = "Translate"
        });

        // Add the call button
        panel.Children.Add(callButton = new Button
        {
            Text = "Call",
            IsEnabled = false
        });

        // Add a click event hander on the translate button
        translateButton.Clicked += (s, e) =>
        {
            string enteredNumber = phoneNumberText.Text;
            translatedNumber = PhonewordTranslator.ToNumber(enteredNumber);

            if (!string.IsNullOrWhiteSpace(translatedNumber))
            {
                callButton.IsEnabled = true;
                callButton.Text = "Call " + translatedNumber;
            }
            else
            {
                callButton.IsEnabled = false;
                callButton.Text = "Call";
            }
        };

        // Set the layout component to the page.
        this.Content = panel;
    }
}
```
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171204/1.png" alt="각각 모바일 플랫폼별 화면">
</a>
<span class="caption text-muted">각각 모바일 플랫폼별 화면</span>
<p>
내부 동작 방식을 보면 버튼을 예로 들었을 때, 위의 코드에서와 같이 Button 클래스를 생성하고 click event handler 를 C# 으로 작성해서 컴파일을 하면 Xamarin 이 각각 플랫폼에 맞게 이를 변환한다고 보면 된다. 각각 플랫폼의 언어로 컴파일이 되었는지는 저는 궁금하지 않아서 보진 않았지만 궁금하신 분들은 한 번 찾아서 보면 좋을 것 같다.
</p>
<p>
그러면 공통적으로 사용할 수 없는 플랫폼 의존적인 기능들은 어떻게 구현할까? 이는 Xamarin 에서 제공하는 DependencyService 등이나 인터페이스나 추상 클래스를 사용하여 상위 클래스를 만든 후 Dependency Injection (DI) 패턴을 적용하여 각각의 플랫폼에서 자기 코드를 넘겨서 처리하는 방법이 있다. 여기선 Xamarin.Forms 가 어떤건지 개념을 잡기 위해 훑어만 보는 수준이므로 (나도 아직 잘 모름..) 실제 적용방법은 <a href="https://university.xamarin.com/welcome" target="_blank">Xamarin University</a> 등에서 각자 알아서 찾아보기로…
</p>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>