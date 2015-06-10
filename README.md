<img src="https://raw.githubusercontent.com/thoughtbot/Runes/gh-pages/Logo.png" width="200" />

Indecipherable symbols that some people claim have actual meaning.

[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)

## Framework Installation ##

### [Carthage] ###

[Carthage]: https://github.com/Carthage/Carthage

```
github "thoughtbot/runes"
```

Then run `carthage update`.

Follow the current instructions in [Carthage's README][carthage-installation]
for up to date installation instructions.

[carthage-installation]: https://github.com/Carthage/Carthage#adding-frameworks-to-an-application

### [CocoaPods] ###

[CocoaPods]: http://cocoapods.org

Add the following to your [Podfile](http://guides.cocoapods.org/using/the-podfile.html):

```ruby
pod 'Runes'
```

You will also need to make sure you're opting into using frameworks:

```ruby
use_frameworks!
```

Then run `pod install` with CocoaPods 0.36 or newer.

## Adding Runes as a Framework Dependency ##

Runes can also be used as a low-overhead dependency for defining these
operators for your own types. After linking to `Runes.swift`, you will be able
to define implementations for your types, and your users will be able to just
import your framework to use these operators.

### [Carthage] ###

```
github "thoughtbot/runes"
```

Then run `carthage update`. Once you've checked out the required version, you
can link `Carthage/Checkouts/Runes/Source/Runes.swift` directly into your
framework.

### [CocoaPods] ###

First, you will need to make sure that Runes is added as a submodule for your
repo. Then, you'll need to make sure to enable submodule support for your
source directive:

```ruby
s.source = { :git => "https://github.com/thoughtbot/Argo", :tag => "v#{s.version}", :submodules => true }
```

Then, you can add `Runes.swift` as a source file:

```ruby
spec.source_files = 'Argo/**/*.{h,swift}', 'Carthage/Checkouts/Runes/Source/Runes.swift'
```

## What's included? ##

Importing Runes introduces 3 new operators and one global function:

- `<^>` (pronounced "map")
- `<*>` (pronounced "apply")
- `>>-` (pronounced "flatMap") (left associative)
- `-<<` (pronounced "flatMap") (right associative)
- `pure` (pronounced "pure")

We also include default implementations for Optional and Array with the
following type signatures:

```swift
// Optional:
public func <^><T, U>(f: T -> U, a: T?) -> U?
public func <*><T, U>(f: (T -> U)?, a: T?) -> U?
public func >>-<T, U>(a: T?, f: T -> U?) -> U?
public func -<<<T, U>(f: T -> U?, a: T?) -> U?
public func pure<T>(a: T) -> T?

// Array:
public func <^><T, U>(f: T -> U, a: [T]) -> [U]
public func <*><T, U>(fs: [T -> U], a: [T]) -> [U]
public func >>-<T, U>(a: [T], f: T -> [U]) -> [U]
public func -<<<T, U>(f: T -> [U], a: [T]) -> [U]
public func pure<T>(a: T) -> [T]
```

Contributing
------------

See the [CONTRIBUTING] document. Thank you, [contributors]!

[CONTRIBUTING]: CONTRIBUTING.md
[contributors]: https://github.com/thoughtbot/Runes/graphs/contributors

Need Help?
----------

We offer 1-on-1 coaching. We can help you with functional programming in Swift,
get started writing unit tests, and convert from Objective-C to Swift.
[Get in touch].

[Get in touch]: http://coaching.thoughtbot.com/ios/?utm_source=github

License
-------

Runes is Copyright (c) 2015 thoughtbot, inc. It is free software, and may be
redistributed under the terms specified in the [LICENSE] file.

[LICENSE]: /LICENSE

About
-----

![thoughtbot](https://thoughtbot.com/logo.png)

Runes is maintained and funded by thoughtbot, inc. The names and logos for
thoughtbot are trademarks of thoughtbot, inc.

We love open source software! See [our other projects][community] or look at
our product [case studies] and [hire us][hire] to help build your iOS app.

[community]: https://thoughtbot.com/community?utm_source=github
[case studies]: https://thoughtbot.com/ios?utm_source=github
[hire]: https://thoughtbot.com/hire-us?utm_source=github
