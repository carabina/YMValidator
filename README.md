# YMValidator

[![CI Status](http://img.shields.io/travis/YMonnier/YMValidator.svg?style=flat)](https://travis-ci.org/YMonnier/YMValidator)
[![Version](https://img.shields.io/cocoapods/v/YMValidator.svg?style=flat)](http://cocoapods.org/pods/YMValidator)
[![License](https://img.shields.io/cocoapods/l/YMValidator.svg?style=flat)](http://cocoapods.org/pods/YMValidator)
[![Platform](https://img.shields.io/cocoapods/p/YMValidator.svg?style=flat)](http://cocoapods.org/pods/YMValidator)
[![Swift 2.2](https://img.shields.io/badge/Swift-2.2-orange.svg?style=flat)](https://developer.apple.com/swift/)


TextField Validation library for Swift (@IBDesignable & Programmatically)

[Documentation](http://cocoadocs.org/docsets/YMValidator/0.1.0/index.html)

<img src="https://raw.githubusercontent.com/YMonnier/YMValidator/master/Resources/Example.gif" alt="alt text" width=280 height=475>

Usage
-----

First create your custom validator class.
The class has to have `@objc` declaration, conform to `YMRulesValidator` protocol and `NSObject` .

``` Swift
@objc(EmailValidator)
class EmailValidator: NSObject, YMRulesValidator {
  var regex: String = "[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,}"
}
```


##### With Storyboard

1. Add your TextField
2. Set the **custom class** `YMValidator`
3. On **attributs inspector**, set `Class Name` and `Error Message`

![CustomClass](https://raw.githubusercontent.com/YMonnier/YMValidator/master/Resources/CustomClass.png)
![Inspector](https://raw.githubusercontent.com/YMonnier/YMValidator/master/Resources/Inspector.png)

4. Set the error label to `YMValidator`
``` Swift
@IBOutlet weak var errorEmailLabel: UILabel!
@IBOutlet weak var inputEmail: YMValidator!

override func viewDidLoad() {
    super.viewDidLoad()
    self.errorEmailLabel.text = ""    
    self.inputEmail.setErrorLabel(self.errorEmailLabel)
}
```

##### Programmatically

``` Swift
//ViewController.swift
let textField = YMValidator(frame: CGRect(x: 30.0, y: 296.0, width: 540, height: 30), rulesValidator: CustomValidator(), errorMessage: "Only alphanumeric characters are allowed", errorLabel: customErrorLabel)
self.view.addSubview(textField)
```

##### Finally
You can check if all inputs are valid with this static function.

```
YMValidator.areValid(self)
```

Example
-------
To run the example project, clone the repo, and run `pod install` from the Example directory first.


Installation
------------
###### Requirements

 * iOS 8.0+
 * Xcode 7 (Swift 2.2)

##### Cocoapods

YMValidator is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "YMValidator"
```

##### Manually
Drag and drop `YMValidator.swift` into your Project.

Author
------------
[@YMonnier](https://github.com/YMonnier) - contact@yseemonnier.com



Contributing
------------
We are open to any proposals to **improve** this library!!

The best way to contribute is by submitting a pull request(Add comments in your code before to it). We'll do our best to respond to your patch as soon as possible. You can also submit a new GitHub issue if you find bugs or have questions. :octocat:

License
-------
YMValidator is available under the MIT license. See the [LICENSE](https://github.com/YMonnier/ProBill/blob/master/LICENSE) file for more info.
