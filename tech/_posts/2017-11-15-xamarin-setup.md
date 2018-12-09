---
layout:     post
title:      "Xamarin Android Emulator Setup in Visual Studio 2017"
subtitle:   "with Visual Studio Emulator for Android"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin,  Visual Studio, C#, Mobile, Android]
---
<blockquote>
<a href="{{ site.baseurl }}/tech/2017/11/15/xamarin-setup-kr/">Korean Version</a>
</blockquote>
<p>
I've recently started to learn Xamarin to build any mobile app with C# because I've mainly used C# for programming. 
The concept of Xamarin which is "write-once, run everywhere" seemed quite attractive so I decided to learn it.  
</p>
<p>
What I had to do at first is to set up Xamarin development environment. 
I chose a Visual Studio 2017 community version. 
For iOS deployment, I have to use either an iMac or a Macbook. 
As I only have Windows environment, so I decided to go with android first and try out the <a href="https://www.xamarin.com/live" target="_blank">Xamarin Live Player</a> app for iOS deployment. 
The live player function enables developers to deploy iOS apps to their actual iPhones via the live player app.
_(* This feature has changed to test apps on Android devices. For iOS, Mac host is still needed..[Link](https://docs.microsoft.com/en-us/xamarin/tools/live-player/))_
</p>
<p>
To install the Visual Studio 2017 was easy as well as Xamarin development tools. 
I could choose whatever tools I want to install on the workload while installing.
</p>
<a class="popupImg">
    <img src="https://developer.xamarin.com/guides/cross-platform/troubleshooting/questions/visualstudio-2017-rc/Images/install1-orig.png" alt="Visual Studio Installer Workloads View">
</a>
<span class="caption text-muted">Visual Studio Installer Workloads View</span>
<p>
The problem was when I tried to deploy an Android project to an emulator. 
I found out that there are two types of emulators. One is using Android SDK and another is using Visual Studio Emulator for Android. 
After taking a closer look on them, I found out that Visual Studio Emulator for Android is much faster than Android SDK 
so I installed it through Visual Studio installer again. _(* Versions after Marshmallow are not supported on this emulator and the website recommends Google emulator for the latest verions instead. [Link](https://visualstudio.microsoft.com/vs/msft-android-emulator/))_
You can select it to install in the Individual components > Emulators menu.
</p>
<a class="popupImg">
    <img src="https://social.msdn.microsoft.com/Forums/getfile/1012756" alt="Visual Studio Installer Individual components View">
</a>
<span class="caption text-muted">Choose Visual Studio Emulator for Android under Emulators if it is not selected.</span>
<p>
I installed that emulator on my computer and tried to deploy again. 
But this time, I couldn’t see anything running on the emulator although everything looked fine.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup1.jpg" alt="Debugging running view">
</a>
<span class="caption text-muted">Everything seems fine.</span>
<p>
So I googled what went wrong and finally reached this page.
</p>
<blockquote><a href="https://forums.xamarin.com/discussion/62307/xamarin-android-projects-failed-to-deploy-in-visual-studio-emulator-for-android" target="_blank">https://forums.xamarin.com/discussion/62307/xamarin-android-projects-failed-to-deploy-in-visual-studio-emulator-for-android</a></blockquote>
<p>
My case came under both the CPU compatibility and the registry.
</p>
<p>
My CPU was Intel i7-6600U and its code name is SkyLake and this CPU has an issue with Hyper-V that the Visual Studio Emulator for Android depends on. In order to sort this out, I followed this step.
</p>
<ol>
    <li>Open the Hyper-V Manager and go to settings of the virtual device.</li>
    <a class="popupImg">
        <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup2.jpg" alt="Hyper-V Manager main view">
    </a>
    <span class="caption text-muted">Right-click on the emulator you want to set up and choose settings.</span>
    <li>Check off “Migrate to a physical computer with a different processor version” in the Processor > Compatibility menu.</li>
    <a class="popupImg">
        <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup3.jpg" alt="Hyper-V Manager processor compatibility configuration view">
    </a>
</ol>
<p>
Secondly, for the registry for Android SDK Tools path, I created a new “Android SDK Tools” key under <blockquote>HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\</blockquote> because there wasn’t existing key like others. Then I added a string value with “Path” for name and the Android SDK full path on my computer for data. 
I could get the Android SDK full path from <blockquote>Visual Studio > Tools > Options > Xamarin > Android Settings > Android SDK Location</blockquote>
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup4.jpg" alt="Visual Studio tools options view">
</a>
<span class="caption text-muted">Copy and paste it to the registry.</span>
<p>
Eventually, I could see something different on the output window after executing debugging.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171115/xamarin-android-emulator-setup5.jpg" alt="Debugging running view2">
</a>
<span class="caption text-muted">Deployment Success!!</span>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>