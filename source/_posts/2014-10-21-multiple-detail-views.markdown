---
layout: post
title: "Multiple Detail Views in iOS8"
date: 2014-10-21 17:17:28 +0530
comments: true
categories: [code, UISplitViewController]
---
A few days back I was trying to create a simple iOS app to compete in one of the contest at [Topcoder](http://www.topcoder.com/?action=callback&utm_source=palewar&utm_campaign=ReferralProgram). I needed a Table View to show initial menu, then one of the menus had submenus so needed second Table View to show that. I needed a couple of Detail Views which should open when clicked on any of the menu items. <!-- more --> I hadn't programed for a few years now, so I was not familiar with Storyboards as Nibs were the norm a few years back. I was also learning Swift, so I couldn't really finish the app before the deadline.

However while trying to work on the app, I often googled for samples with different combinations of keywords 'Multiple Detail Views'. I found a sample by [Apple](https://developer.apple.com/library/ios/samplecode/MultipleDetailViews/Introduction/Intro.html), but it was last updated in 2012 and was done in Objective C and Xib/Nib files. I couldn't find anything done in [Swift](http://www.apple.com/swift/).

I spent a few days understanding Storyboards, Segues, new UISplitViewController in iOS8 and finally could do the job myself. I started with 'Master Detail Application' template of Xcode 6. I selected 'Universal' for Devices and 'Swift' as Language while creating project. I got a Split View, Navigation Controller setup along with a single Table View and a Detail View. I made copies of Table View and Detail View to end up with 2 Table Views and 2 Detail Views, just like in the Apple sample. 

Next we need to wire up the Segues. A simple solution to open different views from different rows of a Table View is to have 'Static Cells' in table view, which allows you to setup rows using Storyboard itself and then you can control+drag from individual rows to different views and voila you have automatic segues to different views. Nothing more needs to be done. This approach is actually very simple and perfect for the scenario we are considering right now. We need first Table View to display menu options, which will probably be known in advance so can use static cells for that.

However in real-life scenarios we may need to open different views from different rows which may not be known in advance. So I decided to use segues with prototype cells and set row contents at runtime using ``` cellForRowAtIndexPath ``` method. Since we don't have access to individual rows in Storyboards while using prototype cells, we can not do automatic segues and we can't control+drag from individual rows. We control+drag from ViewController icon at the top instead. Also we must set up an identifier for the segue using Attributes Inspector, we will need that to trigger segue manually like this:

``` swift
override func tableView(tableView: UITableView, didSelectRowAtIndexPath indexPath: NSIndexPath) {
        if indexPath.row == 0 {
            self.performSegueWithIdentifier("showTableView2", sender: self)
        } else if indexPath.row == 1 {
            self.performSegueWithIdentifier("showDetail1", sender: self)
        } else {
            self.performSegueWithIdentifier("showDetail2", sender: self)
        }
    }

```  

And that's how we open different views from rows of a Table View. I did write a little more code to take care of Back Navigation button for Detail Views and to handle portrait to landscape transition correcly for iPhone 6+ (Yes it's a little different from iPad landscape transition). Also we used **Show Detail** segue instead of **Push**. Show Detail is an **Adaptive segue** introduced with iOS8 and it lets us use SplitView Controller for iPhone app as well and that's how we could do an universal app using a single storyboard, which runs well on both iPhones as well as iPads. You can get the complete code from [Github](https://github.com/palewar/Swift-Samples). I hope it will come handy while doing your new iOS8 project in Swift.

Happy Swifting :-)