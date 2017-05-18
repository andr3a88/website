+++
categories = ["code"]
date = "2017-03-19T20:36:20+01:00"
slug = ""
draft = false
title = "Objective-C Coding Style"
description = "My code convention for Objective-C"
showpagemeta = true
tags = ["iosdev", "objective-c", "codestyle"]
showcomments = true
comments = true

+++ 

My code convention for Objective-C inspired by [Sources](#sources)

## Table of Contents

* [Code Organization](code/objc-codestyle/#code-organization)
* [Spacing](code/objc-codestyle/#spacing)
* [Conditionals](code/objc-codestyle/#conditionals)
* [Ternary Operator](code/objc-codestyle/#ternary-operator)
* [Methods](code/objc-codestyle/#methods)
* [Variables](code/objc-codestyle/#variables)
* [Naming](code/objc-codestyle/#naming)
* [Comments](code/objc-codestyle/#comments)
* [Constants](code/objc-codestyle/#constants)
* [Singletons](code/objc-codestyle/#singletons)
* [Sources](code/objc-codestyle/#sources)

## Code Organization

Use `#pragma mark -` to categorize methods in functional groupings.

```objc
#pragma mark - Lifecycle

- (instancetype)init {}
- (void)viewDidLoad {}
- (void)viewWillAppear:(BOOL)animated {}
- (void)didReceiveMemoryWarning {}

#pragma mark - Custom Accessors

- (void)setCustomProperty:(id)value {}
- (id)customProperty {}

#pragma mark - Public

- (void)publicMethod {}

#pragma mark - Private

- (void)privateMethod {}

#pragma mark - Protocol conformance
#pragma mark - UITextFieldDelegate
#pragma mark - UITableViewDataSource
#pragma mark - UITableViewDelegate

#pragma mark - IBActions

- (IBAction)submitData:(id)sender {}
```

## Spacing

* Indent using tabs. Be sure to set this preference in Xcode.
* Method braces and other braces (`if`/`else`/`switch`/`while` etc.) always open on the same line as the statement but close on a new line.

**For example:**
```objc
if(user.isHappy) {
    // Do something
}
else {
    // Do something else
}
```
* There should be exactly one blank line between methods to aid in visual clarity and organization.
* Whitespace within methods should be used to separate functionality (though often this can indicate an opportunity to split the method into several, smaller methods). In methods with long or verbose names, a single line of whitespace may be used to provide visual separation before the method’s body.
* `@synthesize` and `@dynamic` should each be declared on new lines in the implementation.

## Conditionals

**For example:**
```objc
if (!error) {
    return success;
}
```
**Not:**
```objc
if (!error)
    return success;
```
**or:**
```objc
if (!error) return success;
```
## Ternary Operator
The Ternary operator, **?** , should only be used when it increases clarity or code neatness, only with a single condition.

**For example:** 
```objc
result = a > b ? x : y;
```
**Not:**
```objc
result = a > b ? x = c > d ? c : d : y;
```

## Methods

In method signatures, there should be a space after the scope (-/+ symbol). There should be a space between the method segments.

**For example:** 
```objc
- (void)setExampleText:(NSString *)text image:(UIImage *)image;
```
The beginning bracket should be in the same line of the method signature

**For example:** 
```objc
- (void)setExampleText:(NSString *)text image:(UIImage *)image {    
    // Code...
}
```

## Variables

TO-DO

## Naming

TO-DO

## Comments

TO-DO

## Constants

TO-DO

## Singletons

Singleton objects should use a thread-safe pattern for creating their shared instance.

```objc
+ (instancetype)sharedInstance 
{
   static id sharedInstance = nil;

   static dispatch_once_t onceToken;
   dispatch_once(&onceToken, ^{
      sharedInstance = [[self alloc] init];
   });

   return sharedInstance;
}
```

## Sources
This guide has been built taking inspiration from the following sources:

* [GitHub](https://github.com/github/objective-c-style-guide)
* [Realm-Cocoa](https://github.com/realm/realm-cocoa/wiki/Objective-C-Style-Guide)
* [New York Times](https://github.com/NYTimes/objective-c-style-guide) 
* [Raywenderlich](https://github.com/raywenderlich/objective-c-style-guide)
