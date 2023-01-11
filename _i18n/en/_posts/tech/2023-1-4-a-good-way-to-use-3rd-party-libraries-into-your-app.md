---
layout:     post
title:      "A good way to use 3rd-party libraries into your app"
header-img: "img/home-bg.jpg"
tags:       [Architecture, Design Pattern]
category:   tech
---

Since I started developing mobile apps, I've been using a lot of 3rd-party libraries into my main apps. Although it was super cool to use popular external libraries out there, some pitfalls came along.

The main three pitfalls were;

1. When some libraries must be upgraded because of the requirements from their eco-systems such as Google and Firebase, and they have some breaking changes
2. When some native library upgrades are necessary, however bindings (kind of library wrappers for Xamarin. Yes, I worked on Xamarin ㅠ.ㅠ) are not available yet so need to work on own custom bindings and plan to replace them later
3. When I write unit test

Those cases made me crazy and I had to pull out a bunch of hairs while resolving these. The most simple and easy solution that my colleagues and I came up with was to add an additional layer in between. This can be called like a wrapper or a delegator as well.

For instance, If I want to use the google map library, the architecture would be like:

*Main app <- map wrapper <- google map*

So, google map library is loosely coupled to the main app so it can be easily mocked and its changes don't always affect to the main app. And there is even a chance to replace map provider if needed later.

><h2>“Wrapping third-party APIs is a best practice.” — Robert C. Martin</h2>

Yes, I also think it is a best practice and at least it is a good way to plug in 3rd-party libraries. I needed this kind of quote to back me up as he is a renowned software engineer a.k.a Uncle Bob in the software world.

I also noticed that this is a decorator-ish pattern. The decorator pattern is one of the well-known design patterns from the Gang of Four. When I learned it back in university, it was too abstract so I almost forgot it until now. (Yes, I am not a good software engineer unfortunately)

However, it is always not good to have black and white thinking. We have to choose a proper solution depending on our situations. Luckily, I was able to bring one good article from the Very good layered architecture in Flutter written by Very Good Ventures (VGV). If you go to the subtitle **Use the right amount of abstraction** in the article, you will see that there are two choices we can take. In most business cases, we have to wrap it though.

- [Very good layered architecture in Flutter by Marcos Sevilla](https://verygood.ventures/blog/very-good-flutter-architecture)

I also found out two really great articles about this approach to back me up. They explain everything that I want to write here so I could save my time and toss my baton to them. Nice..

If you want to see more organized and clean articles and examples, please read below links.

- [Bohemian Wrapsody from Dmytro Danylyk](https://proandroiddev.com/bohemian-wrapsody-86a5ac3c910a)

- [Reddit discussion for the above Bohemian Wrapsody article](https://www.reddit.com/r/androiddev/comments/bfn57b/bohemian_wrapsody_wrapping_thirdparty_apis_is_a/)

- [Working with third-party libraries and what to do when you find yourself in a mess from CINQ IT solution company blog](https://www.cinqict.nl/blog/working-with-third-party-libraries-and-what-to-do-when)

><h2 class="section-heading">Happy Coding!</h2>
