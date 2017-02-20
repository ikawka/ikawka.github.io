---
layout: post
title: PHP Date Quirks
description: "Some handy notes about php dates"
published: 2017-02-20
modified: 2017-02-20
tags: [php, date]
categories: [php]
excerpt: Get Monday of the week; this sript is handy if you want to be able to display the current week’s dates. just specify a date.
image:
    feature: leopard.jpg
    width: 1136
    height: 320
---
<!-- more -->
Get Monday of the week; this sript is handy if you want to be able to display the current week’s dates. just specify a date.

```php?start_inline=true
function getMonday($date){
    if(date('N', strtotime($date)) == 7){
        $date = date('Y-m-d', strtotime("-1 days", strtotime($date)));
    }
    return date('Y-m-d', strtotime("this week monday", strtotime($date)));
}

function getSunday($date){
    if(date('N', strtotime($date)) == 7){
        $date = date('Y-m-d', strtotime("-1 days", strtotime($date)));
    }
    return date('Y-m-d', strtotime("this week sunday", strtotime($date)));
}
echo "Start: ".getMonday('2014-08-22');
echo "End: ".getSunday('2014-08-22');
```
