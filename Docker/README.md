**Docker 使用**

  安装 Docker： 查看 [docker](https://docs.docker.com/engine/install/centos/) 官网提供的安装教程。

​	下面提供文档关键步骤：ce 版本是免费的

```shell
$ sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
                  
$ sudo yum install -y yum-utils

$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo

$ sudo yum install docker-ce docker-ce-cli containerd.io
$ sudo systemctl start docker
## docker 设置为开机自启动
$ sudo systemctl enable docker 
```

设置 Docker 镜像加速

```shell
$ sudo mkdir -p /etc/docker
$ sudo tee /etc/docker/daemon.json <<-'EOF'
{
"registry-mirrors": ["https://xxxxxxx.mirror.aliyuncs.com"]
}
EOF
$ sudo systemctl daemon-reload
$ sudo systemctl restart docker
```
其中**https://xxxxxxx.mirror.aliyuncs.com**,换成自己申请的镜像加速域名。

