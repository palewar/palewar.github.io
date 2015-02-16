---
layout: post
title: "Calculator in Swift"
date: 2015-02-16 16:27:51 +0530
comments: true
categories: [code, autolayout, adaptive, stanford, cs193p]
---
{% img /images/stanford-ios8.png %} All new [CS193P](https://itunes.apple.com/us/course/developing-ios-8-apps-swift/id961180099) started at Stanford sometime back. Great news is, that it's being taught in Swift. I have just finished listening first 2 lectures. I am quite impressed with **Paul Hegarty**. He starts the lecture with firing Xcode, talking about it and then beginning to code a Calculator app in Swift. He explains concepts as and when needed while using them. Quite hands-on and practical approach I must say. 

If you have some experience with programming and are well conversant with [OOPS](http://en.wikipedia.org/wiki/Object-oriented_programming) concepts, then the course should be really easy to follow for you. It's a free course and available via iTunes, so I think anybody who is beginning with iOS development or Swift should really go through it.

Paul explains basics of [autolayout](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/AutolayoutPG/Introduction/Introduction.html) in Lecture 1 and explains constraints in Lecture 2. However what stands out in Lecture 2 (last 20 mins) is his explanation of [MVC](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller), he does that like a rock-star and uses roads, arrows, radio transmission analogies to drive home his message. 

There are reading assignments and programming assignments associated with lectures. I religiously read all the prescribed sections from the official [Apple book](https://developer.apple.com/library/mac/documentation/Swift/Conceptual/Swift_Programming_Language/index.html#//apple_ref/doc/uid/TP40014097-CH3-ID0) and actually did learn a few new things which I missed when I went through the book earlier. A couple of them are:

> Swift’s remainder operator can also operate on floating-point numbers: 8 % 2.5   // equals 0.5

and 

> We should Use ++i and --i in all cases instead of i++/i--, for expected behavior of modifying i and returning the result.

Then I moved onto Programming Assignment and started coding the calculator. However I was not really comfortable with the [RFP](http://en.wikipedia.org/wiki/Reverse_Polish_notation) Calculator, Paul demoed in the class, so I decided to instead code simple, standard calculator. Here is my code for it:

``` swift
class ViewController: UIViewController {

    @IBOutlet weak var displayLabel: UILabel!

    var isFirstDigit = true
    var operand1: Double = 0
    var operation = "="

    var displayValue: Double {
        get {
            //notice use of ! twice in below line. If you get that, then you have truely understood optionals :-)
            return NSNumberFormatter().numberFromString(displayLabel.text!)!.doubleValue
        }
        set {
            // Notice how we are using a Property Setter to perform additional tasks while 
            //setting value for the property
            displayLabel.text = "\(newValue)"
            isFirstDigit = true
            operation = "="

        }
    }

    //This single IBAction function is tied to all the digit buttons
    @IBAction func appendDigit(sender: UIButton) {

        let digit = sender.currentTitle!
        //Notice use of ternery operator in below line which results in a single line code
        //instead of usual if-else multiple lines
        displayLabel.text = isFirstDigit ? digit : displayLabel.text! + digit
        isFirstDigit = false
    }

    @IBAction func clearDisplay(sender: AnyObject) {
        displayValue = 0
           }

    @IBAction func saveOperand(sender: UIButton) {
        operation = sender.currentTitle!
        operand1 = displayValue
        isFirstDigit = true
    }

    @IBAction func calculate(sender: AnyObject) {
        switch operation {
        case "÷":displayValue = operand1 / displayValue
        case "×":displayValue *= operand1
        case "+":displayValue += operand1
        case "−":displayValue = operand1 - displayValue
        default:break
        }
    }


}
``` 

It's pretty simple code and I hope should be clear enough. Full project code is available at [Github](https://github.com/palewar/Swift-Samples)

Happy Learning :-)