---
title: 使用五指cms开发官网(二)
tags: 五指,cms,官网
grammar_cjkRuby: true
---

## 一、数据绑定
 1. 进入到五指cms的程序包目录的“coreframe\templates”目录 新建一个文件夹 取名为 "guanwangcms"
 2. 进入到【1】中创建的 “guanwangcms”目录 新建目录 取名为 “content” // 此处放置静态页面
 3. 进入到五指cms的程序包目录的“www\res”目录 新建一个文件夹 取名为 “guanwangcms” // 此处放置外部样式图片文件夹
 4. 进入五指cms的程序包目录的“www\configs”目录 修改文件“web_config.php” 修改 “define('TPLID','t3')” 中的 “t3” 为 【1】中创建的文件夹的名字为 “guanwangcms” 

