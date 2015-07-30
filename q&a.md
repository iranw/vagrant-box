# vagrant 常见问题集合[已解决]


### vagrant启动报错`The following SSH command responded with a non-zero exit status.`
```
E:\Virtual-box\mysql_master>vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
    default: Adapter 2: hostonly
==> default: Forwarding ports...
    default: 22 => 2222 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
    default: Warning: Remote connection disconnect. Retrying...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Configuring and enabling network interfaces...
The following SSH command responded with a non-zero exit status.
Vagrant assumes that this means the command failed!

ARPCHECK=no /sbin/ifup eth1 2> /dev/null

Stdout from the command:

Device eth1 does not seem to be present, delaying initialization.


Stderr from the command:


E:\Virtual-box\mysql_master>vagrant ssh
```
说明：打好包重新init初始化，启动后就报这种错误。原因在于持久网络设备udev规则（persistent network device udev rules）是被原VM设置好的，再用box生成新VM时，这些rules需要被更新。而这和Vagrantfile里对新VM设置private network的指令发生冲突。删除就好了。

解决方案：
```
#vagrant ssh        #进入终端
$sudo rm -f /etc/udev/rules.d/70-persistent-net.rules
$exit               #退出终端
#vagrant reload     #重启虚拟机
```



### vagrant设置公网ip
Vagrantfile文件修改
```
config.vm.network "public_network", ip: "172.16.1.201",:netmask => "255.255.0.0"
default_router = "172.16.0.1"
```