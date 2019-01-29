---
layout:     post
title:      "Layouts in Xamarin.Forms"
header-img: "tech/img/20171115/xamarin-android-emulator-setup.jpg"
category:   tech
tags:       [Xamarin, C#, Mobile]
---
<blockquote>
<a href="{{ site.baseurl }}/tech/2017/12/15/layouts-in-xamarin-forms-kr/">Korean Version</a>
</blockquote>
<p>
<u><small>Please let me know if there is any incorrect information because this is what I summarized what I understood.</small></u>
</p>
<p>
In order to build up a well-made app, it is important to keep the same look on every devices. Therefore, Xamarin.Forms provides flexible layout containers. These containers calculate positions and sizes of UI components automatically and re-calculate them when a user rotates a device or changes a view size also automatically. These layout containers that Xamarin.Forms provides are StackLayout, Grid, AbsoluteLayout and RelativeLayout and StackLayout and Grid are popular among them.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/1.png" alt="Types of layout container">
</a>
<span class="caption text-muted">Types of layout container</span>
<p>
You can use WidthRequest and HeightRequest attributes to set width and height ot each UI component instead of width and height that are normally used in general because Xamarin.Forms doesn't guarantee exact sizes as they are re-calculated based on which platform the app is run. For alignment, you can use VerticalOptions and HorizontalOptions attributes.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/2.png" alt="Width and height attributes of UI component">
</a>
<span class="caption text-muted">Width and height attributes of UI component</span>
<p>
Each platform has different way to translate sizes and resolutions so if you set WidthRequest and HeightRequest, then although absolute sizes might not be same but would have the same look.
</p>
Resolution method on major platforms.
<ul>
    <li>Windows Phone – Effective pixels</li>
    <li>iPhone – Points</li>
    <li>Androind – Density-independent pixels</li>
</ul>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/4.png" alt="UI component size on each platform">
</a>
<span class="caption text-muted">UI component size on each platform</span>
<p>
Let's look into two popular layout containers, StackLayout and Grid.
</p>
<p>
StackLayout is just to stack up UI components in vertical way. As it is very simple, it is also used for building up prototypes.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/5.png" alt="StackLayout container">
</a>
<span class="caption text-muted">StackLayout container</span>
<p>
Grid is similar to table. You can set the size of rows and columns in <code>&lt;Grid&gt;</code> tag and can set where each UI component locates by Grid.Row and Grid.Column. Besides, You can make the layout flexible using attributes like RowSpan and ColumnSpan in HTML.
</p>
<a class="popupImg">
    <img src="{{ site.baseurl }}/tech/img/20171215/6.png" alt="Grid container">
</a>
<span class="caption text-muted">Grid container</span>
<p>
In general, layout containers and UI components have same attributes like the web design such as spacing, padding and margin. Hence, if you already know how to design a webpage, it would be easier to understand the layouts in Xamarin.Forms.
</p>
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>