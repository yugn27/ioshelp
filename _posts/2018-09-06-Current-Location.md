---
layout: post
title: "User's Current Location and Coordinates"
date: 2018-09-06 12:26:40
image: 'https://blog.tomasmahrik.com/wp-content/uploads/2015/06/swift.jpg'
description: About User's Current Location and Coordinates Documentation
category: 'Beginners'
tags:
- Swift
- Location
- Maps

introduction: User's Current Location and Coordinates Documentation
---


## Code

Import MapKit + CoreLocation

adding CLLocationManagerDelegate in the class definition.

## To get a user's current location you need to declare:
```
let locationManager = CLLocationManager()

````
## In viewDidLoad() you have to instanitate the CLLocationManager class, like this:
```
// Ask for Authorisation from the User.
self.locationManager.requestAlwaysAuthorization() 

// For use in foreground
self.locationManager.requestWhenInUseAuthorization()

if CLLocationManager.locationServicesEnabled() {
    locationManager.delegate = self
    locationManager.desiredAccuracy = kCLLocationAccuracyNearestTenMeters
    locationManager.startUpdatingLocation()
}

```
## Then in CLLocationManagerDelegate method you can get user's current location coordinates:
```
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    guard let locValue: CLLocationCoordinate2D = manager.location?.coordinate else { return }
    print("locations = \(locValue.latitude) \(locValue.longitude)")
}
```

### In the info.plist you will have to add Privacy - Location Always Usage Description and your custom alert message like, AppName(Demo App) would like to use your current location.


Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
