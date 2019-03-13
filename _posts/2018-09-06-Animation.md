---
layout: post
title: "Using Animation in Swift"
date: 2018-09-06 12:26:40
image: '/assets/img/swift.jpg'
description: About Using Animation in Swift
category: 'Beginners'
tags:
- Swift
- Animation
- Core


introduction: Using Animation in Swift
---


## Animation


```
// Calling Function (left to right)
AnimateItem(duration: 0.5, delay: 0.6, object: lab4)

// Function
func AnimateItem (duration: Double, delay: Double, object: UIView) {
        
        UIView.animate(withDuration: duration, delay: delay, options: .curveEaseOut, animations: {
                object.center.x += self.view.bounds.width
        }) { (true) in
            
        }
    }
```

```
// FadeIn FadeOut effect animation to parent view
// Calling function in viewdidload
Tick()

// Function 
 func Tick () {
        timeLabel.text = Utilities().GetCurrentTime()
      UIView.animate(withDuration: 0.95, delay: 0, options: .curveEaseOut, animations: {
               self.view.alpha = 0.5
           }) { (true) in
            self.view.alpha = 1.0
        }
    }

```


Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
