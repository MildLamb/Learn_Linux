# rpm包 安装JDK
1. 下载JDK rpm
2. 安装java环境
```bash
# 检查当前系统是否存在java环境  
java -version
# 如果有的话就要先卸载
# rpm -qa|grep jdk # 检测JDK版本信息
# rpm -e --nodedps jdk_
```
3. 安装jdk
```bash
rpm -ivh xxx.rpm
```
4. **配置环境变量**  
```bash
[root@EngulfMissing jdk]# vim /etc/profile

# 进入后在下面添加
JAVA_HOME=/usr/java/jdk1.8.0_221-amd64
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
PATH=$PATH:$JAVA_HOME/bin
export PATH CLASSPATH JAVA_HOME
```
5. 上传springboot项目
  - 先打包成jar包
  - 判断linux服务器防火墙是否开放端口  firewall-cmd --list-ports
  - 如果没有系统防火墙
```bash
开启防火墙：systemctl start firewalld

关闭防火墙：systemctl stop firewalld

查看防火墙状态：systemctl status firewalld
```
  - 防火墙添加开放端口命令   firewall-cmd --zone=public --add-port=80/tcp --permanent
  - 需要重启防火墙才能看到  重启命令  systemctl restart firewalld.service

- linux 如何查看端口被哪个进程占用？
  - lsof  -i:端口号
  - netstat -tunlp |grep 端口号
  - linux后台运行jar包
  ```bashnohup java -jar xxx.jar &
  ```
