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
