---
layout: post
title: "Inline Swift Function"
date: 2018-10-01 12:26:40
image: '/assets/img/swift.jpg'
description: Inline Swift Function
category: 'Beginners'
tags:
- Swift



introduction: Inline Swift Function
---

# Inline Function written in swift
```
// Hiding Keyboard Gesture
self.view.addGestureRecognizer(UITapGestureRecognizer(target: self.view, action: #selector(UIView.endEditing(_:))))
```

```
// Push Segue by code
let regView = self.storyboard?.instantiateViewController(withIdentifier: "SendViewController") as? SendViewController
self.navigationController?.pushViewController(regView!, animated: true)
```

```
//Custom Frame
pubView.frame = CGRect(x: 0, y: 0, width: Int(100 * UIScreen.main.bounds.width/100), height: Int(90 * UIScreen.main.bounds.height/100))
view.addSubview(pubView)
```


```
//Segment Control
@IBOutlet weak var RoomSelectoutlet: UISegmentedControl!

@IBAction func RoomtypeSeg(_ sender: UISegmentedControl) {
        switch RoomSelectoutlet.selectedSegmentIndex
        {
        case 0:
            RoomType = "Conference";
        case 1:
            RoomType = "Meeting";
        case 2:
            RoomType = "Training";
        case 3:
            RoomType = "Auditorium";
        default:
            break;
        }
}
    
```


```
//Check Box
// Checkbox Swwift file can be found here https://github.com/Apple-Inspire/Checkbox/blob/master/Checkbox.swift
// check box outlet
@IBOutlet weak var InpectionTestingoutlet: Checkbox!

//purpose of visit
var InpectionTestingvar = "No"
    
    
//purpose of visit
                    if (InpectionTestingoutlet.isChecked == true)
                    {
                        InpectionTestingvar = "Yes";
                    }
                    else{
                        InpectionTestingvar = "No";
                    }

```


```
//Check box validation
 if (InpectionTestingoutlet.isChecked == false )
 {
     myalert("Purpose of visit", "Select atleast one item")
 }
```
Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
