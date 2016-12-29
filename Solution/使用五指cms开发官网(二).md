---
title: 使用五指cms开发官网(二)
tags: 五指,cms,官网
grammar_cjkRuby: true
---

## 一、数据绑定
 1. 进入到五指cms的程序包目录的“coreframe\templates”目录 新建一个文件夹 取名为 "guanwangcms"
 2. 进入到【1】中创建的 “guanwangcms”目录 新建目录 取名为 “content” // 此处放置静态页面
 3. 进入到五指cms的程序包目录的“www\res”目录 新建一个文件夹 取名为 “guanwangcms” // 此处放置外部样式图片文件夹 尽可能与【1】中创建的文件夹的名字一致
 4. 进入五指cms的程序包目录的“www\configs”目录 修改文件“web_config.php” 修改 “define('TPLID','t3')” 中的 “t3” 为 【1】中创建的文件夹的名字为 “guanwangcms”  修改 “define('SUPPORT_MOBILE',1)” 中的 “1” 为 “0” 表示无需要跳转到移动端页面 如图所示：![config edit][1]
 5. 将我们写好的静态页面拷贝到 【1】中创建的文件目录下
 6. 将样式文件以及图片放置到 【3】 中创建的文件目录下
 7. 然后进入到管理后台进行 “更新缓存”，“一键全部更新”，“生成首页”，“站点首页”  操作，这时我们页面会跳转到首页，和我们静态页面一样，但是没有样式文件。如图所示 ![首页][2]




















  [1]: http://xxx.freeimage.us/image.php?id=D25D_58646EE1
  [2]: http://xxx.freeimage.us/image.php?id=A34A_58647103