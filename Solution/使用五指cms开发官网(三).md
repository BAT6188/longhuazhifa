---
title: 使用五指cms开发官网(三)
tags: 五指,cms,官网
grammar_cjkRuby: true
---

## 三、页面其它绑定
 1. 很多时候，我们的seo设置和页面的一些公共部分通常不用经常自己去修改，还是查看五指官网[开发文档][1]，进行修改，查询得知 {$title} 会被解析成 <?php echo $title;?>  但是很多时候我们的头和脚也都是公用的，所以我们可以对页面进行头尾分离：新建head.html 和 foot.html 拷贝index.html 头部内容到head，脚部内容到 foot， 然后在index 引入头部和脚步，通过查询 “常见函数方法的整理收集” 得到 （T($m, $template’, $style) $m 模块名称 $template 模版名称 $style 模版风格 Ps: 常用的为前两个参数） 所以我们引入头部 需要  {T "content","head",TPLID}  在index.html页头添加 {T "content","head",TPLID} 页脚添加 {T "content","foot",TPLID}  然后保存，进行php发布四部曲，刷新页面即可看到相应效果
 2. 进入wuzhicms管理后台 “系统设置”-->“基本设置” 对网站进行设置 然后保存，四部曲，首页刷新，查看效果 ![index][2]![edit][3]
 3.  但是由于系统原因，我们并不能对首页的title和copyright进行修改，需要我们手动去修改 “www/index.html” 文件
 4.  接下来同理修改其它页面
 5.  很多时候我们也不要自己去设置导航栏的菜单， 我们可以在后台管理页面进行添加，“发布内容”-->“栏目管理” 进行添加，这里需要注意区分什么叫单页什么叫列表(可以简单理解单页就是这个页面不会再有超链接挑战到新的页面，列表反之)，选择类型选择“文章类型”，在“模板设置”，进行页面配置

  [1]: https://www.wuzhicms.com/doc/
  [2]: http://xxx.freeimage.us/image.php?id=2623_58647DC1
  [3]: http://xxx.freeimage.us/image.php?id=0C3C_58647FA9