---
layout: post
title: Add Mime Types In Wordpress
description: "How to add other mime types in wordpress"
modified: 2017-02-18
tags: [mimes, svg, filter, upload mimes]
categories: [wordpress]
---

{% highlight php %}
<?php 
function cc_mime_types($mimes) {
  $mimes['svg'] = 'image/svg+xml';
  return $mimes;
}

add_filter('upload_mimes', 'cc_mime_types');
{% endhighlight %}
