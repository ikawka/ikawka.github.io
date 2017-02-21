---
title: Wordpres Ajax Frontend
description: Make ajax calls with wordpress for not logged in users.
published: '2017-02-21'
modified: '2017-02-21'
categories:
- wordpress
tags:
- wordpress ajax
- ajax front-end
excerpt: The ajaxurl is not exposed to front end by default.
image:
  feature: abstract-10.jpg
  width: '1136'
  height: '320'
---

<!-- more -->
The ajaxurl is not exposed to front end by default, so lets add it to the header first.

```php?start_inline=true
function set_ajaxurl(){
    echo '<script type="text/javascript"> var _ajaxurl = "'.admin_url("admin-ajax.php").'";</script>';
}
add_action( 'wp_head', 'set_ajaxurl' );
```
And then we make a action function  for our ajax
```php?start_inline=true
function ajax_action(){
    //do something with the $_POST data here
    //like you do with normal WordPress stuffs
 
    exit(); //this is needed
}
 
add_action( 'wp_ajax_nopriv_ajax_action', 'ajax_action' );
```
Take note of the wp_ajax_**nopriv**_ajax_action the **"nopriv"** makes it available to non logged in users. If you want to make you script work for logged in users as well, you need to duplicate your hook with the normal wp_ajax_ajax_action like so.
```php?start_inline=true
add_action( 'wp_ajax_ajax_action', 'ajax_action' );
```