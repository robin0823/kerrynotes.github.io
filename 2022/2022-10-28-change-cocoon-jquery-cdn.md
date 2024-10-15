---
title: "Cocoon主题 - 将jQuery的CDN更改为自己站点"
date: "2022-10-28"
categories: 
  - "others"
tags: 
  - "cocoon"
  - "cdn"
coverImage: "cdn.webp"
---

网站使用了Cocoon主题后，我发现在国内访问会很慢，甚至打不开。F12查看了一下，发现是它加载了Google托管下的jQuery的库。在国外可能没什么问题，但是国内的话，就会一直卡住。

**如何更改Cocoon主题jQuery的CDN？**

经查，发现在主题lib文件夹下的[utils.php](https://github.com/yhira/cocoon/blob/d624b576b0ea8521b357bf1d7b08087eaab62124/lib/utils.php#L366)里，可以自定义URL。

```
function get_jquery_core_url($ver){
  $url = null;
  switch ($ver) {
    case '3':
    $url = 'https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js';
    break;
    case '2':
    $url = 'https://ajax.googleapis.com/ajax/libs/jquery/2.2.4/jquery.min.js';
    break;
    case '1':
    $url = 'https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js';
    break;
  }
  return $url;
}
```

将url改为本地之后， 上传至对应的文件夹即可。
