- docker地址 [https://docs.docker.com/install/linux/docker-ce/centos/](https://docs.docker.com/install/linux/docker-ce/centos/)
- 安装准备环境
```bash
# yum -y install 包名     # yum install 安装命令   -y 所有的提示都选yes
yum -y install gcc
yum -y install gcc-c++
```
- 卸载以前的docker版本
```bash
 sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```
- 安装repo
- 安装阿里云镜像
```bash
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
- 更新所有软件的索引包
```bash
yum makecache fast
```
- 安装docker
```bash
yum -y install docker-ce docker-ce-cli containerd.io
```
- 启动docker
```bash
systemctl start docker
```
- 查看docker进程
```bash
ps -ef|grep docker
```
- 查看docker版本
```bash
docker version
```
- 测试启动docker的helloworld程序(第一次运行docker回去官网下载)
```bash
docker run hello-world
```
