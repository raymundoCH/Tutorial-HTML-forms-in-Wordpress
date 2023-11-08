# Wordpress Plugins and HTML form submission

## Introduction

Each time we develop a Wordpress Plugin it's very likely that we are going to include an HTML form so that the user can input specific information; therefore learning how to handle HTML form submission is a basic skill for any Wordpress developer.

In this tutorial we are going to code an small plugin which sets up an **admin page** and its corresponding menu item; the **admin page** displays an HTML form where the full name of the user must be entered; after the user hits the **submission button** then the data is printed to the **debug.log** file and can be seen by using the console.

## Creating the necessary files and folders for the plugin

Firstly we must create the Plugin folder; navigate to the Plugins folder and create a new directory inside; open the console and run the next commands:

1. cd /var/www/html/wp-content/plugins
2. mkdir myCustomPlugin

Then we must open the **myCustomPlugin** folder and add three different php files inside; those php files are **myCustomPlugin.php, customAdminPage.php and processingFormData.php**.

That's it! you just completed the first part 😃 !

## Adding the header comment

Wordpress requires that all plugins contain a comment section into the main php file so that Wordpress knows some basic details about the plugin being activated.

Open the file **myCustomPlugin.php** and add the next comment at the top of the file:

~~~
<?php
/*
* Plugin Name: Testing HTML for submission
* Description: This plugin generates an HTML form 
* Author: YOUR-NAME-HERE
*/
~~~
Now if you navigate to the Plugins section in the Dashboard you should be able to see the plugin listed; activate the plugin otherwise any change you make to the code won't take effect.



