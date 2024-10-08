##### 《计算机网络 自顶层向下方法》笔记
###### 第2章 应用层
`HTTP;TCP Web 流式多媒体`  
`SMTP;TCP 电子邮件`  
`FTP;TCP 文件传输`  
`Telnet;TCP 远程终端访问`  
`SIP/RTP/或专用;UDP/TCP 因特网电话`  

`应用` `应用层协议` `运输层协议`  
`Web 流式视频` `电子邮件` `文件传输` `目录服务DNS`  
`HTTP` `SMTP` `FTP` `Telnet`  

`进程通信` `客户-服务器` `对等P2P 自扩展性` `混合`  
`进程寻址` `套接字` `IP` `端口号`  

`运输层协议` `可靠数据传输` `安全性` `吞吐量` `定时`  
`分组丢失` `缓存溢出` `比特损坏` `加密传输` `解密交付`  
`带宽保证` `弹性应用` `带宽敏感` `自适应编码技术` `时延保证`  

`UDP` `无连接` `不可靠` `不控制`  
`TCP` `面向连接` `可靠传输` `拥塞控制` `全双工` `非持续连接`  
`SSL` `加密` `数据完整性检测` `端点鉴别`  

`Web` `HTML` `引用对象` `URL` `主机 路径`  
`HTTP TCP` `持续连接 默认`  
`三次握手` `发起TCP连接` `收到响应` `HTTP请求` `响应报文` `TCP关闭`  
`2次RTT` `排队时延` `处理时延` `传播时延`  

`HTTP 无状态协议`  
`初始请求` `标识码 数据库` `响应Set-cookie: 标识码`  
`浏览器cookie文件` `再次请求` `请求cookie: 标识码`  

`内容分发网络CDN` `代理服务器 Web缓存`  
`TCP初次请求` `缓存无副本` `TCP 请求` `初始服务器响应缓存` `副本` `缓存响应客户`  
`TCP再次请求` `缓存有副本` `缓存响应客户`  
`TCP时隔请求` `缓存有副本` `条件GET请求If-Modified-Science` `初始服务器` `响应缓存304 Not Modified` `缓存响应客户`    

`HTTP请求报文` `请求行` `首部行`  
`方法`sp`URL`sp`版本`cr lf    
`首部字段名`sp`值`cr lf   
cr lf 回车换行符  
`实体体` POST  

`HTTP响应报文` `状态行` `首部行` `实体体`  
`版本`sp`状态码`sp`短语`cr lf   
`首部字段名`sp`值`cr lf   
cr lf 回车换行符  
`实体体`  

`GET` `POST` `HEAD` `PUT` `DELETE`  
`cookie` `Host` `Connection` `User-agent` `Accept-language`  

`200 OK`  
`301 Moved Permanently`  
`400 Bad Request`  
`404 Not Found`  
`505 HTTP Version Not Surpported`  

`Set-cookie`  
`Connection`  
`Date`  
`Server`  
`Last-Modified`  
`Content-Length`  
`Content-Type`  

---
`电子邮件` `异步通信媒介`
`用户代理` `邮件服务器` `简单邮件传输协议SMTP` `报文队列`  
`SMTP TCP` `客户 服务器`
```
`端系统通信`：实际是端系统上`进程`通信。  
`同一端系统通信`：进程通信机制由`操作系统`规定。  
`客户-服务器进程`：发起通信进程是`客户`，等待联系进程是`服务器`。  
`P2P进程`：进程既是`客户`又是`服务器`。  

应用程序体系结构  
由服务器间接通信/直接通信 `客户-服务器` `对等P2P` `混合`  
`自扩展性` 对等方产生工作负载同时也为系统增加服务能力  

进程寻址：  
主机向主机进程发送分组，要目标识`目的主机`和`接收进程`。  
`主机`由`IP地址`标识，`接收进程`由`接收套接字`标识，  
因特网标准协议定义周知端口号`Web端口:80`，`邮件端口:25`。  

套接字：  
进程与运输层协议间的`接口`即`应用程序编程接口API`。  
发送端将报文推进`套接字`，接收端将报文从`套接字`取出。  
开发者可以控制套接字在应用层端的一切，但对运输层端少有控制权。  

```
```
网络运输协议与因特网运输协议：  
网络的运输协议服务包括四类，  
`可靠数据传输`、`吞吐量`、`定时`、`安全性`。  
`TCP`提供可靠的端到端数据传送，SSL加强以保证安全性。  
从`TCP/UDP`看，`因特网运输层`不提供`吞吐量`和`定时`保证服务。  
对于在因特网上运行的时间敏感应用，  
它们被设计成尽最大可能对付减少时延。  
`因特网`可以为时间敏感应用如因特网电话提供较好的服务，  
但它`不提供`任何`定时`或`带宽`保证。  
因特网的运输层协议服务：`TCP/UDP`  
运输层协议`TCP/UDP`本身没有加密机制。  
-----------------------------------------------
TCP服务：包括`面向连接`、`可靠数据传输`、`拥塞控制机制`。  
`TCP面向连接`：  
先握手建立连接，后传输数据，传输结束拆除连接。  
全双工，即双方进程可以在连接上同时收发报文。  
`TCP可靠数据传输`：  
无差错、按顺序收发全部数据。  
`TCP拥塞控制机制`：  
网络拥塞时，  
TCP拥塞控制会抑制发送进程客户或服务器，  
或限制TCP连接以使其公平共享网络带宽。  
`SSL`：  
使用安全套接字层`SSL`加强的TCP。  
提供安全性服务，包括`加密`、`数据完整性检测`、`端点鉴别`。  

`发送进程`将明文数据传给`发送端SSL`套接字加密，  
`发送端SSL`将加密数据传给`发送端TCP`套接字，  
`发送端TCP`将加密数据传给`接收端TCP`套接字，  
`接收端TCP`将加密数据传给`接收端SSL`进行解密。  
-----------------------------------------------
UDP服务：  
无连接，没有`握手过程`。  
提供`不可靠数据传输`，不一定或可能乱序收到报文。  
没有`拥塞控制机制`。  

因特网电话应用使用UDP，  
容忍一定丢失以达到一定速率，  
避开TCP的拥塞控制和分组开销。  
但由于大多防火墙被设置成阻挡多数类型的UDP流量，  
因此因特网电话应用常被设计成  
若UDP通信失败就使用TCP作为备份。  
-----------------------------------------------
运输层协议：开发应用时，必须选择其中一种。  
网络运输层协议服务分四类：`可靠数据传输`、`吞吐量`、`定时`、`安全性`。  

可靠数据传输：实现端到端数据准确完整传输。 
不可靠数据传输：多媒体应用、交谈式音视频能够接受一定量数据丢失。  
分组丢失：分组在路由器中缓存溢出，分组中比特损坏被丢弃。  
吞吐量：如因特网电话对语音以`32kbps`的速率进行编码。  
弹性应用：如邮件、文件传输、Web传送，能根据可用带宽利用吞吐量。  
带宽敏感应用：如多媒体应用，具有吞吐量要求。  
自适应编码技术：以与当前可用带宽相匹配的速率对数字音视频进行编码。  
定时：如发送方注入套接字的比特到达接收方套接字的时间不少于`100ms`。  
安全性：如发送方`加密传输`数据、接收方`解密交付`给进程。  
```

```
`应用层协议`是`网络应用`的部分：  
如Web是一种`客户-服务器`应用，  
Web由文档格式标准HTML、浏览器、服务器、应用层协议HTTP组成；  
如电子邮件是应用，  
由邮件服务器、邮件客户程序、  
定义邮件报文结构的标准、报文如何传递的应用层协议、  
解释报文首部信息的应用层协议SMTP组成。  
应用层协议：  
`应用层协议`定义了不同端系统上应用如何互传报文。  
包括报文类型、报文语法、字段语义、何时/如何发送/响应报文。  
有些由`RFC`文档定义的`应用层协议`位于公共域中，  
遵循`HTTP RFC`规则开发的浏览器  
能访问遵循该标准的服务器并获得Web页面；  
有些应用层协议是专用的，不为公共域使用。  
因特网应用：  
Web、文件传输、电子邮件、  
目录服务DNS、流式视频、P2P；  
```
```
Web和HTTP：  
Web应用层协议即`超文本传输协议HTTP`是Web的核心。  
Web页面：  
多数Web页面含有一个HTML基本文件和几个引用对象。  
对象是可以是HTML、JPEG图片、Java小程序、视频文件，通过URL地址寻址。  
URL由对象存储`服务器主机名`和`对象路径名`组成。如  
`http://www.someSchool.edu/someDepartment/picture.gif`，  
`www.someSchool.edu`为主机名，剩下为路径名。  

`HTTP`使用`TCP`作为`运输协议`，`提供`可靠数据传输`服务，  
浏览器向服务器发起连接，浏览器和服务器进程通过套接字访问TCP，  
请求报文脱离了客户控制进入TCP控制，体现分层体系结构特点，
HTTP不用关注TCP恢复数据丢失和乱序的细节。  

HTTP的TCP连接：  
HTTP默认使用`持续连接`，也能使用`非持续连接`。  
`非持续连接`，每个请求经单独的TCP连接发送，  
`持续连接`，所有请求经相同的TCP发送。  
HTTP采用持续TCP连接：  
服务器在发送响应报文后保持TCP连接，  
相同客户与服务器间或相同服务器上多个Web页面
持续和请求响应可共用一个TCP连接，  
通常，一定时间未被使用的连接会自动关闭。  
HTTP/2是HTTP 1.1改版，  
允许在相同连接中交错多个请求与响应。  
```
```
HTTP采用非持续TCP连接：
服务器向客户传送一个Web页面，  
页面包括1个HTML基本页面和10个JPEG图片共11个对象，  
HTML文件的URL为  
`http://www.someSchool.edu/someDepartment/home.index`  

对于10个JPEG图片的TCP连接，并行连接可以缩短响应时间。   
用户可以配置浏览器以控制连接的并行度，默认开启5~10个并行TCP连接，
设置最大并行连接数为1，就会串行连接。  
本次请求要产生11个TCP连接，每个TCP连接只传输一个请求和响应报文，  
完毕后连接关闭。  

非持续连接的缺点：  
为每一个请求对象建立全新的连接，  
客户和服务器都要分配TCP的缓冲区并保持TCP变量，  
对同时服务于数以百计客户请求的服务器来说负荷太重。  
每个对象都要经受两倍RTT交付时延，  
一个用于创建TCP连接，一个用于请求和接收对象。  

（1）  
客户进程在默认端口号80  
向服务器`www.someSchool.edu`发起TCP连接。  
（2）  
客户向服务器发送HTTP请求报文，  
报文包含路径名`/someDepartment/home.index`。  
（3）  
服务器经套接字接收到请求报文，从存储器RAM或磁盘中检索出  
对象`www.someSchool.edu/someDepartment/home.index`，  
将其封装到响应报文中，通过套接字发送给客户。  
（4）  
服务器通知TCP断开该TCP连接，  
确认客户完整收到响应报文，  
TCP连接关闭。  
（5）  
客户从响应报文中提取出HTML文件，  
得到对10个图片的引用，  
对每个引用的图片重复前面步骤。  
-----------------------------------------------
往返时间RTT：  
一个分组从客户到服务器再返回客户的时间。  
`RTT`包括`传播时延`、`排队时延`、`处理时延`。  
用户点击超链接，  
浏览器和Web服务器建立TCP连接，涉及`三次握手`。  
客户向服务器发送一小段TCP报文，  
服务器向客户发送一小段TCP响应报文，  
客户向服务器发起确认以及正式请求，  
三次握手后，服务器向客户发送请求的HTML对象。  
三次握手的前两次占用一个`RTT`，  
正式请求和回传文件占用另一个`RTT`，  
`总响应时间`可视为`两个RTT`加上`传输HTML文件`的时间。  
```
```
cookie：  
HTTP是一种`无状态协议`：  
服务器不会区别在短时间内来自同一个客户的重复请求，  
而是把每次请求当作全新的请求，每次都会重新发送被请求的对象。  
Web站点通过`cookie`识别、跟踪用户。  
四个组件：  
`HTTP请求报文cookie首部行`、`响应报文Set-cookie首部行`、  
Web站点`后端数据库`、用户端系统浏览器管理的`cookie文件`。  

用户首次访问站点时，需要提供一个用户标识，  
后继会话中，浏览器向服务器发送cookie信息，  
允许服务器在用户活动中标识该用户。  
（1）  
用户的请求报文达到服务器，  
Web站点产生唯一标识码，  
后端数据库产生一个表项，  
服务器用发送响应报文到浏览器，  
响应报文首部行包含`Set-cookie: 1678`。  
（2）  
浏览器获得首部行`Set-cookie: 1678`，  
在它管理的cookie文件中添加一行信息，  
包括服务器主机名和首部行中的识别码`1678`。  
（3）  
用户继续浏览服务器，每请求一个Web页面，  
浏览器就会查询cookie文件并提取识别码`1678`，  
放到HTTP请求报文首部行`cookie: 1678`中。  
```

```
Web缓存：  
也叫`代理服务器`，代理`初始服务器`满足客户的HTTP请求。  
`Web缓存器`有自己的磁盘存储空间，保存最近请求对象的副本。  
可配置浏览器使对某对象的请求首先被定向到Web缓存器。  
`Web缓存器`既是服务器也是客户。  
`Web缓存器`通常由ISP购买并安装。  
`内容分发网络CDN`：  
CDN公司在因特网上安装了许多地理上分散的缓存器，  
使大量流量实现了本地化。  

某浏览器向服务器请求某对象：  
（1）  
`浏览器`创建到`Web缓存器`的TCP连接，  
向`Web缓存器`发送HTTP请求。  
（2）  
`Web缓存器`检查是否存储了对象副本，  
若存在，向`浏览器`返回该对象。  
（3）  
若不存在，  
`Web缓存器`与`初始服务器`建立TCP连接并发送请求，  
`初始服务器`向`Web缓存器`返回HTTP响应报文以及对象。  
（4）  
`Web缓存器`在本地创建对象副本，  
向`浏览器`发送包含副本的HTTP响应报文。  
```
```
`机构网络`是个`100Mbps`高速局域网，  
与因特网`初始服务器`以`15Mbps`的链路连接，  
对象平均长`1Mb`，  
机构浏览器访速`每秒15个请求`，  
假设HTTP请求报文足够小不产生通信量。  
`因特网时延`即路由器转发HTTP请求报文到收到响应报文的时间平均为`2秒`，  
`总响应时间`即从浏览器请求到接收到对象的时间，  
等于`局域网时延`、`接入时延`、`因特网时延`之和。  

则`局域网流量强度`为  
`（15个请求/秒）* （1Mb/请求）/100Mbps = 0.15`，  
从因特网路由器到机构路由器即`接入链路流量强度`为  
`（15个请求/秒）*（1Mb/请求）/15Mbps = 1`。  
`局域网上流量强度`为0.15最多导致数十毫秒的时延，可忽略。  
`接入链路流量强度`接近1，会导致非常大的时延并无限增长。  
为改进时间响应特性  

方案一，`增加接入链路速率`，将15Mbps改为100Mbps，  
流量强度可以减少至0.15，但此种方案代价较高。  

方案二，不升级链路带宽，`安装Web缓存器`，  
Web缓存器满足的请求比率为`0.2~0.7`，  
取命中率为0.4，由于客户和缓存连接在相同的高速局域网上，  
40%的请求能立即得到缓存器响应，时延在10ms以内，  
60%的请求需要初始服务器来满足，接入链路流量由1减小到0.6，  
通常，15Mbps链路上流量强度小于0.8时的时延较小，为几十毫秒。  
则平均时延为`0.4*0.01秒+0.6*2.01秒`略大于1.2秒，  
此方案可以获得比方案一更低的时延，  
机构无需升级到因特网的接入链路，  
安装Web缓存器的成本是较低的。  

`Web缓存器`可以减少客户请求响应时间，  
当客户与初始服务器间瓶颈带宽远低于客户与Web缓存器间瓶颈带宽时更是如此。  
`Web缓存器`可以减少接入链路到因特网的通信量，  
减少了通信量即不必急于增加带宽，也就减少了费用。  
```
```
条件GET方法：  
Web缓存器保存的是对象的副本，  
HTTP机制的`条件GET方法`可保证对象副本版本维持最新。  
使用GET的请求报文包含了首部行`If-Modified-Science`，  
则称此HTTP请求报文是一个`条件GET请求报文`。  
（1）代理浏览器的缓存器向Web服务器发送请求报文：  
GET /fruit/kiwi.gif HTTP/1.1  
Host: www.exotiquecuisine.com
（2）Web服务器返回响应报文给缓存器： 
HTTP/1.1 200 OK  
Date: Sat, 3 Oct 2015 15:39:29  
Server: Apache/1.3.0 (Unix)  
Last-Modified: Wed, 9 Sep 2015 09:23:24  
Content-Type: image/gif

(data data data data data ...)  
（3）缓存器将对象以及最后修改时间备份，转发给浏览器。  
（4）一星期后，另一用户再次请求该对象时，期间对象可能已被修改，  
缓存器发送一个条件GET执行最新检查： 
GET /fruit/kiwi.gif HTTP/1.1  
Host: www.exotiquecuisine.com  
If-modified-science: Wed, 9 Sep 2015 09:23:24
其中GET条件请求的If-modified-science
等于服务器最近响应缓存器的Last-Modified
（5）假设对象自上次响应未被修改，服务器返回响应报文给缓存器：
HTTP/1.1 304 Not Modified  
Date: Sat, 10 Oct 2015 15:39:29  
Server: Apache/1.3.0 (Unix)  

(empty entity body)
但响应报文中不再包含对象实体体，避免浪费带宽以及增加时延。
304 Not Modified 指示缓存器可以向用户发送对象副本。
（6）缓存器将对象副本发送给浏览器。
```  
```
HTTP请求报文：  
`GET /somedir/page.html HTTP/1.1`  
`Host: www.comeschool.deu`  
`Connection: close`  
`User-agent: Mozilla/5.0`  
`Accept-language: fr`  

HTTP请求报文通用格式：  
`方法` `sp` `URL` `sp` `版本` `cr` `lf` 请求行  
`首部字段名` `sp` `值` `cr` `lf` 首部行  
`cr` `lf` 回车换行符  
`实体体`  
-----------------------------------------------
`请求行`
方法字段可为`GET`、`POST`、`HEAD`、`PUT`、`DELETE`。  
`首部行` `Host: www.comeschool.deu`  
标识主机  
`首部行` `Connection: close`  
采用非连续的TCP连接，要求发送完被请求对象后关闭连接  
`首部行` `User-agent: Mozilla/5.0`  
标识用户代理即客户浏览器的类型，  
此处为Mozilla/5.0即Firfox浏览器，  
服务器会根据客户浏览器版本的不同发送不同版本的对象。  
`首部行` `Accept-language: fr`  
表示用户期望得到对象的法语版本，  
若服务器没有此版本则发送默认版本。  
-----------------------------------------------
使用`GET`方法，`实体体`为空，  
使用`POST`方法，`实体体`为用户输入。  
`用户提交表单`常使用`POST`以及`实体体`。  
`用户提交表单`也可以不使用`POST`而使用`GET`，  
`HTML`表单用`GET`方法，用户数据常被包含在`URL`中。  
如一个表单包含`monkeys` `bananas`并使用`GET`，  
则URL为`www.somesite.com/animalsearch? monkeys&bananas`  
`HEAD`方法，  
类似于`GET`，
服务器收到使用`HEAD`方法请求时，  
将会使用一个HTTP报文进行相应，而不返回对象，  
开发者常使用`HEAD`方法进行调试跟踪。  
`PUT`方法，  
常与Web工具联合使用，  
允许用户上传对象到指定Web服务器的指定路径。  
`DELETE`方法，  
允许用户删除Web服务器上的对象。  
```

```
HTTP响应报文：  
`HTTP/1.1 200 OK`  
`Connection: close`  
`Date: Tue, 18 Aug 2015 15:44:054 GMT`  
`Server: Apache/20203 (CentOS)`  
`Last-Modified: Tue, 18 Aug 2015 15:11:03 GMT`  
`Content-Length: 6821`  
`Content-Type: text/html`  

`(data data data data data ...)`  

HTTP响应报文通用格式：  
`版本` `sp` `状态码` `sp` `短语` `cr` `lf` 状态行  
`首部字段名` `sp` `值` `cr` `lf` 首部行  
`cr` `lf` 回车换行符  
`实体体`  
-----------------------------------------------
`状态行` `HTTP/1.1 200 OK`  
服务器正在使用HTTP/1.1，  
且服务器找到并发送正请求的对象。  
`首部行` `Connection: close`  
发送完报文后关闭连接。  
`首部行` `Date: Tue, 18 Aug 2015 15:44:054 GMT`  
服务器产生并发送响应报文的日期和时间。  
`首部行` `Server: Apache/20203 (CentOS)`  
指示报文是由一台Apache Web服务器产生的，  
类似于HTTP请求报文中的`User-agent`。  
`首部行` `Last-Modified: Tue, 18 Aug 2015 15:11:03 GMT`  
对象创建或最后修改的日期和时间。  
`首部行` `Content-Length: 6821`  
被发送对象中的字节数。  
`首部行` `Content-Type: text/html`  
指示`实体体`中的对象是HTML文本。  
-----------------------------------------------
状态码及其短语：  
`200 OK`   
请求成功，信息在响应报文中返回。  
`301 Moved Permanently`   
请求的对象已被永久转移，新的URL定义在首部行`Location`中，客户程序自动获取新的URL。  
`400 Bad Request`   
请求不能被服务器理解。  
`404 Not Found`   
请求的文档不在服务器上。  
`505 HTTP Version Not Surpported`   
服务器不支持请求报文使用的HTTP协议版本。  
```
---
```
异步通信媒介：当人们方便时就可以向他人发送邮件，不必与他人的计划协调。
邮件系统：用户代理、邮件服务器、简单邮件传输协议SMTP，Simple Mail Transfer Protocol  
报文队列：用户代理传输邮件到发送方的邮件服务器，再传输到接收方邮件服务器，然后分发到接收方的邮箱中。若A不能将邮件传给B服务器，则在A服务器的报文队列中保持邮件报文，通常每30min进行一次尝试再次发送，若几日后仍不成功，则服务器删除该报文，并以邮件通知到A。

```