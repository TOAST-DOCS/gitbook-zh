## Network > VPC >控制台的使用指南

在控制台对 VPC进行操作时所需内容，下文将对此进行说明。

## VPC

VPC中可以划分多个子网，因此在使用的时候，应设定足够大的网络地址。划分VPC网络的方法，可以参考[CIDR Notation](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)。所有VPC应属于[私有网络](https://en.wikipedia.org/wiki/Private_network)的下述3个地址段中，本地链接地址段无法使用。同时，划分应至少大于24bit-256个的网络地址的网络地址段。

### 私有网络

RFC1918 | IP地址段 | 可以使用的地址个数
-------- | ---------- | -----------------
24bit block | 10.0.0.0/8 | 16,777,216
20bit block | 172.16.0.0/12 | 1,047,576
16bit block | 192.168.0.0/16 | 65,536

###本地链接地址段

169.254.0.0/16的65,536个IP地址，属于本地地址，不可使用。

### 示例

例 | 是否可以使用
-------- | ----------
10.0.0.0/8 | 可以使用。
10.0.0.0/16 |可以使用。
10.0.0.0/24 |可以使用。
10.0.0.0/28 |不可使用。范围过小。
172.16.0.0/16 |可以使用。
172.16.0.0/8 | 不可使用。已超出可以使用的范围。
192.168.0.0/16 |可以使用。将被指定为基本使用范围。
192.168.0.0/24 |可以使用。
192.253.0.0/24 |不可使用。已超出可以使用的范围。

<br>


如果使用了Compute 和 Network的商品，以下项目将会自动生成一些默认配置。

项目 | 名称 | 概要
-------- | ---------- | --------------
VPC | Default Network | 自动创建1个192.168.0.0/16范围的 VPC。
子网 | Default Network | 自动创建1个192.168.0.0/24范围的子网。
路由表（routing table） | vpc-[id] | 自动创建1条含有部分VPC ID名称的路由表。
NAT网关 | ig-[id] | 自动创建1个含有部分路由表ID名称的NAT网关。
安全组（group）| default | 自动创建1个名为default的安全组。

添加VPC时，以下项目将会自动生成一些默认配置。

项目 | 名称 | 概要
-------- | ---------- | --------------
VPC | 自定义的名称 | 创建1个自定义范围的VPC。
子网 | - | 不会自动创建
路由表 | vpc-[id] | 自动创建1个含有部分VPC ID名称的路由表。
NAT网关 | - | 不会自动创建，所以需要自行创建和绑定。
安全组 | - | 不会自动创建。

VPC与各项目之间的使用配额(quota)如下：

项目 | 最大值
-------- | ----------
VPC | 3
子网 | 10
互联网网关 | 3 
Floating IP | 不限制
路由表 | 10 
Peering | 不限制



> [参考]
如果想删除VPC，则VPC内创建的所有子网应为未使用的状态。如果删除 VPC，则里面的子网、路由表、NAT网关一并删除。

* VPC之间是完全隔离的，不能进行相互通讯。

* VPC为私有网络，因此无法在外部互联网上直接访问。

* VPC内的所有实例，无法使用VLAN。

* 对VPC不支持跨地域（region）通讯。即一个VPC中的多个实例，只能是同一个地域。

* 没有NAT网关的情况下， VPC内的所有实例不能连接到外部互联网。

* 以下的情况可能不会被预先通知，”Broadcast, Multicast, Unknown Unicast”过多的情况下，网络可能会被切断。


## 子网

VPC可以划分多个子网，构成几个小型网络。但是，子网应属于VPC地址范围内。例如， 192.168.0.0/16的情况下，可使用 192.168.0.0~192.168.255.255为止共 65536个网络地址。同时，最小的子网为28bit-4个网络地址，且无法比这个小。子网也与 VPC一样，使用CIDR的划分方法。

如果创建子网则网关的IP地址将被自动指定，并且无法对其进行更改。而且将被自动添加到所在VPC的路由表中。

> [参考]
如果想要删除子网，只有子网中不包含实例或负载均衡等设备的空子网时，才能删除。

* 创建实例后，将为其自动分配一个已选定子网中的IP地址(固定 IP(fixed IP)).

* 实例启动时，将通过DHCP自动获取IP地址。

* 子网的地址范围无法更改。

* 在同一个VPC内，子网范围不能重复或重叠。

* 不同VPC中，子网范围可以重复或重叠。

* 如果不是系统自动分配给实例的MAC地址，将无法使用网络。所以，在实例上VPN服务也无法使用。

* 如果一个实例需要连接多个子网时，应在实例内的OS中设定精确、正确的路由。

* 同一个VPC内的两个子网不是完全隔离的。请使用安全组规则来保护实例。

* 子网支持跨不同可用区的本地通讯（相同子网下的多个实例，可以在不同的可用区中）。本地通信不收取费用。


## NAT网关

NAT网关可与路由表连接。VPC私有网络的正常无法进行外部通讯，但使用NAT网关可以访问访问外部互联网。要连接到外部互联网，各实例应将“默认网关”设定为子网的网关地址，NHN Cloud将对此进行自动处理。创建NAT网关时，应选择“外部网络”，但是当前在 NHN Cloud中，目前只能选择“public_network”。

* 创建实例或者VPC网络连接到外部互联网时，NAT网管将自动进行分配，并且无法进行变更。

* 外部无法通过NAT网关地址访问内部实例。

* 外部流入到NAT网关地址的异常流量将被阻止。

* 连接到互联网的实例的上行流量，费用将按照实际使用量来收取。

* 对于实例之间的本地内部通信流量，不收取费用。

### 用于维护服务器的互联网网关重启指南

NHN Cloud定期升级互联网网关服务器软件，提供基本基础设施服务的安全性及稳定性。
为了维护互联网网关服务器，在维护对象服务器中驱动的互联网网关通过重启移动至完成维护的互联网网关服务器。

需要重启的互联网网关在名称旁显示**! 重启**按钮，可以使用该按钮重启。

移动至被指定为维护对象的互联网网关所在的项目，下一步骤进行重启。

1.确认维护对象互联网网关。
    名称旁有**! 重启**按钮的互联网网关是维护对象互联网网关。
    <image-001.png>
    将鼠标光标放在**! 重启**按钮上，可确认详细的维护日程。 
    <image-002.png>
    
2.选择维护对象互联网网关，单击名称旁的**! 重启**按钮。
    重启完成前，使用维护对象互联网网关的实例的互联网连接将断开，因此请在不影响服务的时间进行。 
    但，连接浮动IP的实例不受互联网网关重启影响。
    
3.当询问是否重启互联网网关的窗口弹出时，单击**确定**按钮。
    <image-003.png>

4.状态显示灯变为绿色，等待至**! 重启**按钮消失。
    若互联网网关状态显示灯未改变或**! 重启**按钮未消失，请进行“刷新”。
    <image-004.png>

互联网网关重启过程中，无法操作相应互联网网关。
若互联网网关未正常重启，将自动向管理员报告，NHN Cloud将另行联系您。



## 路由表

路由表与VPC一同生成，并且VPC被删除时路由表也将被删除。一个VPC可以生成多张路由表，如果不是默认路由表，则可以进行删除。子网至少要连接到一个路由表，而且多个路由表不能共享一个NAT网关。

在指定路由表条目的时候，详情页面有扼要信息，**路由**tap上可添加路由条目。

> [参考]
添加路由条目时，必须指定VPC内可到达的网络地址范围，才能添加。超出范围将会添加失败。

* 被包含于路由表的子网网关将被自动添加。

* 无法删除”默认路由表”。删除VPC时，将会一同被删除

* 无法从路由条目中删除子网网关与NAT网关。

* 路由表与NAT网关断开连接，则互联网连接也被断开。



## Peering

Peering是为了两个VPC之间的内网相互通讯。一般情况下VPC之间都是隔离的，无法相互进行通讯，虽然可利用弹性IP来实现通讯，但是弹性IP的流量，将被收取费用。因此我们提供了实现两个VPC之间内网通讯的功能，将此称为Peering。

> [参考] Peering实现两个不同的VPC通讯。但是不支持三方交叉的方式实现VPC间的通讯。例： A <-> B Peering ，B <-> C Peering，A与 C不会自动的Peering。

* 两个VPC网络内的IP 地址段重叠时，则无法使用。<br>
如果创建Peering时，两个VPC的IP地址段有重叠的情况，Peering创建将会失败。
* 未连接到”默认路由表”的子网，将无法通信，与IP地址段的范围大小无关。
  * 한국(평촌) 리전은 피어링을 생성한 후, 피어링한 양쪽 VPC의 라우팅 테이블에 별도의 라우트를 설정해야 통신이 가능합니다.
    * 라우트의 "대상 CIDR"에 상대 VPC의 IP 주소 영역을 입력하고, "게이트웨이" 목록에서 피어링의 이름을 갖는 "PEERING" 항목을 선택하여 라우트를 추가합니다.
    * 라우트를 추가한 라우팅 테이블에 연결된 서브넷으로만 통신이 가능합니다.
* Peering创建成功的同时，将发生费用。
* Peering虽然没有配额限制，但将会消耗一个子网配额。
  * 한국(평촌) 리전은 서브넷 쿼터를 사용하지 않고 피어링된 두 VPC 내에서 IP 1개씩을 사용합니다.



## 코로케이션 게이트웨이

코로케이션 게이트웨이는 NHN Cloud에서 하이브리드로 제공하는 고객의 네트워크를 연결하기 위한 기능이며 한국(평촌) 리전에만 제공됩니다. NHN Cloud에서 하이브리드 서비스를 사용하는 경우에 한정하여 NHN Cloud Zone이 제공되고, 코로케이션 게이트웨이를 이용하여 구성한 VPC에 NHN Cloud Zone을 직접 연결할 수 있습니다.

* 한 개의 VPC는 한 개의 NHN Cloud Zone과 1:1로 연결됩니다.
* 연결과 동시에 과금됩니다.



