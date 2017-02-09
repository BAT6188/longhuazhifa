---
title: 使用五指cms开发官网(四)
tags: 五指,cms,官网
grammar_cjkRuby: true
---
### 由于服务器原因，现在并没有可以直接使用的图片服务器，图片问题会在后期补上

现在我们的页面已经能够正常获取自行添加的后台数据，譬如现在我们已经获取到了菜单列表。

现在通过后台添加菜单，发布内容，然后我们从前台取值：
因为创建菜单的时候有选择：单页||列表 所以获取详情页面也各不一样：
单页：

``` dust
{wz:content action="listing" pagesize="1" order="sort DESC" cid="13" modelid="1" moredata="1" urlrule="$urlrule" }
    {loop $rs $r}
      {$r[title]}
      {$r[remark]}
      {php print_r($r[content])}
      {$r[thumb]}
      <img src="{$r[thumb]}" />
    {/loop}
  {/wz}
```
>  ### 解析代码：
> 因为要获取详情所以我们action 必须使用listing，而因为是单页所以获取pagesize为1就好，cid表示我现在是要获取哪个菜单的id，菜单id可以从后台-->发布类容-->栏目管理查询得知（如果模板能够统一也可以从上一文档中获取菜单的方式动态获取然后赋值给cid）；modelid：模板类型id，1表示文章模型，5表示图片模型，其它的可以从后台-->发布类容-->模型管理查询得知（因为modelid不一样取值字段也不一样，开发者可以自行查询api然后编写模板，因为modelid也是可以在获取菜单的时候获取到）
> 顾名思义loop 循环，那么{loop $rs $r} 就是 循环$rs 然后把每次循环的结果赋值给$r；注意的是在我们没有给定指定返回变量名时系统就会返回一个叫$rs变量
> 然后取值动态显示，常用字段： title 文章标题，remark 摘要简要，content 内容，thumb 缩略图； 因为content在后台是一个富文本编辑器所以前台获取的时候如果需要富文本中编辑的样式时建议用{php print_r($r[content])}的方式输出。


列表：

``` cs
{wz:content action="listing" pagesize="3" order="sort DESC,id DESC" cid="21"} 
	{loop $rs $r}
        {strcut($r['title'], 30, '...')}
        <img class="cnt_img" src="{$r['thumb']}"> 
        {date('Y-m-d',$r['addtime'])}
     {/loop}
 {/wz}
```

> 同单页注释，但是因为是列表所以需要修改pagesize为指定分页大小
> {strcut($r['title'], 30, '...')} 表示 把title截断，保留最多30字符，截断部分用...表示
> {date('Y-m-d',$r['addtime'])} 表示把addtime 格式化成 年-月-日 格式
> 需要注意的是：如果需要分页条需要修改代码为

``` dust
<div>
 {wz:content action="listing" page="$page" pagesize="10" order="sort DESC,id DESC" cid="21" urlrule="$urlrule"}
 ...
 {/wz}
 </div>
 <!-- start-五指分页-->
 <div class="text-center fy">
 {if $this->db->number>10}
 <nav class="text-center">
 <ul class="pagination">
 {$pages}
 </ul>
 </nav>
 {/if}
 </div>
```
> 系统会自动判断并且添加到页面指定位置
> 另外 分页只在 栏目管理中对应页面指定的模板设置中设置的终级栏目页模版的页面生效。

因为是列表所以我们还需要详情页面，在 栏目管理中对应页面指定的模板设置中设置的内容页模版 设置对应页面比如show.html

详情页面：
新建html页面名字为show.html
然后书写为基础html标准页面

``` scss
{php print_r($title)}
{php print_r($content)}
{php print_r($thumb)}
```
> 顾名思义 title 就是标题，content就是内容，其它字段参考单页注释，另有copyfrom 来源 访问量需要用 <lable id="hits">0</lable> 来得到，还需要引入一个js文件：`<script type="text/javascript" src="{WEBURL}index.php?f=stat&id={$id}&cid={$cid}"></script>` 
> 因为页面是通过列表跳转，所以我们不需要其它操作，我们只要在配置的跳转的指定页面中编写获取字段就好
> {WEBURL} 表示网站站点位置，参考后台配置，{R}资源根目录
 

