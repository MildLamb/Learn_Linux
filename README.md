# Learn_Linux
学习Linux

# Linux目录结构
1. 一切皆文件
2. 根目录/，所有的文件都挂载在这个节点下

**目录介绍**  
- /bin：bin是Binary的缩写，这个目录存放着最经常使用的命令
- /boot：这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件
- /dev：dev是Device(设备的缩写)，存放的是Linux的外部设备，在Linux中访问设备的方式和访问文件的方式相同
- **/etc：这个目录用来存放所有的系统管理所需要的配置文件和子目录**
- **/home：用户的主目录，在linux中，每个用户都有一个自己的目录，一般该目录名以用户的账号名称命名**
- /lib：这个目录里存放着系统最基本的动态连接共享库
- /lost+found：这个目录一般情况下是空的，当系统非法关机后，里面就存放了一些文件
- /media：linux系统会自动识别一些设备，如U盘，光驱等等，当识别后，linux会把识别的设备挂载到这个目录下
- /mnt：系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在/mnt/上，然后进入该目录就可以查看光驱里的内容了
- **/opt：这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库就可以放在这个目录下，默认是空的**
- /proc：这个目录是一个虚拟目录，它是系统内存的映射，我们可以通过直接访问这个目录来获取系统信息
- **/root：该目录为系统管理员，也称为超级权限者的用户主目录**
- /sbin：s就是Super User的意思，这里存放的是系统管理员使用的系统管理程序
- /srv：该目录存放一些服务启动之后需要提取的数据
- /sys：这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个系统文件sysfs。
- **/tmp：这个目录是用来存放一些临时文件的，用完即丢的文件可以放这里**
- **/usr：这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似于windows下的program files目录**
- /usr/bin：系统用户使用的应用程序
- /usr/src：内核源代码默认的放置目录
- **/var：这个目录中存放着在不断扩充的东西，我们习惯将那些经常被修改的目录放在这个目录下。包括各种日志文件**
- /run：一个临时文件系统，存储系统启动以来的信息。当系统重启时，这个目录下的文件应该被删除或清除

# Linux常用命令
### 目录管理
**cd，切换目录命令**  
**绝对路径 相对路径**  
cd ：切换目录命令 绝对路径以/开头 相对路径 ../上一级是目录 根据与当前目录的相对位置查找  
./ ：当前目录  
cd.. ：返回上一级目录  
  
**ls ：列出目录**  
-a参数：all，查看全部的文件，包括隐藏文件  
-l参数：列出所有的文件，包含文件的属性和权限，没有隐藏文件  
可以组合使用 -al   

pwd ：显示当前所在目录  

mkdir ：创建一个目录  
mkdir -p ：创建层级目录(递归创建)  
```bash
[root@VM-16-14-centos home]# pwd
/home
[root@VM-16-14-centos home]# mkdir wildwolf
[root@VM-16-14-centos home]# ls
apache-tomcat-9.0.52  lighthouse  mildlamb  wildwolf
[root@VM-16-14-centos home]# mkdir -p EngulfM/champion/kindred
[root@VM-16-14-centos home]# ls
apache-tomcat-9.0.52  EngulfM  lighthouse  mildlamb  wildwolf
[root@VM-16-14-centos home]# cd EngulfM
[root@VM-16-14-centos EngulfM]# ls
champion
[root@VM-16-14-centos EngulfM]# cd champion
[root@VM-16-14-centos champion]# ls
kindred
```
rmdir ：删除目录，只能删除空目录，如果下面存在文件，需要先删除文件  
rmdir -p ：递归删除多个目录  

rm ：移除文件或者文件夹  
-f：忽略不存在的文件，不会出现警告，强制删除
-r：递归删除目录  
-i：互动，删除时询问是否删除

cp ：复制文件或者目录  
格式：cp 拷贝文件 新的地方  

mv ：移动文件或文件夹(剪切)/重命名文件夹  
-f 强制  
-u 只替换更新过的文件
