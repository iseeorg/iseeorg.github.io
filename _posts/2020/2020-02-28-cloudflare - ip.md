---
layout: post
title: "cloudflare 全球节点备忘录"
subtitle: 'cloudflare 全球节点备忘录'
author: "panmg"
header-style: text
catalog:    true
tags:
  - cloudflare ip
  - cloudflare 节点
---


具体步骤不叨叨了 自己搜索 大概就是用cloudflare的cdn 以CNAME别名方式解析  然后到各种智能dns里面a到节点就ok了  暂时收入精华博文

接入CF之后，CF会给域名分配一个入口IP，一般是美西洛杉矶那边的。这个IP其实是采用的AnyCast技术，当用户访问到时候，会就近分配一个真实的节点IP，以加快访问速度。

访问：http://{节点IP/域名}/cdn-cgi/trace。比如要查看访客的真实IP ，则访问 https://www.31du.cn/cdn-cgi/trace

 MaxCDN (StackPath) vs CloudFlare vs Amazon CloudFront vs Akamai Edge vs Fastly

需要用到的
CF:www.cloudflare.com

cfp（Cloudflare合作伙伴）
推荐笨牛:cdn.bnxb.com (介绍 lowvps.cn/bnxb-cloudflare-cdn/)

稳定很长时间的: https://cf.tlo.xyz/

https://cdn.wzfou.com/

萌精灵 https://cdn.moeelf.com/

智能解析 国内随便选 建议dnspod/dnsdun/dnsla

都比较不错 因为这三家支持智能三网/四网解析 外加搜索引擎百度等单独解析

 

下面说一下IP段 比较杂乱  可以参考CloudFlare节点IP收集(全球附亚洲节点/日本,香港,韩国,印度,美国)

这里面有一个思想 就是需要 自己添加后 不断去优化! 也就是 用各种ping命令检查一下 把 延迟比较高的换掉

******************************************节点开始*****************************

CloudFlare的节点：国内速较快的IP段：

（联通移动推荐节点）

104.23.240.0-104.23.243.254

（电信推荐CloudFlare 百度云合作 ip）

162.159.208.4-162.159.208.103

162.159.209.4-162.159.209.103

162.159.210.4-162.159.210.103

162.159.211.4-162.159.211.103

各线路推荐列表：
电信：推荐走圣何塞，例：104.16.160.* 或者上面的百度云合作 ip。
移动：推荐走移动香港，例：172.64.32.*、141.101.115.* 或者 104.23.240.0-104.23.243.254。
联通：没发布什么好线路，可走圣何塞。例：104.16.160.* 或者 104.23.240.0-104.23.243.254。也可以试一下走亚特兰大 108.162.236.*（日前不可用。） 。

延迟和速度不错，IP地址：162.159.211.3-162.159.211.103

移动很不错：198.41.214.162

162.158.26.1
172.68.144.1
172.69.152.1
104.19.195.151
104.18.177.69
104.25.176.1
可以设置用于 移动网络

108.162.227.1
162.158.4.1
172.69.152.1
可以设置用于 联通网络

162.158.116.1
108.162.226.1
可以设置用于 默认网络

172.68.32.1
108.162.243.1
108.162.245.1
108.162.246.1
172.68.172.1
可以设置用于 电信网络


CloudFlare官方公开的所有节点 https://www.cloudflare.com/zh-cn/ips/

IPv4
173.245.48.0/20
103.21.244.0/22
103.22.200.0/22
103.31.4.0/22
141.101.64.0/18
108.162.192.0/18
190.93.240.0/20
188.114.96.0/20
197.234.240.0/22
198.41.128.0/17
162.158.0.0/15
104.16.0.0/12
172.64.0.0/13
131.0.72.0/22
Also available as a IPv4 text list.

IPv6
2400:cb00::/32
2606:4700::/32
2803:f800::/32
2405:b500::/32
2405:8100::/32
2a06:98c0::/29
2c0f:f248::/32
Also available as a IPv6 text list.

 

某博主找到了一批CF亚洲节点，再通过实测最终得出了3个ping值很低（100ms以内）的节点IP：

202.86.161.100（澳门）、27.102.67.84（韩国）、23.61.246.100（台湾，速度略慢，但相对其他节点亚洲又好那么一丢丢）。未测试

******************************************节点结束*****************************

所有这些节点 摘自各个博主  不保证效果  , 只有自己去测试 筛选

 

国内的CDN譬如 dnspod/ dnsdun/ dnsla/ 阿里dns /百度DNS/ 华为云dns /京东云dns / cloudxns /蓝汛 网宿 Azure之类

 

其他参考资料

https://www.shanyemangfu.com/cloudflare-hk.html (我的启蒙贴)

https://zhang.ge/5149.html

https://www.wanvi.net/10187.html

Cloudflare免费版详细使用教程 https://www.imhunk.com/cloudflare-tutorials/

 