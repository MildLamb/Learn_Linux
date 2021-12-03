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
