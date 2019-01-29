---
layout:     post
title:      "XAML in Xamarin"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin, C#, Mobile]
category:   tech
---
<blockquote>
<a href="{{ site.baseurl }}/tech/2017/12/10/xaml-in-xamarin-kr/">Korean Version</a>
</blockquote>
<p>
<u><small>Please let me know if there is any incorrect information because this is what I summarized what I understood.</small></u>
</p>
<p>
What isi XAML? It is an acronym for eXtensible Application Markup Language and is used to seperate UI and functional codes. UI codes can be placed in the behind C# codes and can be controlled there, however that would cause difficulties to work on view designs and function implementations repectively because they are mixed up in one file. (of course, for dynamic generation of UI componenets helplessly should be implemented in this way)
</p>
<p>
The key point of popular patterns or approaches thesedays in development such as MVC, MVVM and DI is to seperate each role or interest as a component and make it independent. After that, to mix and match those components to complete a product like machinary assembly. It went a bit far. By the way, due to the benefits we could get from modularization, I think UI and functions should also be seperated but it might depend on situations.
</p>
<p>
XAML code and behind code can be mapped like this.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171210/2.png" alt="Mapping between UI code and XAML code">
</a>
<span class="caption text-muted">Mapping between UI code and XAML code</span>
<p>
XAML is used in WPF, Silverlight, UWP and Windows Workflow. Xamarin.Forms also uses the same grammar like others but it has unique grammars so it cannot be same like others. Here, I think just knowing XAML is used in those technologies is enough.
</p>
<p>
Like HTML tags, each XAML tags can take event handlers.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171210/03.png" alt="Add an TextChanged event handler in XAML code">
</a>
<span class="caption text-muted">Add an TextChanged event handler in XAML code</span>
<p>
In Xamarin.Forms XAML, it supports Markup Extension for flexible settings of UI control attributes and for settings for respective mobile platforms, it provides the Device.OS property. Besides, it provides the reusable capsulation of components, which is called ContentView, so that it could be used in another UI like the user control feature in WinForms. When it comes to this feature, it would be better to check it out from <a href="https://university.xamarin.com/welcome" target="_blank">Xamarin University</a>
</p>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>