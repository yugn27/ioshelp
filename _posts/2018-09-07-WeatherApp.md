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
l//
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
        getWeather()
        
    }
    
    
    func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        guard let locValue: CLLocationCoordinate2D = manager.location?.coordinate else { return }
        //print("locations = \(locValue.latitude) \(locValue.longitude)")
        
        print(locValue.latitude)
        print(locValue.longitude)
        let latitude = String(locValue.latitude)
        let longitude = String(locValue.longitude)
        
        let parms: [String : String] = ["lat" : latitude, "lon" : longitude, "appid" : APP_ID]
        
      getWeather()
        
        //mapView1.setRegion(viewRegion, animated: false)
        
        // self.map.setRegion(UIRegion, animated: true)
        //return (locValue.latitude)
        
    }
    
    
    
    //MARK: - Networking
    /***************************************************************/
    
    //Write the getWeatherData method here:
    

    
    
    
    
    
    //MARK: - JSON Parsing
    /***************************************************************/
   
    
    //Write the updateWeatherData method here:
    

    
    
    
    //MARK: - UI Updates
    /***************************************************************/
    
    
    //Write the updateUIWithWeatherData method here:
    
    
    
    
    
    
    //MARK: - Location Manager Delegate Methods
    /***************************************************************/
    
    
    //Write the didUpdateLocations method here:
    
    
    
    //Write the didFailWithError method here:
    
    
    

    
    //MARK: - Change City Delegate methods
    /***************************************************************/
    
    
    //Write the userEnteredANewCityName Delegate method here:
    

    
    //Write the PrepareForSegue Method here
    
    var main: Int = 0
    
    func getWeather() {
        guard let url = URL(string: "https://samples.openweathermap.org/data/2.5/weather?q=Nagpur,uk&appid=b6907d289e10d714a6e88b30761fae22") else {return}
        let task = URLSession.shared.dataTask(with: url) { (data, response, error) in
            guard let dataResponse = data,
                error == nil else {
                    print(error?.localizedDescription ?? "Response Error")
                    return }
            do{
                //here dataResponse received from a network request
                let jsonResponse = try JSONSerialization.jsonObject(with:
                    dataResponse, options: [])
                print(jsonResponse) //Response result
            } catch let parsingError {
                print("Error", parsingError)
            }
        }
        
        task.resume()
        
    }
    
    
    func updateWeth()
    {
        let temp =json["main"]["temp"].
        
    }
    
    
    
    
}




````


### In the info.plist you will have to add Privacy - Location Always Usage Description and your custom alert message like, AppName(Demo App) would like to use your current location.


Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
