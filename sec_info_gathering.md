

### IP/Domain信息

|名称|描述|
|:-------------:|-----|
|domain tools| |
|https://www.virustotal.com/#/domain/qq.com| 综合查询 Whois/子域名/DNS解析历史(支持子域名) |
|https://findsubdomains.com/subdomains-of/qq.com|domain 子域名信息 Find subdomains online.|
|https://dnsdumpster.com/|domain DNS枚举子域名信息 FREE domain research tool that can discover hosts related to a domain.|
|https://viewdns.info/|Reverse Whois/IP/domain/DNS/MS/NS Lookup.|
|https://dnstable.com/ip/203.205.158.53| Reverse 解析为某ip的诸多域名|
|https://viewdns.info/iphistory/?domain=qq.com|DNS解析历史(IP History) 该网站不支持查询子域名的历史IP|
|http://www.domaincrawler.com/qq.com|综合查询 whois/Mailserver(s)/subdomains|
|https://censys.io/ipv4/104.93.196.220/table|根据tls证书获取域名 443.https.tls.certificate.parsed.extensions.subject_alt_name.dns_names|
[https://url.fht.im/domain_search?domain=qq.com|基于大数据 [查看被搜索引擎收录的URL](https://url.fht.im/url_search?domain=v.qq.com)|
|other tools| |
|https://dns.google.com/query?name=qq.com|Google Public DNS 查询dns解析|
|https://www.ipip.net/ip.html | 查国内ip的比较精确的物理位置|
[https://iplocation.com/?ip=52.186.31.196|IP Location|
|[wappalyzer.com](https://www.wappalyzer.com/) |web技术栈信息 web frameworks, server software, analytics tools and many more. |
|https://api.hackertarget.com/nmap/?q=qq.com|实测确认是即时的 端口扫描 仅对8个端口发起nmap扫描|
|https://api.hackertarget.com/dnslookup/?q=vqq.com|实测确认是即时的 DNS lookup (A MX ..)|
|https://whoer.net/ | ip匿名性自测 可获取内网ip(通过webRTC等技术) |
|http://www.ifconfig.io/ | my ip address |
|https://osintframework.com/|OSINT Framework( 自动化工具[Photon: Incredibly fast crawler designed for OSINT.](https://github.com/s0md3v/Photon))|

### Google常规语法

```
使用引号搜索完全匹配的结果
"tallest building"

搜索未知字词
"largest * in the world"

搜素具体域名站点下的url
site:so.com

url中存在具体字符的url
inurl:"php?id="
inurl:.edu

url中存在具体关键字(所有关键字都必须存在 忽略符号 如/ )的url
allinurl:foo bar

在html body中存在特定关键字(多个关键字之一的都符合)的url
intext:seo blog

在html body中存在特定关键字(allintext 多个关键字同时存在才行)的url
allintext:seo blog

搜索社交媒体 如
@twitter

找相似的网站
related:bilibili.com
related:alipay.com

查找具体文件
filetype:pdf
filetype:xls inurl:pass user
```

```
用减法排除具有某些关键字的结果
site:apple.com -paper -music -inurl:https -inurl:.edu
site:apple.com -site:www.apple.com -inurl:support
```

[优化网页搜索 - Google 搜索帮助](https://support.google.com/websearch/answer/2466433)

[Advanced Searching in Google - Resources and Search Strategies](https://sites.google.com/site/resourcesandsearchstrategies/google/advanced-searching-in-google)

[Google高级语法（非官方） - Google Guide](http://www.googleguide.com/or_operator.html)

[ Google Hacking Database - exploit-db.com](https://www.exploit-db.com/google-hacking-database)

**例1 找web后台**

```
管理 后台 登陆 用户名 帐号 密码 验证码 系统 inurl:manage|admin|login|system|portal
site:github.com inurl:manage|admin|login|system|portal
```

**例2 找子域名**

```
site:<qq.com>
```
