# 什么是 SSL、TLS 和 HTTPS？

</br>
</br>

## 概念

- `SSL` ： 安全套接字层(Secure Sockets Layer，SSL) 是一种加密安全协议;（SSL是 TLS的前身）
- `TLS` ： 安全传输层协议(Transport Layer Security，TLS) 是为网络通信提供安全及数据完整性的一种安全协议;
- `HTTP` ： 超文本传输协议(Hyper Text Transfer Protocol) 是从WEB服务器传输超文本标记语言(HTML)到本地浏览器的传送协议。
- `HTTPS` ： 超文本传输安全协议（Hypertext Transfer Protocol Secure），是以安全为目标的HTTP通道，简单讲是HTTP的安全版；即HTTP下加入SSL层，HTTPS的安全基础是SSL，因此加密的详细内容就需要SSL。

### SSL/TLS

1. SSL 介绍

    > 安全套接字层 (SSL) 是一种加密安全协议。它最初由 Netscape 于 1995 年开发，旨在确保 Internet 通信中的隐私、身份验证和数据完整性。SSL 是如今使用的现代 TLS 加密的前身。

    - SSL 是指安全套接字层，简而言之，它是一项标准技术，是为网络通信提供安全及数据完整性的一种安全协议；
    - SSL协议位于TCP/IP协议与各种应用层协议之间，为数据通讯提供安全支持；

2. TLS 介绍

    ![http-vs-https](https://cdn.jsdelivr.net/gh/librarookie/Picgo/images/http-vs-https.png)

    > 传输层安全性（Transport Layer Security，TLS）是一种广泛采用的安全性协议，旨在促进互联网通信的私密性和数据安全性。TLS 的主要用例是对 web 应用程序和服务器之间的通信（例如，web 浏览器加载网站）进行加密。TLS 还可以用于加密其他通信，如电子邮件、消息传递和 IP 语音（VOIP）等。在本文中，我们将重点介绍 TLS 在 web 应用程序安全中发挥的作用。

    - TLS 其前身是 SSL，它最初的几个版本（SSL 1.0、SSL 2.0、SSL 3.0）由网景公司开发；
    - 1999年从 3.1 开始被 IETF 标准化并改名，发展至今已经有 TLS 1.0、TLS 1.1、TLS 1.2 三个版本；
    - SSL3.0和TLS1.0由于存在安全漏洞，已经很少被使用到。
    - 目前使用最广泛的是TLS 1.1、TLS 1.2。

3. TLS 和 SSL 联系

    - SSL 是TLS（传输层安全性）的协议的直接前身。
    - SSL 的最终版本（3.0）与 TLS 的第一版本之间并无明显差异，应用名称更改只是表示所有权改变。
    - SSL 由 Netscape 于 1995 年开发，并且在 1999 年，互联网工程任务组（IETF）提出了对 SSL 的更新，由于不再牵涉到 Netscape，因此名称更改为 TLS。
    - SSL 自 1996 年推出 SSL 3.0 以来未曾更新过，并且存在多个已知漏洞，现已弃用。实际上，大多数现代 Web 浏览器已彻底不再支持 SSL
    - 由于它们紧密地联系在一起，这两个术语经常互换使用并混为一谈。有些人仍然使用 SSL 来指代 TLS，其他人则使用术语“SSL/TLS 加密”，因为 SSL 仍然具有很大的知名度。
    - 由于许多人仍在搜寻“SSL 保护”，因此这个术语在许多产品页面上仍然处于醒目位置。但如今提供“SSL”的任何供应商提供的几乎肯定都是 TLS 保护

4. SSL/TLS 作用

- SSL/TLS 协议实现的功能有三个主要组成部分：加密、认证和完整性。
  - 加密：隐藏从第三方传输的数据。为了提供高度隐私，对传输的数据进行加密。这意味着，任何试图截取此数据的人都只会看到几乎无法解密的乱码字符。
  - 身份验证：在两个通信设备之间启动称为握手的身份验证过程，以确保两个设备确实是它们声称的真实身份。
  - 完整性：验证数据未被伪造或篡改。对数据进行数字签名，以提供数据完整性，验证数据是否在到达目标接收者之前被篡改过。

### HTTP

> HTTP（HyperText Transfer Protocol：超文本传输协议）是一种用于分布式、协作式和超媒体信息系统的应用层协议。 简单来说就是一种发布和接收 HTML 页面的方法，被用于在 Web 浏览器和网站服务器之间传递信息。

1. HTTP 是一个基于TCP/IP通信协议来传递数据的协议，传输的数据类型为HTML 文件,、图片文件, 查询结果等。

2. HTTP 协议以明文方式发送内容，不提供任何方式的数据加密，如果攻击者截取了Web浏览器和网站服务器之间的传输报文，就可以直接读懂其中的信息，因此，HTTP协议不适合传输一些敏感信息，比如：信用卡号、密码等支付信息。

3. HTTP特点：
    - http协议支持客户端/服务端模式，也是一种请求/响应模式的协议。
    - 简单快速：客户向服务器请求服务时，只需传送请求方法和路径。请求方法常用的有GET、HEAD、POST。
    - 灵活：HTTP允许传输任意类型的数据对象。传输的类型由Content-Type加以标记。
    - 无连接：限制每次连接只处理一个请求。服务器处理完请求，并收到客户的应答后，即断开连接，但是却不利于客户端与服务器保持会话连接，为了弥补这种不足，产生了两项记录http状态的技术，一个叫做Cookie,一个叫做Session。
    - 无状态：无状态是指协议对于事务处理没有记忆，后续处理需要前面的信息，则必须重传。

4. HTTP缺点
    - 请求信息明文传输，容易被窃听截取；
    - 数据的完整性未校验，容易被篡改；
    - 没有验证对方身份，存在冒充危险；

5. URI和URL的区别
    - HTTP使用统一资源标识符（Uniform Resource Identifiers, URI）来传输数据和建立连接。
    - URI： 统一资源标识符（Uniform Resource Identifier）
    - URL： 统一资源定位符（Uniform Resource Location）
    - URI 是用来标示 一个具体的资源的，我们可以通过 URI 知道一个资源是什么。
    - URL 则是用来定位具体的资源的，标示了一个具体的资源位置。互联网上的每个文件都有一个唯一的URL。

### HTTPS

> HTTPS（Hypertext Transfer Protocol Secure：超文本传输安全协议）是一种透过计算机网络进行安全通信的传输协议。HTTPS 经由 HTTP 进行通信，但利用 SSL/TLS 来加密数据包。HTTPS 开发的主要目的，是提供对网站服务器的身份认证，保护交换数据的隐私与完整性。

1. HTTPS 默认工作在 TCP 协议443端口，它的工作流程一般如以下方式：
    - TCP 三次同步握手
    - 客户端验证服务器数字证书
    - DH 算法协商对称加密算法的密钥、hash 算法的密钥
    - SSL 安全加密隧道协商完成
    - 网页以加密的方式传输，用协商的对称加密算法和密钥加密，保证数据机密性；用协商的hash算法进行数据完整性保护，保证数据不被篡改。

2. HTTPS缺点
    - HTTPS协议多次握手，导致页面的加载时间延长近50%；
    - HTTPS连接缓存不如HTTP高效，会增加数据开销和功耗；
    - 申请SSL证书需要钱，功能越强大的证书费用越高。
    - SSL涉及到的安全算法会消耗 CPU 资源，对服务器资源消耗较大。

3. HTTPS和HTTP的区别
    - HTTPS是HTTP协议的安全版本，HTTP协议的数据传输是明文的，是不安全的，HTTPS使用了SSL/TLS协议进行了加密处理。
    - http和https使用连接方式不同，默认端口也不一样，http是80，https是443。
    - 使用 HTTPS 协议需要到 CA（Certificate Authority，数字证书认证机构） 申请证书，一般免费证书较少，因而需要一定费用。证书颁发机构如：Symantec、Comodo、GoDaddy 和 GlobalSign 等。
    - HTTP 页面响应速度比 HTTPS 快，主要是因为 HTTP 使用 TCP 三次握手建立连接，客户端和服务器需要交换 3 个包，而 HTTPS除了 TCP 的三个包，还要加上 ssl 握手需要的 9 个包，所以一共是 12 个包。

</br>

## SSL 证书

![20220527175255](https://cdn.jsdelivr.net/gh/librarookie/Picgo/images/20220527175255.png)

> SSL 证书使得网站能够从 HTTP 转到更加安全的 HTTPS。SSL 证书是托管在网站源服务器中的数据文件。SSL 证书促成了 SSL/TLS 加密，它们含有网站的公钥和网站标识以及相关信息。尝试与源服务器通信的设备将引用此文件，以获取公钥并验证服务器的身份。私钥应保密并妥善保管。

### SSL 证书内容

SSL 证书包含以下信息：

- 针对其颁发证书的域名
- 证书颁发给哪一个人、组织或设备
- 证书由哪一证书颁发机构颁发
- 证书颁发机构的数字签名
- 关联的子域
- 证书的颁发日期
- 证书的到期日期
- 公钥（私钥为保密状态）

用于 SSL 的公钥和私钥本质上是用于加密和解密数据的长字符串。使用公钥加密的数据只能用私钥解密，反之亦然。

### SSL 证书作用

1. 互联网上的每个网站都应通过 HTTPS 提供服务。 原因如下：

- 性能：现代 SSL 实际上可以缩短页面加载时间。
- 搜索排名提升 ：搜索引擎偏爱 HTTPS 网站。
- 安全：使用 SSL 加密流量可确保任何人都无法窥探用户的数据。
- 信任：通过在浏览器的地址栏中显示绿色锁，SSL 增加了访问者的信任度。
- 合規性：SSL 是 PCI 合规性的关键组成部分。
- 加密：SSL 证书促成了公钥私钥配对。客户端（例如 Web 浏览器）从服务器的 SSL 证书获取打开 TLS 连接所需的公钥。
- 身份验证：SSL 证书可验证客户端正在与实际拥有该域的正确服务器进行通信。这有助于防止域欺骗和其他类型的攻击。

### SSL 自签名证书

[keytool命令生成证、管理数字证书](https://www.cnblogs.com/librarookie/p/16364384.html "Keytool配置 Tomcat的HTTPS双向认证")

</br>
</br>

Reference

- <https://zhuanlan.zhihu.com/p/72616216>
- <https://www.runoob.com/w3cnote/http-vs-https.html>
- <https://www.cloudflare.com/zh-cn/learning/ssl/what-is-an-ssl-certificate/>