###### 使用vagrant+virtualbox打造统一开发环境



###### 1、下载box镜像包
地址：[http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box](http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box)
包搜索:[https://atlas.hashicorp.com/boxes/search](https://atlas.hashicorp.com/boxes/search)

###### 2、执行命令引入镜像包
```
//vagrant box add 命名 box文件目录
#vagrant box add centos64 opscode_centos-6.5_chef-provisionerless.box
#vagrant box list
#cd E:\Virtual-box\centos-dev(需要建立虚拟机的空目录)
#vagrant init centos64
#vagrant up(启动)
#vagrant ssh(进入虚拟机 用户密码都是vagrant)
#vagrant halt(关闭虚拟机)
```

###### 3、如何打包

