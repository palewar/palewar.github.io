---
layout: post
title: "Enum=Struct=Class"
date: 2014-10-10 16:07:43 +0530
comments: true
categories: theory 
---
I have used enums, structs and classes in other languages before, but never thought that I will ever be comparing them,[^1] as they always seemed to be completely different programming concepts in other languages. Well Swift is different, it has supercharged enums and structs so much so that it may seem overwhelming and outright confusing to not-so-pro programmers like me.

Ok, brace yourself. Here it comes - **Both enums and structs can have properties and methods like classes.** <!-- more -->What?? That was exactly my reaction. This new concept was so alien to me that my head started spinning and I gave up on reading and understanding these concepts in detail in the [Swift Book](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/ClassesAndStructures.html#//apple_ref/doc/uid/TP40014097-CH13-XID_135). So a few days passed and I was just checking out how many [Swift Repos](https://github.com/trending?l=swift&since=monthly) are there on Github, and I came across [swift-json](https://github.com/dankogai/swift-json) by [Dan Kogai](http://en.wikipedia.org/wiki/Dan_Kogai). While [explaining](https://github.com/dankogai/swift-json/wiki/Discussion) his approach, Dan drops some pearls of wisdom:

> Some thing must be copied by value and that's what struct is for. In swifts primitives are struct that happens to fit in the register. So is enum, which is really a union in disguise. And as with C and friends enums are also copied by value.

I read and re-read these 2 lines again and again so that I can really make complete sense of these lines. So the key takeaway from this post should be that **enums and structs are value types, whereas classes are reference types**. This key difference gives us the reason to use Structs and Classes in different scenarios.

I am probably not the best person to explain these different scenarios myself here, so I would just point you to an [excellent blog post](http://www.objc.io/issue-16/swift-classes-vs-structs.html) on this same topic. Go through that post and you will feel becoming a little more wiser than before. Also last but not the least, [Swift Book](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/ClassesAndStructures.html#//apple_ref/doc/uid/TP40014097-CH13-XID_135) actually explains these concepts quite clearly and in detail, so you should definitely read it to gain an indepth understanding of these concepts.

My intention was just to really smoothen-up the road ahead :-)

[^1]: I am sorry for a misleading title for this post, but couldn't think of anything better. This post is about similarities and differences between Enumeration, Structure and Class and yes before you point out, I know that I should have used '==' instead of '=', but hey title doesn't have to be syntactically correct, right?