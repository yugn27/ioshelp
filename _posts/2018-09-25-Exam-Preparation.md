---
layout: post
title: "Exam"
date: 2018-09-25 12:26:40
image: '/assets/img/swift.jpg'
description: Exams
category: 'Beginners'
tags:
- Swift



introduction: Exams
---

# Exam #2
Facts
- Multitasking for iOS was first released in June 2010 along with the release of iOS 4.
- Dec 3, 2015 Swift Open Source.
- 12.0 is stable iOS version (Sep 17, 2018)
- Xcode 10 is latest IDE for Apple dev
- macOS High Sierra 10.13
- macOS Mojave 10.14


### Swift
Swift is a general-purpose, multi-paradigm, compiled programming language developed by Apple Inc. for iOS, macOS, watchOS, tvOS, and Linux. Swift is designed to work with Apple's Cocoa and Cocoa Touch frameworks and the large body of existing Objective-C code written for Apple products. It is built with the open source LLVM compiler framework and has been included in Xcode since version 6. On platforms other than Linux,[10] it uses the Objective-C runtime library which allows C, Objective-C, C++ and Swift code to run within one program.[11]

Apple intended Swift to support many core concepts associated with Objective-C, notably dynamic dispatch, widespread late binding, extensible programming and similar features, but in a "safer" way, making it easier to catch software bugs; Swift has features addressing some common programming errors like null pointer dereferencing and provides syntactic sugar to help avoid the pyramid of doom. Swift supports the concept of protocol extensibility, an extensibility system that can be applied to types, structs and classes, which Apple promotes as a real change in programming paradigms they term "protocol-oriented programming"[12] (similar to traits).[13]

Swift was introduced at Apple's 2014 Worldwide Developers Conference (WWDC).[14] It underwent an upgrade to version 1.2 during 2014 and a more major upgrade to Swift 2 at WWDC 2015. Initially a proprietary language, version 2.2 was made open-source software under the Apache License 2.0 on December 3, 2015, for Apple's platforms and Linux.[15][16]

In March 2017, Swift made the top 10 in the monthly TIOBE index ranking of popular programming languages,[17] and was ranked 11th at the end of 2017.[18] By October 2017, however, Swift had begun to lose momentum in the TIOBE index as mobile development moved toward Xamarin and C#, as well as similar tools for JavaScript.[19] As of April 2018, Swift ranked No. 15 at 1.53% share, losing 0.75% from its 2.28% share just one year earlier.[20]

Different major versions have been released at an annual schedule with incompatible syntax and library invocations each, requiring significant source code rewrites. For larger code bases this has caused many developers to dismiss Swift [21] until a more stable version becomes available.


### History
Development of Swift started in July 2010 by Chris Lattner, with the eventual collaboration of many other programmers at Apple. Swift took language ideas "from Objective-C, Rust, Haskell, Ruby, Python, C#, CLU, and far too many others to list".[7] On June 2, 2014, the Apple Worldwide Developers Conference (WWDC) application became the first publicly released app written with Swift.[22] A beta version of the programming language was released to registered Apple developers at the conference, but the company did not promise that the final version of Swift would be source code compatible with the test version. Apple planned to make source code converters available if needed for the full release.[22]




### Version History
Date	Version
2014-09-09	Swift 1.0
2014-10-22	Swift 1.1
2015-04-08	Swift 1.2
2015-09-21	Swift 2.0
2016-09-13	Swift 3.0
2017-09-19	Swift 4.0
2018-03-29	Swift 4.1
2018-09-17	Swift 4.2

### Cocoa
Cocoa is Apple's native object-oriented application programming interface (API) for their operating system macOS.

For iOS, tvOS, and watchOS, a similar API exists, named Cocoa Touch, which includes gesture recognition, animation, and a different set of graphical control elements. It is used in applications for Apple devices such as iPhone, iPad, iPod touch, Apple TV, and Apple Watch.

Cocoa consists of the Foundation Kit, Application Kit, and Core Data frameworks, as included by the Cocoa.h header file, and the libraries and frameworks included by those, such as the C standard library and the Objective-C runtime.[1]

Cocoa applications are typically developed using the development tools provided by Apple, specifically Xcode (formerly Project Builder) and Interface Builder (now part of Xcode), using the languages Objective-C or Swift. However, the Cocoa programming environment can be accessed using other tools, such as Clozure CL, LispWorks, Object Pascal, Python, Perl, Ruby, and AppleScript with the aid of bridge mechanisms such as PasCocoa, PyObjC, CamelBones, RubyCocoa, and a D/Objective-C Bridge. A Ruby language implementation named MacRuby, which removes the need for a bridge mechanism, was formerly developed by Apple, while Nu is a Lisp-like language that can be used with Cocoa with no bridge. It is also possible to write Objective-C Cocoa programs in a simple text editor and build it manually with GNU Compiler Collection (GCC) or clang from the command line or from a makefile.

For end-users, Cocoa applications are those written using the Cocoa programming environment. Such applications usually have a distinctive feel, since the Cocoa programming environment automates many aspects of an application to comply with Apple's human interface guidelines.


### Cocoa Touch
Cocoa Touch is a UI framework for building software programs to run on iOS for the iPhone, iPod Touch, and iPad, watchOS for the Apple Watch, and tvOS for the fourth-generation Apple TV, from Apple Inc.

Cocoa Touch provides an abstraction layer of iOS, the operating system for the iPhone, iPod Touch, and iPad. Cocoa Touch is based on the macOS Cocoa API toolset and, like it, is primarily written in the Objective-C language. Cocoa Touch allows the use of hardware and features that are not found in macOS computers and are thus unique to the iOS range of devices. Just like Cocoa, Cocoa Touch follows a Model-View-Controller (MVC) software architecture.

Cocoa Touch contains a different set of graphical control elements to Cocoa. Tools for developing applications based on Cocoa Touch are included in the iOS SDK.


### Model–view–controller(MVC)
Model–view–controller is an architectural pattern commonly used for developing user interfaces that divides an application into three interconnected parts. This is done to separate internal representations of information from the ways information is presented to and accepted from the user.[1][2] The MVC design pattern decouples these major components allowing for efficient code reuse and parallel development.

Traditionally used for desktop graphical user interfaces (GUIs), this architecture has become popular for designing web applications and even mobile, desktop and other clients.[3] Popular programming languages like Java, C#, Ruby, PHP have MVC frameworks that are used in web application development straight out of the box.

### What are the delegate methods of UITableview?
tableView(_:viewForHeaderInSection:)
tableView(_:viewForFooterInSection:)
tableView(_:heightForHeaderInSection:)
tableView(_:heightForFooterInSection:)
tableView(_:willSelectRowAt:)
tableView(_:didSelectRowAt:)
tableView(_:willDeselectRowAt:)
tableView(_:didDeselectRowAt:)


Setup the delegate
```
  self.tableview.delegate = self
```

Most of the other part is pretty boilerplate code where we need to implement the numberOfRowsInSection and cellForRowAtIndexPath.
```
//
//  TableViewController.swift
//  Tableviewc
//
//  Created by yashn on 26/09/18.
//  Copyright © 2018 yashn. All rights reserved.
//

import UIKit

class MainViewController: UIViewController, UITableViewDataSource, UITableViewDelegate {

    @IBOutlet weak var tableView: UITableView!
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        self.tableView.delegate = self
        self.tableView.dataSource = self
        self.workouts = manager.getWorkOuts()
    }
    
    func tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return self.workouts.count
    }

    func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
        
        let workout = self.workouts[indexPath.row] as? Workout
        let cell = tableView.dequeueReusableCellWithIdentifier("Cell") as? WorkoutCell!
        cell!.textCell?.text = workout?.title
        cell!.backgroundColor = workout?.color
        cell!.countLabel.text = "\(indexPath.row+1)"
        cell!.selectionStyle = UITableViewCellSelectionStyle.None
        return cell!
    }    
}
```
### What are the delegate methods of MapkitUI?

Step 1:
First we import MapKit as well as CoreLocation. The reason we need to implement CoreLocation is so that we can use it to request authorisation for using the users location.

```
import MapKit
import CoreLocation
```

Create a property for a CLLocationManager as follows (which can be put just below the mapView IBOutlet):

```

let locationManager = CLLocationManager()
```

In viewDidLoad add the following:

```
 override func viewDidLoad() {
        super.viewDidLoad()
        
        self.locationManager.requestWhenInUseAuthorization()
        
        if CLLocationManager.locationServicesEnabled() {
            locationManager.delegate = self
            locationManager.desiredAccuracy = kCLLocationAccuracyNearestTenMeters
            locationManager.startUpdatingLocation()
        }
    }
    
    func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        guard let locValue: CLLocationCoordinate2D = manager.location?.coordinate else { return }
       
       let latitude = String(locValue.latitude)
        let longitude = String(locValue.longitude)
    }
```



Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
