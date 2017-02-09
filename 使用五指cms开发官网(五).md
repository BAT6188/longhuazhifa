---
title: 使用五指cms开发官网(五)
tags: 五指,cms,官网
grammar_cjkRuby: true
---

在页面有多个循环的时候 我们需要指定页面获取数据返回变量的名称
参考代码：

``` nix
{wz:content action="listing" pagesize="999" modelid="5" moredata="1" order="sort DESC" cid="36" urlrule="$urlrule" return="rdata" }
  {loop $rdata $pbanner}
  {/loop}
{/wz}
```
> 解析代码：
> 可以发现和之前唯一区别就是 多加了一个参数return="rdata"
> rdata可以随意指定，看开发者自身

另外 五指后台配置的logo seo 等信息都是基于缓存，所以使用的时候需要

``` powershell
logo:
{if $siteconfigs['logo'] ==''}<img src="{$siteconfigs['logo']}" />{else}<img src="{R}guanwangcms/img/logo.png" />{/if}

title:
{if isset($seo_title)}{$seo_title}{/if}

seo:
{if isset($seo_description)}{$seo_description}{/if}

keywords:
{if isset($seo_keywords)}{$seo_keywords}{/if}

```

如需使用反馈功能请添加feedback.html并参考以下代码：

``` applescript
 <form action="index.php?m=feedback&f=index&v=contact" method="post">
        <div  class="form-inline" style="margin-bottom: 15px;">

            <div class="form-group">
                <label for="exampleInputName2">姓名<span class="color_danger">*</span></label>
                <input type="text" name="form[linkman]" class="form-control" id="exampleInputName2" placeholder="姓名" required>
            </div>
            <div class="form-group" style="margin-right: 100px;"></div>
            <div class="form-group">
                <label for="exampleInputEmail2">联系邮箱 <span class="color_danger">*</span></label>
                <input type="email" name="form[email]" class="form-control" id="exampleInputEmail2" placeholder="xxx@xxx.com" required>
            </div>
        </div>
        <div class="form-box">
            <div class="row">
                <div class="col-md-12">
                    <textarea name="form[content]" class="form-control" rows="10" placeholder="请详细的输入反馈问题" required></textarea>
                </div>
            </div>
        </div>
        <br>
        <div class=" form-inline text-center" >
            <input type="hidden" name="form[forward]" value="{$forward}">
            <button type="submit" name="submit" class="btn btn-warning  btn-lg" >&nbsp;&nbsp;&nbsp;提交&nbsp;&nbsp;&nbsp;</button>
        </div>
    </form>
```
开发时返回功能可以写在其它页面，但是目录必须要feedback.html 文件可以用五指cms 默认模板拷贝过来

