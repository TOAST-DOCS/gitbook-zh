## Network > Load Balancer > 概要

NHN Cloud 负载均衡优点如下:

- 一个实例难以处理的负荷，可通过数台实例分散处理增加处理能力。
- 通过将已出现故障或检查中的实例自动地从服务器池中隔离，提高可用性。

## 负载均衡（load Balancing）调度算法

负载均衡共支持三种负载均衡调度算法。

* Round Robin(轮询): 按照访问顺序依次将外部请求依序分发到后端实例，属于最基本的负载均衡调度算法。是所有后端实例对相同请求做出相同回应的情况下所能使用的调度算法。

* Least Connections(最少连接): 是选择目前 TCP 连接数最少的后端实例的调度算法。即，以 TCP 连接数为标准，参考所有实例的负载状态，将连接请求转发到连接数最少的后端实例，确保能尽量均等地处理请求。这种方式可以防止负载集中到特定实例（instance）的现象发生。

* Source IP(源IP地址):根据请求的源IP选择进行处理的后端实例。使用该方式时，可以保证同一源IP的请求总是负载分发到后端同一实例进行处理，可以确保同一源IP的请求总是负载分发到后端同一实例进行处理。


## 支持的协议

负载均衡支持的协议类型如下。

* TCP
* HTTP
* HTTPS
* TERMINATED_HTTPS

上述协议中，TERMINATED_HTTPS协议是指接收HTTPS数据后，再以 HTTP 数据向后端实例（instance）进行传输的方式。使用 TERMINATED_HTTPS 协议时，最终用户与负载均衡之间，以 HTTPS方式进行通信来确保较高的安全性，而向服务器传输 HTTP 数据可减少译码所需 CPU 负荷。

> [参考] 要想使用TERMINATED_HTTPS 协议，则需将认证书与私有密钥(private key)注册于负载均衡。此时所注册的私有密钥必须解除密码才能正常工作。

## 负载均衡SSL/TLS版本
* 创建使用TERMINATED_HTTPS协议的负载均衡时，可选择客户与负载均衡之间通信使用的SSl(Secure Socket Layer)/TLS(Transport Layer Security)版本。
* 若SSL/TLS协议版本低，则可能存在安全漏洞，构成密码套件(Cipher Suite)的密码算法的安全性也较低，因此最好选择客户支持的TLS版本中最高版本的SSL/TLS。
* NHN Cloud负载均衡正在为支持TLSv1.3进行准备。

### TLS版本
从TLS版本中选择一个创建负载均衡。创建的负载均衡仅使用如下选择的版本与比所选版本更高级的版本与客户通信。

| SSL/TLS版本设置 | 负载均衡使用的TLS版本 |
| -- | -- |
| SSLv3 | SSLv3, TLSv1.0, TLSv1.1, TLSv1.2 |
| TLSv1.0 | TLSv1.0, TLSv1.1, TLSv1.2 |
| TLSv1.0_2016 | TLSv1.0, TLSv1.1, TLSv1.2 |
| TLSv1.1 | TLSv1.1, TLSv1.2 |
| TLSv1.2 | TLSv1.2 |

### SSl/TLS各版本密码套件
* 客户与负载均衡之间密钥交换、证书验证、信息加密、信息无缺陷检查等HTTPS通信使用的密码算法的集合称为密码套件。
* 根据SSL/TLS版本使用的密码套件如下。
* 若选择高版本的TLS版本，不使用应用安全性较低的算法的密码套件。

| SSL/TLS版本设置 | 使用的密码套件 | 备注 |
| -- | -- | -- |
| SSLv3 | ECDHE-RSA-AES128-GCM-SHA256<br>ECDHE-RSA-AES128-SHA256<br>ECDHE-RSA-AES128-SHA<br>ECDHE-RSA-AES256-GCM-SHA384<br>ECDHE-RSA-AES256-SHA384<br>ECDHE-RSA-AES256-SHA<br>AES128-GCM-SHA256<br>AES256-GCM-SHA384<br>AES128-SHA256<br>AES256-SHA<br>AES128-SHA<br>DES-CBC3-SHA<br>RC4-MD5 | |
| TLSv1.0 | ECDHE-RSA-AES128-GCM-SHA256<br>ECDHE-RSA-AES128-SHA256<br>ECDHE-RSA-AES128-SHA<br>ECDHE-RSA-AES256-GCM-SHA384<br>ECDHE-RSA-AES256-SHA384<br>ECDHE-RSA-AES256-SHA<br>AES128-GCM-SHA256<br>AES256-GCM-SHA384<br>AES128-SHA256<br>AES256-SHA<br>AES128-SHA<br>DES-CBC3-SHA | RC4-MD5除外 |
| TLSv1.0_2016 | ECDHE-RSA-AES128-GCM-SHA256<br>ECDHE-RSA-AES128-SHA256<br>ECDHE-RSA-AES128-SHA<br>ECDHE-RSA-AES256-GCM-SHA384<br>ECDHE-RSA-AES256-SHA384<br>ECDHE-RSA-AES256-SHA<br>AES128-GCM-SHA256<br>AES256-GCM-SHA384<br>AES128-SHA256<br>AES256-SHA<br>AES128-SHA | DES-CBC3-SHA除外 |
| TLSv1.1 | ECDHE-RSA-AES128-GCM-SHA256<br>ECDHE-RSA-AES128-SHA256<br>ECDHE-RSA-AES128-SHA<br>ECDHE-RSA-AES256-GCM-SHA384<br>ECDHE-RSA-AES256-SHA384<br>ECDHE-RSA-AES256-SHA<br>AES128-GCM-SHA256<br>AES256-GCM-SHA384<br>AES128-SHA256<br>AES256-SHA<br>AES128-SHA | 相同 |
| TLSv1.2 | ECDHE-RSA-AES128-GCM-SHA256<br>ECDHE-RSA-AES128-SHA256<br>ECDHE-RSA-AES256-GCM-SHA384<br>ECDHE-RSA-AES256-SHA384<br>AES128-GCM-SHA256<br>AES256-GCM-SHA384<br>AES128-SHA256 | ECDHE-RSA-AES128-SHA<br>ECDHE-RSA-AES256-SHA<br>AES256-SHA<br>AES128-SHA除外 |


## 创建负载均衡

负载均衡创建在 [VPC](/Network/VPC/zh/overview/#_2)的[子网](/Network/VPC/zh/overview/#_2)上。负载均衡在创建时从指定的子网获得IP之后，作为自己的IP使用。并且，将属于VPC（与所指定子网相同的）的实例，作为成员实例添加到服务器池，分配所流入的流量。同时应注意，无法添加属于其他 VPC的实例。

应在监听中定义负载均衡处理访问流量的转发策略。按监听分类定义接收流量的端口与协议，实现利用一个负载均衡处理不同种类流量的架构。通常设置的协议和端口分别为HTTP 80端口以及HTTPS 443端口。可以在一个负债均衡器登录多个listener。

> [注意] 在负载均衡中，无法创建重复使用相同端口的监听。

## 代理服务器方式

负载均衡以“代理服务器方式”运行。客户端为了发出请求与负载均衡建立连接，负载均衡则与实例服务器建立连接。对于成员实例服务器，会话的源(Source) IP被视为负载均衡的IP。要验证服务器上客户端的IP，应参考负载均衡添加的X-Forwarded-For header中的信息，或使用(HTTP/TERMINATED_HTTPS协议) Proxy Protocol(TCP/HTTPS协议)。

> [参考] 代理服务器方式 <br>
> 是L4负载均衡运行方式的一种，是指服务器的回应通过负载均衡传达至客户端。即，负载均衡将与客户端进行 TCP 连接，再与服务器进行 TCP 连接。
>
> 负载均衡以代理服务器方式运行时，客户端所请求的端口，有可能与后端服务器监听的端口不同。同时，即便不属于相同的子网，也可将实例添加到负载均衡。
>
> 相反，因客户端与负载均衡之间，及负载均衡与服务器之间进行两次连接，所以导致造成资源浪费。换言之，为了进行一个连接每次都会消耗两个负载均衡所能使用的端口。同时，在后端服务器中，难以识别客户端IP。为了克服上述内容，可以使用添加了X-Forwarded-For的 HTTP header或者使用负载均衡所提供的Proxy Protocol
<br>

> [参考] X-Forwarded-For header<br>
>作为HTTP非标准header，服务器为了确认客户端 IP 而使用。
通过负载均衡进入的 HTTP 请求，包括 **X-Forwarded-For** 键，其值为客户端 IP。
>
> X-Forwarded-For header只在将负载均衡的协议设置为 HTTP/TERMINATED_HTTPS 时才可使用。

<br>

> [参考] 代理服务器协议(proxy protocol) <br>
> 是用于负载均衡使用 TCP 时，传送客户端的 IP信息的协议，为了便于理解，以US-ASCII格式文本化的方式呈现。实现 TCP 连接后最初传送一次，并在接收方全部接收为止，其他数据传送将被推迟。
>
> 代理服务器协议可大致分为 6个项目。各项目以空白文字区分。
> 最后的文字须以 Carriage Return (\r) + Line Feed (\n)结束。
>  ```
>  PROXY INET_PROTCOL CLIENT_IP PROXY_IP CLIENT_PORT PROXY_PORT\r\n
>  ```
>
> | 简称 | ASCII | HEX | 说明 |
> |--|--|--|--|
> | PROXY | "PROXY" | 0x50 0x52 0x4F 0x58 0x59 | 为了告知此处使用代理服务器协议|
> | INET_PROTOCL | "TCP4" 或者 "TCP6" | 0x54 0x43 0x50 0x34 或者 0x54 0x43 0x50 0x36 | 使用中的 INET 协议类型|
> | CLIENT_IP | 例) "192.168.100.101" <br> 或者 "fe80::a159:b1f3:c346:5975" | 0xC0 0xA8 0x64 0x65 | 源IP地址|
> | PROXY_IP | 例) "192.168.100.102" <br> 或者 "fe80::a159:b1f3:c346:5976" | 0xC0 0xA8 0x64 0x66 | 目的IP地址 |
> | CLIENT_PORT | 例) "43179" | 0xA8 0xAB | 源端口 |
> | PROXY_PORT | 例) "80" | 0x80 | 目的端口 |
>
> 代理服务器协议的样例如下：
>
>- "PROXY TCP4 255.255.255.255 255.255.255.255 65535 65535\r\n": TCP/IPv4
>- "PROXY TCP6 ffff:f...f:ffff ffff:f...f:ffff 65535 65535\r\n": TCP/IPv6
>- "PROXY UNKNOWN\r\n": 未知连接

## 连接限制

负载均衡为了QoS保障，而限制着每个监听可以同时维持的连接数。若请求超过指定连接限制值，则将按负载均衡内部队列顺序处理），并在之前的请求结束之后再被处理。同时，因线索充满或服务器/客户端的超时（time-out）而请求有可能被强制性地中断。此类情况，客户端将被无限延迟。随之，应慎重选择所使用的负载均衡连接限制数值。

> [参考] 标准型负载均衡的最大会话连接数为60,000，专用型为480,000，您可以根据此范围来设置会话连接数。

## 会话保持

需要保持用户请求,或者满足某个客户端的请求转发给特定后端实例的需求，可使用负载均衡的会话保持功能。此功能可确保同一客户端请求转发到同一后端实例处理，由于会话保持是基于客户端源IP来确定的，因此，若选择负载均衡方式为SOURCE IP时，则提供会话保持特性。如果负载均衡方式使用的是ROUND ROBIN或LEAST CONNECTION，则可以使用以下会话保持功能

* No Session Persistence(不维持会话): 是不维持会话的方式。

* Source IP(基于源IP地址): 是基于源IP地址为基准维持对话的方式。为此，在最初请求时，对通过负载均衡选择的实例与原IP之间的变换表（mapping table）进行内部保管。此后，如果接收到拥有相同源IP的请求，则将在确认变换表之后再向给第一个请求做出回应的实例进行传送。负载均衡最多可保存10,000个源IP的session。
如果在TCP协议监听中设置会话保持时，则应使用该方式。

* APP Cookie(按应用程序管理会话): 通过服务器转发的，明文cookie设置保持session的方法。最初请求时，服务器为了自身设置的cookie值生效，通过HTTP的 **Set-Cookie** header进行转发。此时，负载均衡检查服务器回应中是否存在指定的cookie，如果cookie 存在，则将在内部维持cookie与服务器 ID 之间的对应关系。此后，客户端将特定服务器指定的cookie值添加到**Cookie**  header中发送，则负载均衡将向对应于cookie的服务器转发请求。在负载均衡中，未使用的cookie与服务器 ID 之间的对应关系时间超过3小时时将自动删除。

* HTTP Cookie(按负载均衡管理会话): 虽然与APP Cookie 方式类似，但这是一种通过负载均衡中自动设置cookie来维持对话的方式。负载均衡将对服务器的回应，添加名为**SRV**的cookie之后进行转发。此时，**SRV** cookie值为每个服务器所对应的固有ID。客户端将**SRV**放入到cookie后再转发时，则向首次回应的服务器转发请求。

> [参考] 在负载均衡可以设置TCP会话保持时间。可以通过设置Keepalive timeout值来调整负载均衡针对客户端和与服务器之间的会话保持时间。

## 实例状态确认(health check)

NHN Cloud 负载均衡，为了确认后端的众多实例工作是否正常，按计划进行周期性的状态确认。所谓的状态确认是指，既定回应是否按照所指定的协议传输。如果在指定的次数或时间之内，未收到正常回应，则看作非正常实例，并暂时停止向该实例转发请求。通过该功能，在无法预测的故障或检查中断情况下也能提供服务。

负载均衡，通过状态确认协议支持（或提供）TCP, HTTP, HTTPS。为了进行详细的状态确认，使用各自的协议时，可设置多种状态确认方法。

## 负载均衡统计功能

负载平衡处理的网络流量相关的各种统计指标可以通过图表确认。NHN Cloud负载均衡统计功能的特点如下。

* 提供负载均衡、监听的统计图表。
* 可以按1个小时，24小时，1周，1个月等期间区分查看。
* 基于负载均衡，在不同的图表中提供客户端统计和实例端统计的功能。
* 实例端统计可以按成员实例区分查看，也可以只查看汇总结果。（按实例查看：ON / OFF）

提供的图表如下。

| 统计指标名称<br>(图表名) | 区分 | 单位 | 说明 |
|--|--|--|--|
| 客户端会话数 | 客户端 | ea | 负载均衡当前与客户端的连接数 |
| 客户端会话CPS | 客户端 | cps<br>(connections per second) | 与客户端每秒新建连接数 |
| 会话CPS | 实例端 | cps<br>(connections per second) | 与实例端每秒新建连接数 |
| 流量 In | 实例端 |  bps<br>(bits per second) | 负债均衡发送给实例的流量 |
| 流量Out | 实例端 | bps<br>(bits per second) | 实例发送给负债均衡的流量 |
| 负载均衡排除数 | 实例端 | ea | 因健康检查失败，让负载均衡自动排除健康状况异常的后端服务器的数量 |

> [参考] 限制事项及参考事项
>
> * 仅对目前使用中的负载均衡、监听、成员提供统计图表。当删除负债均衡资源时，将不再提供该资源的历史统计数据。
> * 根据在单位为ea的图表中设置的期间，数字的含义可能会有所不同。请把鼠标拖到个别图表上端的问号即可确认数字的含义。
> * 流入流出等网络流量使用量相关指标图表中的数据，除L2,L3,L4 Head的Payload流量大小除以单位时间的数据。因此，图表中显示的数据与收费数据无关。
> * 统计数据最长提供1年。

## 负载均衡IP访问控制功能

若欲控制流入负载均衡的数据包，可使用IP访问控制功能。
该功能不同于[安全组](/Network/VPC/zh/console-guide/#_6)的功能，区别如下。

> [参考] 安全组与负载均衡IP访问控制功能比较
>
> | 分类 | 安全组 | 负载均衡IP访问控制 | 备注 |
> |--|--|--|--|
> | 控制对象 | 实例 | 负载均衡 | |
> | 设置对象 | IP、端口设置 | 仅设置IP | 默认阻止负载均衡中设置的端口以外的流量 |
> | 控制流量 | 可选择流入/流出<br>流量 | 仅流入流量为控制对象 |
> | 访问控制类型 | 仅设置允许策略 | 可选择允许或阻止策略 |

安全组设置与负载均衡IP访问控制设置互不影响。因此，若欲控制流入及流出实例的流量，则使用安全组，若欲控制流入负载均衡的流量，应使用IP访问控制
功能。

若欲使用IP访问控制功能，应设置如下事项。

### IP访问控制组
* 一个项目最多可以创建 10 个组。
* 组属性为名称、备忘录、访问控制类型。
* 访问控制类型属性可以在“允许(Allow)”与“阻止(Deny)”中设置一种。
* 可以在访问控制组中添加想要控制的IP访问控制对象。
* 若删除IP访问控制组，将删除组中所有IP访问控制对象，不控制应用该访问控制组的所有负载均衡中的IP。

### IP访问控制类型
* “允许(Allow)”：<b>允许</b>组中IP的访问，<b>阻止</b>其他所有IP的访问。
* “阻止(Deny)”：<b>阻止</b>组中IP的访问，<b>允许</b>其他所有IP的访问。
> [注意]
> 若欲在负载均衡中应用“允许”类型的访问控制组，应将负载均衡的成员实例IP添加到访问控制对象。


### IP访问控制对象
* 一个项目中最多可创建1,000个访问控制对象。
* 访问控制对象具有备忘录、IP地址等属性。
* 一个访问控制对象可以具有IP地址或CIDR形式的IP地址范围。若输入CIDR形式的IP地址范围，相应网络中的所有段则都包含在访问控制对象中。

> [参考]
> 若使用[NHN Cloud Security Monitoring](/Security/Security%20Monitoring/zh/Overview/)服务，可以找出具有威胁性的远程IP。
>
> 若创建将IP访问控制类型设置为“阻止”的IP访问控制组，并将发现的具有威胁性的远程IP添加至访问控制对象，可提高系统的安全性。
>

### 应用IP访问控制组
* 一个访问控制组可以应用于多个负载均衡。
* 一个负载均衡中可以应用多个访问控制组。但绑定的组的访问控制类型应相同。
* 未应用IP访问控制组的负载均衡允许所有IP的访问。

> [参考]
> 
> * 在更改负载均衡与IP访问控制时操作
>     * 若删除负载均衡，访问控制绑定也将被删除。访问控制组不会被删除。
>     * 若删除访问控制组，相应明细反映到与组绑定的所有负载均衡中。
>     * 若在访问控制组中添加或删除访问控制对象，相应明细反映到与组绑定的所有负载均衡中。


## 收费

负载均衡收费标准，可大致分为两种。

 * 负载均衡使用费用: 只要负载均衡的状态处于ACTIVE状态，将收取使用期间的费用。有关使用费的详细信息，请参考[负载均衡类型费用](/service/network/load_balancer)。
 * 负载均衡流量费用: 把从负载均衡中传出的流量加到项目的全部流量后，一并收取。


