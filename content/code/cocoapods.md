+++
categories = ["code"]
draft = false
date = "2017-03-20T20:26:14+01:00"
showpagemeta = true
tags = ["cocoapods", "swift", "objective-c"]
slug = ""
title = "Cocoapods"
description = "A list of pod and some tips to use during development"
comments = true
showcomments = true

+++

### Installation

Last version
```
sudo gem install cocoapods -n/usr/local/bin
```

Pre release version
```
sudo gem install cocoapods --pre -n/usr/local/bin
```

### Best Pods

A list of useful pod and common issue with Cocoapods

##### Model - Database

* [Mantle](https://github.com/Mantle/Mantle) [Obj-C]
* [Realm](https://github.com/realm/realm-cocoa) [Obj-C, Swift, Java]
 
##### Networking
* [AFNetworking](https://github.com/realm/realm-cocoa) [Obj-C]
* [Alamofire](https://github.com/Alamofire/Alamofire) [Swift]
* [AlamofireImage](https://github.com/Alamofire/AlamofireImage) [Swift]

##### Menu - PagedView - TableView 
* [SWRevealViewController](https://github.com/John-Lluch/SWRevealViewController) [Obj-C]
* [RESideMenu](https://github.com/romaonthego/RESideMenu) [Obj-C]
* [PagingMenuController](https://github.com/kitasuke/PagingMenuController) [Swift]
* [DZNEmptyDataSet](https://github.com/dzenbot/DZNEmptyDataSet) [Obj-C]
* [SWTableViewCell](https://github.com/CEWendel/SWTableViewCell) [Obj-C]

##### Form & Charts 
* [XLForm](https://github.com/xmartlabs/XLForm) [Obj-C]
* [Eureka](https://github.com/xmartlabs/Eureka) (XLForm Swift Version) [Swift]
* [iOS-Charts](https://github.com/danielgindi/ios-charts) Port of MPAndroidChart [Swift]

#### Logger
* [SwiftyBeaver](https://github.com/SwiftyBeaver/SwiftyBeaver) SwiftyBeaver [Swift]


## Podfile example

```
# Pod configuration
platform :ios, "8.0"
use_frameworks! # for Swift project

def import_pods
    
    #Core libraries
    pod 'CocoaLumberjack'
    pod 'AFNetworking', '~> 2.6.0'
    
    #Object serializer
    pod 'Mantle', '~> 2.0'
    
    #Mobile Database
    pod 'Realm', '~> 0.95'
    
    #Table view swipe cell and table view empty view
    pod 'SWTableViewCell', '~> 0.3'
    pod 'DZNEmptyDataSet'
    
    #Autolayout helper
    pod 'Masonry', '~> 0.6'
    
    #Detect Urls, #, @ and regex patterns on UILabel
    #pod 'ResponsiveLabel', '~> 1.0.3'
    pod 'TTTAttributedLabel', '~> 1.13'
    
    #Collection of NSFormatter subclasses for colors, time, location and phone number
    pod 'FormatterKit'
    
    #Pull to refresh for table view and collection view
    pod 'INSPullToRefresh', '~> 1.0'

   ...
    
    #For development pod
    #pod "LocalPod", :path => "development pod path"
    
end

target 'AppTarget' do
    
    import_pods
    
end

target 'AppTargetTests' do
    
    import_pods
    
end
```

## Create a Pod
Run  ```pod lib create PodName``` command to create the default template for a Pod. The setup process ask some question about the pod configuration. For more information  [Getting started](https://guides.cocoapods.org/making/using-pod-lib-create).

To learn more about the template see [Pod Template](https://github.com/CocoaPods/pod-template.git) .
To learn more about creating a new pod, see [Making a Cocoapods](http://guides.cocoapods.org/making/making-a-cocoapod).

#### The Podspec
A Podspec, or Spec, describes a version of a Pod library. One Pod, over the course of time, will have many Specs. It includes details about where the source should be fetched from, what files to use, the build settings to apply, and other general metadata such as its name, version, and description.

* [Podspec Syntax Reference](https://guides.cocoapods.org/syntax/podspec.html)

After the Podspec creation run ```pod spec lint``` to check configuration errors:


#### Release and update a Pod

Once you have a release ready you'll need to make the corresponding tag. First run a quick ```pod lib lint``` then create your tag and push it.

```
$ cd ~/code/Pods/NAME
$ edit NAME.podspec
# set the new version to 0.0.1
# set the new tag to 0.0.1
$ pod lib lint

$ git add -A && git commit -m "Release 0.0.1."
$ git tag '0.0.1'
$ git push --tags
``` 


First of all, you have to register your device to **pod trunk** with this command:

 ```
pod trunk register mario.red@cocoapods.org 'Mario Red' --description='macbook air'
  ```
  
 Then validate your pod with:
 
  ```
 pod lib lint NAME.podspec
  ```
 Now send you pod to Cocoapods:
 
 ```
 pod trunk push NAME.podspec
 ```
 
 
## Common Cocoapods Issue
A list of common issue 

#### Overrides FRAMEWORK_SEARCH_PATHS
```
 [!] The `AppTests [Debug]` target overrides the `FRAMEWORK_SEARCH_PATHS` build setting defined in `Pods/Target Support Files/Pods-SlhashTests/Pods-SlhashTests.debug.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
```

**Solution:** a `“$(inherited)”` to _FRAMEWORK_SEARCH_PATHS_ (App target => Build Settings Tab => Search for “Framework Search Path”

#### undefined symbols for architecture arm64

After `pod update` undefined symbols for architecture arm64

**Solution**: Adding `$(OTHER_LDFLAGS)` to the App target under  _"Other Linker Flags"_ got me through this

#### Overrides EMBEDDED_CONTENT_CONTAINS_SWIFT
```
[!] The `App [Debug]` target overrides the `EMBEDDED_CONTENT_CONTAINS_SWIFT` build setting defined in `Pods/Target Support Files/Pods-App-Quotes.debug.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
```

**Solution:** Search for `“EMBEDDED_CONTENT_CONTAINS_SWIFT` on App build settings. Press the delete key on the item. (the item will change from bold to regular text)

