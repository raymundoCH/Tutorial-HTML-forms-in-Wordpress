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




