[![Build Status](https://travis-ci.org/Jerry0523/Intent.svg?branch=master)](https://travis-ci.org/Jerry0523/Intent)
[![CocoaPods Compatible](https://img.shields.io/cocoapods/v/Intent.svg)](https://img.shields.io/cocoapods/v/Intent.svg)

A solution for iOS modules and components separation. You can route to viewController or perform native block with url.

Features
-------

### Register LoginViewController as follow

```swift
Router.defaultCtx.register(LoginViewController.self, forPath: "test.com/login")

```

### Register closure as follow

```swift
Handler.defaultCtx.register({ (input) in
    print(input)
}, forPath: "test.com/showAlert?title=Hello World")

```

### Route to LoginViewController by a router key

```swift
try? Router(path: "test.com/login")
        .input(["stringValue": "This message came from a router"])
        .submit()

```

### Route to LoginViewController with a custom transition

```swift
try? Router(path: "test.com/login")
        .input(["stringValue": "This message came from a router"])
        .transition(SystemTransition(axis: .horizontal, style: .zoom(factor: 0.8)))
        .submit()

```

### Route to LoginViewController with a custom config

```swift
try? Router(key: "test.com/login")
        .input(["stringValue": "This message came from a router"])
        .config(.present([.fakePush, .wrapNC]))
        .transition(SystemTransition(axis: .horizontal, style: .zoom(factor: 0.8)))
        .submit()

```
### Currently, we support

- Present
- Push
- Switch
- Modal
- Child

### Route to LoginViewController by a remote URL

```swift
try? Router(urlString: "router://test.com/login?stringValue=This message came from a url string")
        .submit()

```

## Installation with CocoaPods

[CocoaPods](http://cocoapods.org) is a dependency manager for Objective-C, which automates and simplifies the process of using 3rd-party libraries. You can install it with the following command:

```bash
$ gem install cocoapods
```
#### Podfile

To integrate Intent into your Xcode project using CocoaPods, specify it in your `Podfile`:

```ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'

pod 'Intent'
```

Then, run the following command:

```bash
$ pod install
```

License
-------
(MIT license)
