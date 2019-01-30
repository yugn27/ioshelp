---
layout: post
title: "TableViewController Documentation"
date: 2018-09-02 12:26:40
image: '/assets/img/swift.jpg'
description: About TableViewController Documentation
category: 'Basic'
tags:
- Swift
- iOS

introduction: TableViewController Documentation
---




## TableViewController



### UITableViewController
A view controller that specializes in managing a table view.

Overview
Subclass UITableViewController when your interface consists of a table view and little or no other content. Table view controllers already adopt the protocols you need to manage your table view's content and respond to changes. In addition, table view controllers implement the following behaviors:

If a nib file is specified via the init(nibName:bundle:) method (which is declared by the superclass UIViewController), UITableViewController loads the table view archived in the nib file. Otherwise, it creates an unconfigured UITableView object with the correct dimensions and autoresize mask. You can access this view through the tableView property.

If a nib file containing the table view is loaded, the data source and delegate become those objects defined in the nib file (if any). If no nib file is specified or if the nib file defines no data source or delegate, UITableViewController sets the data source and the delegate of the table view to self.

When the table view is about to appear the first time it’s loaded, the table-view controller reloads the table view’s data. It also clears its selection (with or without animation, depending on the request) every time the table view is displayed. The UITableViewController class implements this in the superclass method viewWillAppear(_:). You can disable this behavior by changing the value in the clearsSelectionOnViewWillAppear property.

When the table view has appeared, the controller flashes the table view’s scroll indicators. The UITableViewController class implements this in the superclass method viewDidAppear(_:).



You create a custom subclass of UITableViewController for each table view that you want to manage. When you initialize the controller in init(style:), you must specify the style of the table view (plain or grouped) that the controller is to manage. Because the initially created table view is without table dimensions (that is, number of sections and number of rows per section) or content, the table view’s data source and delegate—that is, the UITableViewController object itself—must provide the table dimensions, the cell content, and any desired configurations (as usual). You may override loadView() or any other superclass method, but if you do be sure to invoke the superclass implementation of the method, usually as the first method call.

<a href="https://developer.apple.com/documentation/uikit/uitableviewcontroller">https://developer.apple.com/documentation/uikit/uitableviewcontroller</a>

```
//
//  ViewController.swift
//  api tests
//
//  Created by Yash Nayak on 20/01/19.
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
