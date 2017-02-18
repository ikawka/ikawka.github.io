---
layout: post
title: Add Mime Types In Wordpress
description: "How to add other mime types in wordpress"
modified: 2017-02-18
tags: [mimes, svg, filter, upload mimes]
categories: [wordpress]
---

If you are having trouble uploading a specific file with wordpress. Chances are they file type might not be allowed. However there is always a way to tell wordpress to recognize the file type. You can add the following code to your
theme's function.php

{% highlight php %}
<?php
function cc_mime_types($mimes) {
  $mimes['svg'] = 'image/svg+xml';
  return $mimes;
}

add_filter('upload_mimes', 'cc_mime_types');
{% endhighlight %}

The code above will allow you to upload svg files to wordpress. Read more about mime types [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types){:target="_blank"}
