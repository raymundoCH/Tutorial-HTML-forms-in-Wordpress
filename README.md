# Wordpress Plugins and HTML form submission

## Introduction

Each time we develop a Wordpress Plugin it's very likely that we are going to include an HTML form so that the user can input specific information; therefore learning how to handle HTML form submission is a basic skill for any Wordpress developer.

In this tutorial we are going to code an small plugin which sets up an **admin page** and its corresponding menu item; the **admin page** displays an HTML form where the full name of the user must be entered; after the user hits the **submission button** then the data is printed to the **debug.log** file and can be seen by using the console.

## Creating the necessary files and folders for the plugin

Firstly we must create the Plugin folder; navigate to the Plugins folder and create a new directory inside; open the console and run the next commands:

1. cd /var/www/html/wp-content/plugins
2. mkdir myCustomPlugin

Then we must open the **myCustomPlugin** folder and add three different php files inside; those php files are **myCustomPlugin.php, customAdminPage.php and processingFormData.php**.


<img src="/1F604.svg" height="40" width="40"/> That's it! you just completed the first part!


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

## Including the function add_menu_page

Setting up a new **admin page** for the Dashboard is the first step; open the file **customAdminPage.php** and add the next php code snippet at the top of the file:
~~~
<?php

if(!function_exists("add_menu_page")){

	include(ABSPATH."wp-admin/includes/plugin.php");
}

//more php code will be added here...
~~~
The code above is used to check whether the function **admin_menu_page** is available for use; in case the function is not available then the source code is included.

## Setting up the add_menu_page function

The **add_menu_page** function is called to create a new **admin page** in the Dashboard; open the file **customAdminPage.php** and make the next modifications:

~~~
if(!function_exists("test_HTML_form")):

	function test_HTML_form_markup(){
		?>
		<div class="wrap">
      <!-- The HTML markup for the form will be here -->
    </div>
		<?php
	}

	function test_HTML_form(){

		add_menu_page(
			"Test HTML form plugin",
			"Test HTML form",
			"manage_options",
			"test-form",
			"test_HTML_form_markup",
			"dashicons-store",
			4
		);

	}

	add_action("admin_menu","test_HTML_form");
endif;
~~~
The **admin_menu** hook is used to configure admin pages for the Dashboard in this case; when the **admin_menu** hook is run then the function **test_HTML_form** is run.

The function **test_HTML_form** is declared and then used as a parameter for the **add_action** function; note how the **add_menu_page** function is invoked inside the **test_HTML_form** function.

The **add_menu_page** function requires the next parameters:

1. **Test HTML form plugin** is the webpage title displayed in the web browser tab.
2. **Test HTML form** is the text for the menu item.
3. **manage_options** is the user permission necessary to see the admin page; this permission is granted only to admins.
4. **test-form** is the slug of the admin page.
5. **test_HTML_form_markup** is the name of the function which contains the HTML markup for the form.
6. **dashicons-store** is the name of the icon for the menu item.
7. The number **4** represents  the position of the menu item.

The **test_HTML_form_markup** function contains a div with the class **wrap**; this HTML element is used by Wordpress and should be placed inside each admin page.

## Adding the necessary HTML markup

Open the file **customAdminPage.php** and apply the next modifications:

~~~
function rch_submit_watch_menu_html(){
		?>
		<div class="wrap">
			<form method="post">
  				<label for="firstName">
			          <input type="text" id="firstName" name="firstName"/>
				</label><br/>
				<label for="lastName">
				   <input type="text" id="lastName" name="lastName"/>
				</label><br/>
				<input type="submit" value="Submit"/>
			</form>
		</div>
	<?php
	}
~~~
As you can see two different text fields were added; these text fields are used to enter the full name of the user; note how the **form tag** only has the **method attribute**; this configuration makes the webpage to be reloaded when the user hits the **Submit button**.



