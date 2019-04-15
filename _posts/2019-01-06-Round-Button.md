---
layout: post
title: "Round-Button"
date: 2018-01-06 12:26:40
image: '/assets/img/swift.jpg'
description: About making round button in swift
category: 'Beginners'
tags:
- Swift
- Button

introduction: About making round button in swift
---


## Code

### Create an new Swift File with Button.swift in your project folder

```
import UIKit
@IBDesignable
class Button: UIButton {
    @IBInspectable var cornerRadius: CGFloat = 0 {
        didSet{
            self.layer.cornerRadius = cornerRadius
        }
    }
    @IBInspectable var borderWidth: CGFloat = 0 {
        didSet{
            self.layer.borderWidth = borderWidth
        }
    }
    @IBInspectable var borderColor: UIColor = UIColor.clear {
        didSet{
            self.layer.borderColor = borderColor.cgColor
        }
    }

}
```
### Select the button
### Add class 'Button' in Editor Section
### Set Property Corner Radius to value
```
eg. 9

```
### Done



Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
