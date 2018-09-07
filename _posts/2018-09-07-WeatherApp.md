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

Import CoreLocation

adding CLLocationManagerDelegate in the class definition.

##  ViewController.swift
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


class WeatherViewController: UIViewController ,CLLocationManagerDelegate, ChangeCityDelegate {
    
    //Constants
    let WEATHER_URL = "http://api.openweathermap.org/data/2.5/weather"
    let APP_ID = "e72ca729af228beabd5d20e3b7749713"
    //let APP_ID = "b6907d289e10d714a6e88b30761fae22"
    
    
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
    func userEnteredANewCityName(city: String){
        let params: [String:String] = ["q": city ,"appid" : APP_ID]
        getWeatherData(url: WEATHER_URL, parameter: params)
    }
    
    
    //Write the PrepareForSegue Method here
    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        if segue.identifier == "changeCityName"{
            let destinationVC = segue.destination as! ChangeCityViewController
            destinationVC.delegate = self
        }
    }
    
    
}



```

### WeatherDataModel.swift
```
//
//  WeatherDataModel.swift
//  WeatherApp
//
//  Created by Angela Yu on 24/08/2015.
//  Copyright (c) 2015 London App Brewery. All rights reserved.
//

import UIKit
import CoreLocation
import Alamofire
import SwiftyJSON

class WeatherDataModel {

    //Declare your model variables here
    var temp : Int = 0
    var city : String = ""
    var cond : Int = 0
    var weatherIconName : String = ""
    
    //This method turns a condition code into the name of the weather condition image
    
   func updateWeatherIcon(condition: Int) -> String {
    
   switch (condition) {
   
       case 0...300 :
            return "tstorm1"
    
        case 301...500 :
           return "light_rain"
    
       case 501...600 :
           return "shower3"
    
       case 601...700 :
            return "snow4"
    
        case 701...771 :
           return "fog"
    
        case 772...799 :
            return "tstorm3"
    
        case 800 :
            return "sunny"
    
        case 801...804 :
            return "cloudy2"
    
        case 900...903, 905...1000  :
            return "tstorm3"
    
        case 903 :
            return "snow5"
    
        case 904 :
            return "sunny"
    
        default :
            return "dunno"
        }

    }
    
    
    
    
   
}


```

### ChangeCityViewController.swift
```
//
//  ChangeCityViewController.swift
//  WeatherApp
//
//  Created by Himanshu on 11/05/2018.
//  Copyright (c) 2018 Inspire Infotech Pvt Ltd. All rights reserved.
//

import UIKit


//Write the protocol declaration here:

protocol ChangeCityDelegate{
    func userEnteredANewCityName(city: String)
    
}

class ChangeCityViewController: UIViewController {
    
    
    
    
    //Declare the delegate variable here:
    var delegate: ChangeCityDelegate?
    
    //This is the pre-linked IBOutlets to the text field:
    @IBOutlet weak var changeCityTextField: UITextField!
    
    
    //This is the IBAction that gets called when the user taps on the "Get Weather" button:
    @IBAction func getWeatherPressed(_ sender: AnyObject) {
        
        let cityName = changeCityTextField.text!
        delegate?.userEnteredANewCityName(city: cityName)
        self.dismiss(animated: true, completion: nil)
        
        //1 Get the city name the user entered in the text field
        
        
        //2 If we have a delegate set, call the method userEnteredANewCityName
        
        
        //3 dismiss the Change City View Controller to go back to the WeatherViewController
        
        
    }
    

    

    

    //This is the IBAction that gets called when the user taps the back button. It dismisses the ChangeCityViewController.
    @IBAction func backButtonPressed(_ sender: AnyObject) {
        self.dismiss(animated: true, completion: nil)
    }
    
}

```


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
