---
layout: post
title: Human Readable Filesize
description: "Filesize that are more human readable in php"
published: 2017-02-21
modified: 2017-02-21
tags: [php, filesize, humanized]
categories: [php]
excerpt: The easiest way to automatically convert file sizes in bytes to more human readable in php.
image:
    feature: abstract-11.jpg
    width: 1136
    height: 320
---
<!-- more -->
The easiest way to automatically convert file sizes in bytes to more human readable in php.

```php?start_inline=true
function human_filesize($bytes, $decimals = 2) {
    $sz = 'BKMGTP';
    $factor = floor((strlen($bytes) - 1) / 3);
    return sprintf("%.{$decimals}f", $bytes / pow(1024, $factor)) . @$sz[$factor];
}
```
