---
layout: post
title: "Using Alamofire in Xcode"
date: 2018-09-06 12:26:40
image: '/assets/img/swift.jpg'
description: About Using Alamofire in Xcode Documentation
category: 'Beginners'
tags:
- Swift
- Location
- Maps


introduction: User's Current Location and Coordinates Documentation
---


## Code

### Open Terminal and Type 
```
sudo gem install cocoapods
```
### Change Directory 
```
cd projectpath
```

### Create Xcode project and set directory of project in terminal
```
pod init
```
### open Podfile
```
nano Podfile
```
```

platform :ios, '9.0'

target 'Clima' do
  # Comment the next line if you're not using Swift and don't want to use dynamic frameworks
  use_frameworks!
    pod 'Alamofire'
    pod 'SwiftyJSON'
  # Pods for Clima
 

end
```
```
ctrl+x
Yes
Enter
```

### Install third party lib's
```
pod install
```

### Open projectname.workspace file

Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
