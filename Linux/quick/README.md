**快速安装 Linux**

  使用 [VirtualBox](https://www.virtualbox.org/wiki/Downloads) + [Vagrant](https://www.vagrantup.com/downloads.html) 傻瓜式安装； Vagrant可能会比较慢!!!

  安装完成后需要重启电脑！

​		在 windows cmd 窗口执行

​		`Vagrant init centos/7`

​		该版本（centos/7）需要到 [vagrant](https://app.vagrantup.com/boxes/search) 官方镜像下查找

​	启动虚拟机`vagrant up` 

​		需要确保 当前 cmd 窗口的路径下有 `Vagrantfile` 文件

​		`Vagrantfile`  默认在 `C:\Users\woniu` 下

​	连接虚拟机`vagrant ssh`  

​	默认的网络地址转换为 端口转发。

​	  可以修改 `Vagrantfile` 文件下

​		`config.vm.network "private_network", ip: "192.168.56.58"`  该ip必须和本机同一网段。

​	  也可以修改虚拟机ip配置文件。 这里不再做具体描述。





若 vagrant up 太慢 或者失败

 可以尝试以下方法

 到[镜像下载地址](http://www.vagrantbox.es/)查找 所需的镜像版本， 如 我找的 centos 7 x64, 复制地址，用下载工具下载。

先删除`Vagrantfile` 文件

 然后 cmd 窗口执行： 

```shell
 vagrant box add {title} {url}
 vagrant init {title}
 vagrant up
```

​			url 改为本地镜像存放地址， title可以随意取。

**路径千万不要有中文！！！路径千万不要有中文！！！路径千万不要有中文！！！**

若有和我一样创建电脑时用户名是中文的小伙伴，那么不要急

首先把 **VirtualBox** 的默认存储路径改为英文

​	`VirtualBox` 运行界面，点击“管理” --> “全局设定”  ， 把常规设置里边的 “默认虚拟电脑位置” 改成自定义路径。有些网友说直接改用户下的xml配置，憨憨我自己改了不生效。

改 `Vagrant` 的 HOME 目录，其实就是用户下的 .vagrant.d 文件夹的路径

```bash
setx VAGRANT_HOME "D:\Vagrant\Home\.vagrant.d"
setx VAGRANT_HOME "D:\Vagrant\Home\.vagrant.d" /M
```

或者把 “VAGRANT_HOME” 添加到环境变量里去。这里我就不接受步骤了。

通过以上两个步骤,虚拟机应该是装好了。 

我以后装系统要是还把用户弄成中文的，D那我就是铁憨憨！！！😈