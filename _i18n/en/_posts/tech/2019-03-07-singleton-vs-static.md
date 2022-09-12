---
layout:     post
title:      "Singleton pattern VS Static class in C#"
header-img: "img/tech-bg.jpg"
tags:       [C#, Singleton, Static, Design Pattern]
category:   tech
---
<p>
I had spent one or two days to try to understand which one of these two approaches I should use for exactly what kind of usage.
</p>
<p>
Thus, I here wrap up big features among what I have understood.
</p>
<p>
Common:
<ul>
    <li>
    Static classes and members are stored in a special memory area called “High-Frequency Heap” and this area is excluded from Garbage Collector (GC). Classes that implement the Singleton pattern (let’s say Singleton class) also have static members so these are also excluded from GC. Therefore, these resources are released when a corresponding process or AppDomain end.
    </li>
    <br />
    <li>
    Both cannot be instantiated so share only one reference throughout an application.
    </li>
</ul>
</p>
<p>
Difference:
<ul>
    <li>
    The static class cannot implement an interface or inherit other class. But it is possible for the Singleton class.
    </li>
    <br />
    <li>
    Developers can handle the point of time of instantiation by how they implement the laziness). On the other hand, the static class is dependent on Common Language Runtime (CLR).
    </li>
    <br />
    <li>
    The Singleton class can be written Thread-Unsafe, which means developers should handle this.
    </li>
</ul>
</p>
<p>
In the course of googling, I have seen some said using the Singleton pattern is not good in terms of performance while some said using the static class is not good at performance. So I could not find the answer that says “This is it!”. However, I by myself have concluded like below.
</p>
<p>
When to use the Singleton pattern:
<ul>
    <li>
    With the common sense, if only one instance is needed over an application. (Logging, caching, DB connection pool and hardware related jobs such as camera and sensor.
    </li>
</ul>
</p>
<p>
When to use the static class:
<ul>
    <li>
    For simple utility-kind classes, global variables, an instance creation class of the Factory pattern, etc…. Mostly, things that can be resolved by using the static class.
    </li>
</ul>
</p>
<p>
References:
</p>
[Singleton VS Static class in C#](https://dotnettutorials.net/lesson/singleton-vs-static-class/)
<br />
[Implementing the Singleton Pattern in C#](http://csharpindepth.com/articles/Singleton)
<br />
[Implementing Singleton in C#](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/ff650316(v%3dpandp.10))
<br />
[C# and beforefieldinit](http://csharpindepth.com/articles/BeforeFieldInit)
<br />
[TYPE INITIALIZATION CHANGES IN .NET 4.0](https://codeblog.jonskeet.uk/2010/01/26/type-initialization-changes-in-net-4-0/)
<br />
<blockquote><h2 class="section-heading">Happy Coding!</h2></blockquote>