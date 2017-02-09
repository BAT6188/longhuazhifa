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


