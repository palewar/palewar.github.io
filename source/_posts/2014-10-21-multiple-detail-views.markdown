---
layout: post
title: "Multiple Detail Views in iOS8"
date: 2014-10-21 17:17:28 +0530
comments: true
categories: [code, UISplitViewController]
---
A few days back I was trying to create a simple iOS app to compete in one of the contest at [Topcoder](http://www.topcoder.com/?action=callback&utm_source=palewar&utm_campaign=ReferralProgram). I needed a Table View to show initial menu, then one of the menus had submenus so needed second Table View to show that. I needed a couple of Detail Views which should open when clicked on any of the menu items. <!-- more --> I hadn't programed for a few years now, so I was not familiar with Storyboards as Nibs were the norm a few years back. I was also learning Swift, so I couldn't really finish the app before the deadline.

However while trying to work on the app, I often googled for samples with different combinations of keywords 'Multiple Detail Views'. I found a sample by [Apple](https://developer.apple.com/library/ios/samplecode/MultipleDetailViews/Introduction/Intro.html), but it was last updated in 2012 and was done in Objective C and Xib/Nib files. I couldn't find anything done in [Swift](http://www.apple.com/swift/).

I spent a few days understanding Storyboards, Segues, new UISplitViewController in iOS8 and finally could do the job myself. I started with 'Master Detail Application' template of Xcode 6 and made some modifications to code and storyboard to achieve the desired result. Using latest iOS 8 API meant we could do an universal app which should run well on both iPhones as well as iPads. You can get the code from [Github](https://github.com/palewar/Swift-Samples). I hope it will come handy while doing your new iOS8 project in Swift.

Happy Swifting :-)