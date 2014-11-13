---
layout: post
title: "UISplitViewController=UINavigationController"
date: 2014-11-04 12:02:40 +0530
comments: true
categories: [theory, equals, UISplitViewController, Adaptive, iOS8]
---
You read it right. If you are using iOS8, UISplitViewController indeed behaves as if it's a UINavigationController on iPhone. Obviously it means that **UISplitViewController is now supported for iPhones as well**. This is a small but important part of the bigger picture of Universal Storyboards and Adaptive UI starting from iOS8. <!-- more --> Now it's possible for us to have a single **Universal Storyboard which supports all types of iPhones and iPads**.

You will also notice that in XCode6 there is now a new Master-Detail Application template. If you select a Universal Project option with it, you get a Storyboard with UISplitViewController and you can run it against both iPhone as well as iPad simulators. You use **new Adaptive segues, 'Show' for Master View and 'Show Detail' for Detail View instead of 'Push'** which is now deprecated. 'Show' is similar to 'Push'. When running on iPad 'Show Detail' ensures that Detail View is displayed on right side of Split, but when running on an iPhone 'Show Detail' automatically starts behaving as 'Show' and Detail View is displayed as the single view on top. Very creative approach isn't it?

For the sake of simplicity I have generalized a bit. Once you understand the concepts though, you need to know that above behavior is not really fixed and you can have a split view on an iPhone if you want. Not to forget iPhone 6+ by default supports Split View in landscape mode. To support Split View on smaller iPhone you can modify [Trait Collection](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UITraitSet_ClassReference/index.html). Also at times you may want to not display detail view on iPhones and instead directly show master view. If detail is empty, it doesn't make sense to display a blank view as the only view at the top. You can control which view appears as the top view on iPhone when using Universal Storyboard using new methods in [Delegate](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UISplitViewControllerDelegate_protocol/index.html)

For a really simple introduction to new UISplitViewController you may read this [post by Natasha Murashev](http://nshipster.com/uisplitviewcontroller/) and then come back and check out my [Multiple Detail Views Sample](http://swiftwala.com/multiple-detail-views) to see the Split View in action. I also suggest you to check out [Adaptive UI by Jesse Squires](http://www.jessesquires.com/adaptive-user-interfaces/) where he explains 'Size-Classes' in a very simple manner and suggests the way forward for iOS Developers and designers.

Let's be Adaptive :-)