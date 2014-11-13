---
layout: post
title: "Functions = Closures"
date: 2014-11-11 12:04:48 +0530
comments: true
categories: [theory, equals, closure, function]
published: true
---
Unlike my other posts [equating](http://swiftwala.com/blog/categories/equals/) 2 concepts, I am actually completely right this time. As Functions in Swift are actually just **Closures with a name**. So what is a Closure? It's like a function, but without a name :-)

Here is a simple Function:<!-- more -->

``` swift
func isFirstStringGreater(s1: String, s2: String) -> Bool {
    return s1 > s2
}
``` 
Which can be written as Closure like this:

``` swift
{ (s1: String, s2: String) -> Bool in
    return s1 > s2
}
``` 
So basically we write Closure inside the curly braces, omit the `func` keyword and a name and instead of wrapping body within braces, we mark the beginning of body by  `in` keyword.

Above closure can be further shortened to `{ s1, s2 in s1 > s2 }` and even to just `>` if closure is being passed as an argument to a function. How all these shortening works has been explained really well in [Apple Docs](https://developer.apple.com/library/mac/documentation/swift/conceptual/swift_programming_language/Closures.html). You will find details about concepts like **'Trailing Closure'** and **'Capturing'** explained in the documentation as well.

Now let's talk about Functions. We have already seen what a function looks like in Swift above, however if you have used Objective C, you may miss the named parameters while calling a function. Well don't worry functions in swift are quite flexible and powerful. Here are some points to remember regarding function parameters in Swift:

* We can prefix `#` to Parameter names to get expressive parameter names like Objective-C.
* For parameters with default values Swift automatically uses their names as external names without prefixing `#`.
* Parameter are constant by default, to make them variable prefix parameter name with `var`.

Again Apple has explained Functions quite well in it's [documentation](https://developer.apple.com/library/mac/documentation/swift/conceptual/swift_programming_language/Functions.html) so do check it out for detailed understanding. You may like to pay special attention to understand **In-out** and **Variadic** parameters.

Something which is really different and powerful regarding Swift Functions is that you can treat them as regular objects or types. You can assign them to vars and constants, pass them as parameters to other functions and even return a function from a function. Swift has taken these ideas from **'Functional Programming'** languages. Although [Swift is not completely functional](http://robnapier.net/swift-is-not-functional), it lets you use several Functional Programming concepts. To better understand Functional Programming with Swift you can check out this [Ray Wenderlich Tutorial](http://www.raywenderlich.com/82599/swift-functional-programming-tutorial) and consider buying [this book](http://www.objc.io/books/).