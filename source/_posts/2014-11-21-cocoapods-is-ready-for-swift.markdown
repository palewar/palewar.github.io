---
layout: post
title: "CocoaPods is ready for Swift"
date: 2014-11-21 18:38:10 +0530
comments: true
categories: [code, cocoapods, alamofire, swiftyjson]
---

{% img left /images/CocoaPods.png 100 100 %} When we work on a real project, we use many third-party libraries to make our lives easier. To use these libs, we first need to find them, download them and include them in our project. [CocoaPods](http://cocoapods.org/) lets us automate all this process and also handles dependency management for us. Check out this [post on NSHipster](http://nshipster.com/cocoapods/) for a very good intro. <!-- more -->

> CocoaPods is like [RubyGems](http://rubygems.org/) from the Ruby world and [NPM](https://www.npmjs.org/) from the Node.js world.

Using Cocoapods is really easy. You need to first install it by running `$ sudo gem install cocoapods` in Terminal. Then you need to create a `Podfile` in your project directory. A `Podfile` for including very popular [AFNetworking](https://github.com/AFNetworking/AFNetworking) lib will look like this:

``` ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '7.0'
pod 'AFNetworking', '~> 2.4'
``` 
And you are all set to use CocoaPods. You run `$ pod install` and you get an Xcode workspace file `.xcworkspace` created alongside your project file. From now on you need to always open and build project using workspace file instead of project file and you will be fine.

When Swift became available, iOS programmers wanted to use their much beloved CocoaPods to integrated with already existing ObjectiveC libraries and that was not really difficult, above steps work with Swift projects as well, you just need [a couple more steps](https://medium.com/@kirualex/cocoapods-with-swift-e6f8ba8f0afc) and you are done.

However soon some new and shiny libraries written in Swift came on the scene. My favorites being [Alamofire](http://nshipster.com/alamofire/) and [SwiftyJSON](https://github.com/SwiftyJSON/SwiftyJSON), but CocoaPods was not yet ready for Swift libs and people had to rely on using [alternative methods](http://git-scm.com/book/en/Git-Tools-Submodules) to use these libs. However [CocoaPods 0.36](https://github.com/CocoaPods/CocoaPods/milestones/0.36.0) is just around the corner and it will include support for Swift Pods.

While a public release is still some time away, you can use CocoaPods unreleased code to start integrating Swift libs in your projects right now. Just be cautious, that this is not fully tested code and treat it as a stopgap measure till 0.36 comes out. Ok so let's see what needs to be done:

* Create a file, called `Gemfile` in your project directory and just paste these lines in the file and save:

``` ruby
source 'https://rubygems.org'

gem 'cocoapods', :git => 'https://github.com/CocoaPods/CocoaPods.git', :branch => 'swift'
gem 'cocoapods-core', :git => 'https://github.com/CocoaPods/Core.git'
gem 'xcodeproj',  :git => 'https://github.com/CocoaPods/Xcodeproj.git'
gem 'claide', :git => 'https://github.com/CocoaPods/CLAide.git'
```  

* Run command `bundle install` 
* Create a `Podfile`. If you want to use Alamofire and SwiftyJSON in your project, your `Podfile`[^1] should look like this:

``` ruby
source 'https://github.com/CocoaPods/Specs.git'

platform :ios, '8.0'
pod 'SwiftyJSON', :git => "https://github.com/orta/SwiftyJSON", :branch => "podspec"
pod 'Alamofire', :git => "https://github.com/mrackwitz/Alamofire.git", :branch => "podspec"
```  

* Run `bundle exec pod install`[^2] and you are done. You get the workspace file which you need to use from now on.

Now you should be able to import Alamofire and SwiftyJSON in your project and use[^3] them.

Hope you liked this post. Connect via [Twitter](https://twitter.com/swiftwala) & [email](https://feedburner.google.com/fb/a/mailverify?uri=SwiftWala&amp;loc=en_US) for future updates. Thanks for reading.

[^1]: Each lib should have a [podspec](http://guides.cocoapods.org/making/specs-and-specs-repo.html) file to work with CocoaPods, since that's not the case right now, we are using forks of libs which contain a podspec file. This also means that if you want to use any other Swift lib with CocoaPods, you will need to fork it and create a podspec file for it yourself and then you will need to use path of your fork in the podfile.
[^2]: 'bundle exec' ensures that you are using Swift CocoaPods version from your Gemfile. Thanks [Brian](https://twitter.com/modocache) of [Quick](https://github.com/Quick/Quick#how-to-install-quick-using-beta-cocoapods) for the tip.
[^3]: Thanks [Ambas](https://www.facebook.com/ambaschobsanti) for the tip about CLAide.
