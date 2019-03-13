---
layout: post
title: "TableView"
date: 2018-09-02 12:26:40
image: '/assets/img/swift.jpg'
description: About TableView
category: 'Basic'
tags:
- Swift
- iOS

introduction: TableView
---




## TableView

### UITableViewController
A view controller that specializes in managing a table view and displaying data from swift file to UI view controroller.

```
// Table View Delegate method
cellForRowAt
numberOfRowsInSection
```

```
//
//  ViewController.swift
//  TableView Program
//
//  Created by Yash Nayak on 20/08/18.
//  Copyright © 2019 Yash Nayak. All rights reserved.
//

import UIKit

class ViewController: UIViewController ,UITableViewDelegate, UITableViewDataSource{
    
   
    let names: [String] = ["Yash", "Sahil", "Prakshr", "Sudanshu", "Vaibhav"]
    let cellReuseIdentifier = "cell"
    

    @IBOutlet var tableView: UITableView!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        self.tableView.register(UITableViewCell.self, forCellReuseIdentifier: cellReuseIdentifier)
        
        tableView.delegate = self
        tableView.dataSource = self
    }
    
   
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return self.names.count
    }
    
  
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        
        let cell:UITableViewCell = self.tableView.dequeueReusableCell(withIdentifier: cellReuseIdentifier) as UITableViewCell!
        
        cell.textLabel?.text = self.names[indexPath.row]
        return cell
    }
    
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        print("You tapped cell number \(indexPath.row).")
    }
}
    
  

```


Want to see something else added? <a href="https://yugn27.github.io/contact/">Open an issue.</a>
