# DigitalOcean-Shadowsocks
在DigitalOcean搭建shadowsocks

今天花半天时间再digitalOcean上搭建了socketsocks

1.注册学校邮箱，申请github学生包（有学校邮箱的话基本是秒过，没有邮箱只能上传学生证照片，这个就有点难了），获取学生包内digitalOcean的优惠码（50刀）
注意：不要随便把这些优惠码给人，也不要去网上买便宜货，被查出来会被封！

2.注册digitalOcean的账号

3.注册paypal的账号，绑定银行卡（只支持工，建，招）

4.digitalOcean通过paypal支付5刀激活用户（首充再送10刀，不能代付！！被查出来就是欺诈，直接封号）
注意：5刀送10刀的活动和50刀的优惠码两者只能取一！！！这个下一点细说。


5.不要脸的一步，去给digitalOcean客服写申请，说自己的学生包用不了，态度好一点就直接给你加50刀，运气不好的话只能让你二选一。(如果不想这样，可以试试能不能只用50刀的学生包，但我不知道这样能不能激活用户)

6创建服务器（5刀一个月，现在共有65刀，可以用13个月）

7git bash登陆
输入ssh root@服务器ip
第一次登陆要输入原密码（邮箱发给你了），然后设置新密码，记住新密码（密码输入是不会显示的，光标也不会动，自己记住就好。git bash也不能直接ctrl+v，要用右键粘贴）

8安装shadowsocks+配置文件
我是根据http://www.topjishu.com/9263.html 的提示来的
也可以安装别人做好的包https://teddysun.com/342.html

1)在root下安装shadowsocks

apt-get install python-pip
pip install shadowsocks

在实际安装下发现很多依赖缺失，所以需要先执行一下：apt-get update。另外也有一些同学会选择CentOS的服务器，附上在CentOS下安装shadowsocks的方法：

yum install python-setuptools &amp;&amp; easy_install pip
pip install shadowsocks

2)配置文件
创建一个文件：/etc/shadowsocks.json
指令：vi /etc/shadowsocks.json
内容如下{
 "server":"你的服务器ip地址",
 "server_port":8388,
 "local_address": "127.0.0.1",
 "local_port":1080,
 "password":"你设置的密码",
 "timeout":300,
 "method":"aes-256-cfb",
 "fast_open": false
}

接下来你就可以使用下面这个指令启动服务

ssserver -c /etc/shadowsocks.json

#或者在后台运行
ssserver -c /etc/shadowsocks.json -d start
ssserver -c /etc/shadowsocks.json -d stop

9在你的电脑上配置shadowsocks设置，选择启动系统代理，选择PAC模式
在浏览器中选择系统代理，（Chrome浏览器下载插件Proxy SwitchyOmega）你就可以翻墙了
