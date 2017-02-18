---
layout: post
title: Add Metabox To Any Post Type
description: "How to add meta box to any post type"
modified: 2017-02-18
tags: [metabox, metaboxes]
categories: [wordpress]
excerpt: So you want to up your game and add a little bit of complexity to your post or custom post type perhaps. Meta boxes might be one of the things that you are looking for.
---
<!-- more -->
So you want to up your game and add a little bit of complexity to your post or custom post type perhaps. Meta boxes might be one of the things that you are looking for.

Lets start by creating a hook to the **add_meta_boxes** action.
```php?start_inline=true
//add the action
add_action( 'add_meta_boxes', 'custom_meta_boxes', 10, 2 );
```
Then create the callback function of the action, this is where you can check the current post-type and decide what to do. The defaults are post and page.
```php?start_inline=true
function custom_meta_boxes($post_type, $post){
    if($post_type == '{post-type}'){
        //now we create the meta box and add a callback function to render
        add_meta_box( 'my-meta-box',
                      'Meta Box Title',
                      'render_meta_box', //<-- callback function
                      'post-type',
                      'normal',
                      'default');
    }
}
```
Lastly you need to render the content of the meta box
```php?start_inline=true
//this will be called to render the meta box
function render_meta_box($post){
    //render the meta box here
}
```
