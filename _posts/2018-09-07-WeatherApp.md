---
layout: post
title: "WeatherApp"
date: 2018-09-07 01:26:40
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

## To get a user's current location you need to declare and use in :
```
//
//  ViewController.swift
//  WeatherApp
//
//  Created by Himanshu on 11/05/2018.
//  Copyright (c) 2018 Inspire Infotech Pvt Ltd. All rights reserved.

import UIKit
import CoreLocation
import Alamofire
import SwiftyJSON


class WeatherViewController: UIViewController ,CLLocationManagerDelegate {
    
    //Constants
    let WEATHER_URL = "http://api.openweathermap.org/data/2.5/weather"
    let APP_ID = "e72ca729af228beabd5d20e3b7749713"
    
    //TODO: Declare instance variables here
    
    //Pre-linked IBOutlets
    @IBOutlet weak var weatherIcon: UIImageView!
    @IBOutlet weak var cityLabel: UILabel!
    @IBOutlet weak var temperatureLabel: UILabel!

    let locationManager = CLLocationManager()
    let weatherDataModel = WeatherDataModel()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        
        //self.locationManager.requestAlwaysAuthorization()
        
        // For use in foreground
        self.locationManager.requestWhenInUseAuthorization()
        
        if CLLocationManager.locationServicesEnabled() {
            locationManager.delegate = self
            locationManager.desiredAccuracy = kCLLocationAccuracyNearestTenMeters
            locationManager.startUpdatingLocation()
        }
    }
    
    
    func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        guard let locValue: CLLocationCoordinate2D = manager.location?.coordinate else { return }
        //print("locations = \(locValue.latitude) \(locValue.longitude)")
        
        print(locValue.latitude)
        print(locValue.longitude)
       let latitude = String(locValue.latitude)
        let longitude = String(locValue.longitude)
        
        let parms: [String : String] = ["lat" : latitude, "lon" : longitude, "appid" : APP_ID]
        
      getWeatherData(url: WEATHER_URL, parameter: parms)
        //mapView1.setRegion(viewRegion, animated: false)
        
        // self.map.setRegion(UIRegion, animated: true)
        //return (locValue.latitude)
    }
    
    
    
    //MARK: - Networking
    /***************************************************************/
    
    //Write the getWeatherData method here:
    
    func getWeatherData(url : String,parameter : [String: String]) {
        Alamofire.request(url, method: .get, parameters: parameter).responseJSON{
                response in
                if response.result.isSuccess{
                    let weatherJSON : JSON = JSON(response.result.value!)
                    print(weatherJSON)
                    self.updateWeth(json: weatherJSON)
                }
                else{
                    print("Error")
                }
        }
    }
    
    
    //MARK: - JSON Parsing
    /***************************************************************/
    
    //Write the updateWeatherData method here:
    func updateWeth(json : JSON)
    {
        let temp = json["main"]["temp"].doubleValue
        
        weatherDataModel.temp = Int(temp - 273.15)
        weatherDataModel.city = json["name"].stringValue
        weatherDataModel.cond = json["weather"][0]["id"].intValue
        weatherDataModel.weatherIconName = weatherDataModel.updateWeatherIcon(condition: weatherDataModel.cond)
        updateUIWithWeatherData()
    }
    
    
    //MARK: - UI Updates
    /***************************************************************/

    //Write the updateUIWithWeatherData method here:
    
    func updateUIWithWeatherData()
    {
        cityLabel.text = weatherDataModel.city
        temperatureLabel.text = "\(weatherDataModel.temp)"
        weatherIcon.image = UIImage(named: weatherDataModel.weatherIconName)
    }
    

    
    //MARK: - Location Manager Delegate Methods
    /***************************************************************/
    
    //Write the didUpdateLocations method here:

    
    //Write the didFailWithError method here:
    
   
    
    //MARK: - Change City Delegate methods
    /***************************************************************/
    
    
    //Write the userEnteredANewCityName Delegate method here:
    

    
    //Write the PrepareForSegue Method here

}





````


### In the info.plist.
```
<key>NSAppTransportSecurity</key>
	<dict>
		<key>NSExceptionDomains</key>
		<dict>
			<key>openweathermap.org</key>
			<dict>
				<key>NSIncludesSubdomains</key>
				<true/>
				<key>NSTemporaryExceptionAllowsInsecureHTTPLoads</key>
				<true/>
			</dict>
		</dict>
	</dict>
```


Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
