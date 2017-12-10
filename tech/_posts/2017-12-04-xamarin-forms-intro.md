---
layout:     post
title:      "Introduction to Xamarin.Forms"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin,  Visual Studio, C#, Mobile]
---
<blockquote>
<a href="{{ site.baseurl }}/tech/2017/12/04/xamarin-forms-intro-kr/">Korean Version</a>
</blockquote>
<p>
<u><small>Please let me know if there is any incorrect information because this is what I summarized what I understood.</small></u>
</p>
<p>
Xamarin.Forms enables for users to reuse commonly used UI components as well as business logics that are possible by the <a href="{{ site.baseurl }}/tech/2017/12/01/xamarin-code-sharing/" target="_blank">code sharing</a> feature that I dealt with before. For instance, components such as Page, Layout, Inputbox, Button and Label can be used in all platforms thus, we can write only one UI components generation code and then apply to all platforms through Xamarin.Forms.
</p>
<p>
You can see the list of available components in Xamarin.Forms through this <a href="https://developer.xamarin.com/guides/xamarin-forms/user-interface/controls/views/" target="_blank">link</a>.
</p>
<p>
If you take a look at how the code matches UI with below, you will notice that you can implement same components and functions on all platforms once you write the code once.
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
    <img src="{{ site.baseurl }}/tech/img/20171204/1.png" alt="UI views on each mobile platform">
</a>
<span class="caption text-muted">UI views on each mobile platform</span>
<p>
If we look into how this works under the hood, button classes created and bound click event handlers in C# code is transformed to each language for each playform at compile tiem. If you want to see what do the code or files transformed to each platform look like, please do research on it by yourself because I am quite...lazy and am not curious... but it would be great to understand the inside of Xamarin for sure :)
</p>
<p>
Then how we can implement functions that are platform-specific? Xamarin provides several approach to resolve this such as DependencyService or applying the dependency injection (DI) pattern with super classes like interfaces or abstract classes and then each platform inject their methods into it. In this writing, we are just catching a glimpse in order to understand Xamarin concept (I don't know well either..), so I recommend you watch lectures in the <a href="https://university.xamarin.com/welcome" target="_blank">Xamarin University</a>.
</p>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>