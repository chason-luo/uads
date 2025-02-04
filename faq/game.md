{{indexmenu_n>1}}

# 常见问题

## 1\. 高防服务是否可以试用，有什么规定或限制吗？

不支持试用。

## 2\. 高防能抗多少层的攻击？

3-7层攻击。

## 3\. 购买高防服务后，没有受到攻击收不收费？

如果您已经购买高防服务，无论您是否接入或受到攻击，我们将从购买时间开始计费。

## 4\. 高防服务有好几个套餐，该如何选择？

高防服务的套餐是按DDoS防护峰值（Gbps）设定，建议选择防护峰值大于历史攻击流量峰值的套餐。

## 5\. 如果遭遇的攻击流量峰值超过了已购买的高防服务防护峰值，该怎么办？

如果攻击流量峰值超过了购买的防护峰值，相应的高防IP也会触发自动封堵机制，一般会在封堵30分钟后自动解封。

为了不影响您的业务，您可以采用补差价升级防护套餐的方式来提高防护峰值、改善防护效果。升级生效后，如果被封堵的高防IP未自动解封，可向我们申请提前解封。

## 6\. 没有备案的域名可以接入高防吗？

不行。高防服务会对接入的域名进行备案检查，如果域名未备案，会有被封堵高防IP的风险。

## 7\. 使用高防服务会影响网站的备案吗？

不会。

## 8\. 网站接入高防服务后，多长时间会生效？

网站接入高防服务的生效时间取决于DNS解析生效时间，在所有配置正确的情况下，一般10-60分钟生效。

## 9\. 非80端口的网站是否可以接入高防服务？

可以。高防服务除了支持常用的80、443端口外，还支持一些自定义的端口，通用高防无需配置端口默认即可支持，如有问题可联系我们。

## 10\. 非HTTP协议的服务是否可以接入高防服务？

通用高防不但支持HTTP/HTTPS的业务，还支持其他TCP/UDP等协议的业务。

## 11\. 接入高防是否会和其他软防或硬防产生冲突？

接入高防后，需要在相应软防或硬防里将高防回源IP放行。（相应回源IP会在通用高防的界面上给出）

## 12\. 使用高防服务后，为什么ping出来的IP不是源站IP？

开启高防服务后，ping网站域名显示的将是高防服务的IP，源站IP会被隐藏起来了，使攻击者无法直接攻击源站IP。（请注意源站IP不要泄露或直接对外提供服务）

## 13\. 通用高防如何获取用户的真实IP地址？

通用高防获取真实IP地址需要通过toa模块实现，目前仅支持部分64位的linux系统，其他系统暂不支持。

64位的linux系统可运行"modprobe toa"尝试加载模块，成功后无需其他操作。

如提示未找到该模块，可按如下步骤进行手工编译与加载：

<WRAP left round box 100%>

（1）下载对应版本的源码包，目前只有Centos 6.5和Centos 7的源码包供下载：

> <http://ddospcap.ufile.ucloud.cn/toa_centos6.5_v2.tar.gz>
> 
> <http://ddospcap.ufile.ucloud.cn/toa_centos7_v3.tar.gz>

（2）编译与加载

> yum install gcc
> 
> yum install kernel-headers
> 
> yum install kernel-devel
> 
> ·\#以上环境如已安装可忽略
> 
> tar -zxvf toa\_centos6.5\_v1.tar.gz 或 tar -zxvf
> toa\_centos7\_v3.tar.gz
> 
> cd toa
> 
> make
> 
> mv toa.ko /lib/modules/\`uname -r\`/kernel/net/netfilter/ipvs/toa.ko
> 
> insmod /lib/modules/\`uname -r\`/kernel/net/netfilter/ipvs/toa.ko

</WRAP>

<wrap hi> 有问题请联系我们，如版本不符合，需升级内核再加载该模块；或者可直接使用UCloud 64位Centos
6.5/7系统的云主机，默认带有toa模块。</wrap>

## 14\. 使用高防服务后，如何使用FTP/SSH/3389远程桌面等服务？

可以直接使用源站IP来连接FTP、SSH及3389远程桌面。

## 15\. 使用高防服务后，更换了源站IP需要在高防配置界面做更改吗？

更换源站IP时，需要在对应高防界面上同步变更配置。

## 16\. 使用高防服务后，为什么建议更换一下源站IP？

因为在接入高防前，您的源站IP可能已经暴露，攻击者可以直接对该IP进行攻击，攻击流量将直接到达源站。

所以，在使用高防服务后，建议更换一下源站IP，使得新的源站IP被高防服务隐藏并防护着。

## 17\. 可以临时关闭防护吗？

通用高防在页面上不支持关闭防护，可以自行将业务切出高防来关闭防护。

## 18 如何切出高防服务？

不同业务切出方式不同，如站点业务可将域名解析会源站IP即可，其他业务只要保证不再使用高防IP接入业务即为切出高防。
