---
title: php动态页面静态化
date: 2016-06-18 18:56:12
categories: [php,后端]
tags: [php,后端]
---


# 优化页面响应时间

* 动态页面静态话

```
如果页面中的一些内容不经常改动，动态页面静态化是非常有效的加速方法。
因为静态化后不需要再php程序的 语法分析-编译-执行这个流程。直接呈现页面，大大减少了服务器脚本的计算时间
```

* 优化数据库
* 使用负载均衡
* 使用缓存

# 关于动态URL地址设置静态形式

例如： 

`http://state.com/index.php?c=play&a=index&id=83743` => `http://state.com/play/83743.shtml`  

虽然转换了地址，但是加载的内容没变。 这个配置是通过服务器配置的，这是伪静态


# 静态化介绍

php静态化可以划分为两部分

> 纯静态
> >局部纯静态  
> >全部纯静态

> 伪静态

局部纯静态化是通过使用 ajax技术局部动态化的。


# buffer
纯静态化需要用到buffer，

php.ini 里面可以配置 output_buffering = ON。使用缓冲区

```
<?php
echo 1;
// ob_getcontents() 获取缓冲区内容
echo ob_getcontents();

```
输出 

```
1
1
```

|函数|备注|
|----|---|
|ob\_start|打开输出空值缓存|
|ob\_get\_contents|返回输出缓冲区内容|
|ob\_clean|清空输出缓冲区|
|ob\_get\_clean|得到缓冲区的内容并删除当前缓冲区|


# php如何实现页面纯静态化

* 1、file\_put\_contents()函数，写内容入文件
* 2、使用php内置缓存机制实现页面静态化 - output\_buffering

# 纯静态化案例实现
* 1、链接数据库、然后从数据库里面获取数据
* 2、把获取到的数据填充到模板文件里面
* 3、需要把动态的页面转化为静态页面，生成纯静态化文件



























