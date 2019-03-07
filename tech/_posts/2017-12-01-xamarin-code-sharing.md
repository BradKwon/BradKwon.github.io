---
layout:     post
title:      "Xamarin Code Sharing"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
tags:       [Xamarin, C#, Mobile]
category:   tech
---
<p>
The aim of Xamain is to write a function once, run on every platform. However, it seems impossible pragmatically.
Therefore, this code sharing approach came out to reuse common code except for platform-specific code.
There are two ways in this approach. One is shared projects and the other is shared compiled binaries.
</p>
<p>
I quoted the part which explains the reason why you use or consider Xamarin from the lecture in Xamarin University.
</p>
<blockquote>
One of the reasons you are probably either using or evaluating Xamarin is because it allows you to write your core logic 
once in a familiar .NET language and then share it across all the popular mobile platforms. This means we fix bugs once, 
implement new features once and reduce our maintenance and testable surfaces because we have less code to maintain
</blockquote>
<p>
I think it would be better to watch lectures in <a href="https://university.xamarin.com/welcome" target="_blank">Xamarin University</a> and build up exercise projects in them so I am going to sum up basic concepts here.
</p>
<p>
Shared projects is to create an additional project in the solution and, in turn, to have other mobile platform projects, such as android, iOS, windows phone and universal windows app (UWP), refer to it. In the conventional way, this kind of project can be compied as binary file and being refered to other projects in the form of DLL, however this shared project is included to other mobile platform projects in the form of code and compiled together at compile time like partial feature in C#. The include feature in web development.
I captured the picture that depicts well of this concept.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171201/3.png" alt="Concept of shared projects">
</a>
<p>
Shared compiled binaries is to refer as a DLL like the conventional way.
There are also two approaches. One is to create portable class library (PCL) project and refer it.
In order to run on multiple platforms, you have to configure which platform are you going to run in the profile of this PCL project.
For example, such as .Net Framework 4.5, Windows Universal 10.0, Windows Phone 8.1, Xamarin.Android, Xamarin.iOS, Xamarin.iOS (Classic).
</p>
<p>
The other is to create .Net Standard Library project and refer it.
This is the .Net API library that can be commonly used in every .Net platform and it has rolled out up to version 2.0 from initial version 1.0. The lower version you choose, the less APIs you can use. You can choose which version you want to set in the project property.
</p>
<p>
As these two approaches hasa pros and cons respectively, you can choose either one that fits on your development environment.
Xamarin University recommends to use shared projects if the size of your dev team is small and should be in the same solution with other projects and to use shared compiled binaries if the size of dev team is big or should be controlled in the form of component.

I brought the summaries of each approach's pros and cons below.
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
        <td>All APIs available</td>
        <td>Can lead to spaghetti code</td>
    </tr>
    <tr>
        <td>Platform-specific logic can be added directly</td>
        <td>Difficult to unit test conditional code</td>
    </tr>
    <tr>
        <td>All file types can be shared</td>
        <td>Must be shipped in source form</td>
    </tr>
    <tr>
        <td>Smaller package sizes/platform-specific optimizations</td>
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
        <td>Enforces architectural design</td>
        <td>Limited APIs available</td>
    </tr>
    <tr>
        <td>Can be unit tested separately</td>
        <td>Difficult to share non-code files</td>
    </tr>
    <tr>
        <td>Can be shipped in binary form (NuGet)</td>
        <td>Limited to target platforms or APIs</td>
    </tr>
    <tr>
        <td></td>
        <td>Requires more work to integrate platform-specific code</td>
    </tr>
    </tbody>
    </table>
</p>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>