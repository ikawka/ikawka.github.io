---
title: Option Page for your Plugin or Theme
description: How to add option page to your plugin or theme.
published: '2017-03-02'
modified: '2017-03-02'
categories:
- wordpress
tags:
- option page
- plugin
- theme
excerpt: How to add option page to your plugin or theme.
image:
  feature: abstract-5.jpg
  width: '1136'
  height: '320'
---

<!-- more -->
How to add option page to your plugin or theme.
```php?start_inline=true
add_action('admin_menu', 'my_option_page');

function my_option_page(){
    add_menu_page(
        'Option Page Title',
        'Menu Title',
        'publish_pages', //Capability
        'menu-slug-for-page', //this is the link identifier
        'render_option_page', //the callback function for rendering
        'dashicons-lightbulb', //Menu Icon
        62 //Menu Position
     );
     add_submenu_page(
         'menu-slug-for-page', //link identifier of your main menu
         'Sub Page Title',
         'Submenu Title',
         'publish_pages', //Capability
         'submenu_slug_for_page',
         'render_sub_page'
     );
}

//Render your Option Page
function render_option_page(){
    //do what you want here or include another php file
    include 'myoption-form.php';
}

function render_sub_page(){
   //do what you want here or include another php file
}
```
To be able to keep the setting of your plugin or theme in the database you will need to register your settings.
```php?start_inline=true
add_action( 'admin_init', 'register_my_setting' );

function register_my_setting() {
    register_setting(
        'my_options_group', //Option Group Name
        'my_option_name', //The Option Name itself
        'sanitize_values' //optional callback to sanitize the values
    );
}
```
Once you have successfully registered your setting, now it can be used in the option page your theme or plugin. Continuing with our example function **render_option_page()**.
//myoption-form.php
```php
<?php
       //initialy you get all the options so that you
       //will be able to use it in the form
      $options = get_option( 'my_option_name' );  
?>
<form action='options.php' method='post' role='form'>
<?php
      //initiate the registered settings
      //basically tell WordPress to save the data
      //under the 'my_options_group'
      settings_fields( 'my_options_group' );
      do_settings_sections( 'my_options_group' );
?>
<!-- I use array name "my_option_name[some-setting]" for the field -->
<input type="text" name="my_option_name[copyright-text]" value="<?php echo $options['copyright-text']; ?>" />

<!-- Use WordPress' default submit button -->
<?php submit_button(); ?>
</form>
```
Reference for Capabilities:
https://codex.wordpress.org/Roles_and_Capabilities
Default Icon Reference:
https://developer.wordpress.org/resource/dashicons
Default Menu Structure Position:
* 2 – Dashboard
* 4 – Separator
* 5 – Posts
* 10 – Media
* 15 – Links
* 20 – Pages
* 25 – Comments
* 59 – Separator
* 60 – Appearance
* 65 – Plugins
* 70 – Users
* 75 – Tools
* 80 – Settings
* 99 – Separator
