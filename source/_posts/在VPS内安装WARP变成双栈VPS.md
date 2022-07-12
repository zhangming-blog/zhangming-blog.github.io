title: 在VPS内安装WARP变成双栈VPS
author: zhangming
tags:
  - vps
  - cf warp
  - ipv4
  - ipv6
categories:
  - warp
date: 2022-07-12 11:25:00
---
在IPv6 Only的VPS（例如：Hax和Euserv）中，我们想无限制的使用IPv4的资源。又或者是IPv4 only的VPS，想无限制的使用IPv6的资源。这篇文章来和大家聊一聊如何安装WARP，让自己的VPS变成双栈的VPS

### 准备材料

 一台VPS
 开启TUN模块（仅限LXC / OpenVZ架构的VPS）
 
### 步骤

1.打开TUN模块（如果是KVM机器可跳过此步骤）。以Hax官网为例，打开官网的控制面板，点击“Enable TUN”按钮，稍等片刻后再点击“Restart”按钮重启VPS
![20220115155318.png](https://s2.loli.net/2022/07/12/OTwNMApr8e1I9K2.png)
2.输入cat /dev/net/tun命令，检查TUN模块状态，如出现“cat: /dev/net/tun: File descriptor in bad state”时即为开启成功
3.复制以下安装命令
```
wget -N https://raw.githubusercontent.com/fscarmen/warp/main/menu.sh && bash menu.sh
```
4.选择语言，输入2选择简体中文
5.输入“1”安装WARP（IPV4连接走WARP的流量），当然你输入“2”也可以（全部连接走WARP的流量）
![20220115160104.png](https://s2.loli.net/2022/07/12/jVcG7dvf1wOZqap.png)
6.选择账户类型，IPV4优先级
![20220115160250.png](https://s2.loli.net/2022/07/12/RnUfwsEuB9DoZAz.png)
7.等待安装，待安装完成后会出现安装的结果
![20220115160532.png](https://s2.loli.net/2022/07/12/2ymPewF5YED9zS6.png)
### 注意事项
1.WARP的IP只是给你访问IPV4 / IPV6资源的代理IP，并非公网IP  
2.对于部分CloudFlare CDN的网站，使用WARP+或WARP Teams账户会走专线，实现加速效果
