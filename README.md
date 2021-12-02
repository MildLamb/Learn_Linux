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

# 文件属性查看与修改
```bash
[root@VM-16-14-centos ~]# cd /
[root@VM-16-14-centos /]# ls -ll
total 76
lrwxrwxrwx.   1 root root     7 Mar  7  2019 bin -> usr/bin
dr-xr-xr-x.   5 root root  4096 Nov 23 09:00 boot
drwxr-xr-x    2 root root  4096 Nov  5  2019 data
drwxr-xr-x   20 root root  3040 Nov 23 10:28 dev
drwxr-xr-x.  96 root root 12288 Nov 23 10:28 etc
drwxr-xr-x.   5 root root  4096 Dec  1 12:16 home
drwxr-xr-x    2 root root  4096 Nov 23 17:22 images
lrwxrwxrwx.   1 root root     7 Mar  7  2019 lib -> usr/lib
lrwxrwxrwx.   1 root root     9 Mar  7  2019 lib64 -> usr/lib64
drwx------.   2 root root 16384 Mar  7  2019 lost+found
drwxr-xr-x.   2 root root  4096 Apr 11  2018 media
drwxr-xr-x.   2 root root  4096 Apr 11  2018 mnt
drwxr-xr-x.   5 root root  4096 Jan  8  2021 opt
dr-xr-xr-x  106 root root     0 Nov 23 10:28 proc
dr-xr-x---.   6 root root  4096 Nov 23 09:00 root
drwxr-xr-x   24 root root   820 Dec  1 16:29 run
lrwxrwxrwx.   1 root root     8 Mar  7  2019 sbin -> usr/sbin
drwxr-xr-x.   2 root root  4096 Apr 11  2018 srv
dr-xr-xr-x   13 root root     0 Dec  1 11:37 sys
drwxrwxrwt.   9 root root  4096 Dec  1 16:28 tmp
drwxr-xr-x.  14 root root  4096 Jan  8  2021 usr
drwxr-xr-x.  20 root root  4096 Jan  8  2021 var
```
文件属性  文件数量  属主  属组  文件大小  时间  名称  

在linux中第一个字符代表这个文件是目录，文件或链接文件等等
- 第一个字符为[d]则是目录
- 第一个字符为[-]则是文件
- 若为[l]则表示为链接文档
- 若为[b]则表示为装置文件里面的可供储存的接口设备(可随机存取装置)
- 若为[c]则表示为装置文件里面的串行端口设备，例如键盘，鼠标(一次性读取装置)

接下来的字符中，以三个为一组，且均为[rwx]的三个参数的组合  
其中，[r]表示可读(read),[w]表示可写(write),[x]表示可执行(execute)  
这三个权限的位置不会改变，如果没有权限，就会出现减号[-]而已  
每个文件的属性由左边第一部分的10个字符来确定，如上图  

![image](https://user-images.githubusercontent.com/61497283/131208069-2171d0e8-ecbe-4c89-a468-a3d34b8aa65f.png)

## 修改属性
1. chgrp：更改文件属组  
```bash
chgrp [-R] 属组名 文件名 
```
2. chown：更改文件属主，也可以同时更改文件属组  
```bash
chown [-R] 属主名 文件名  
chown [-R] 属主名: 属组名 文件名  
```
3. **chmod：更改文件9个属性(必须掌握)**  
当你没权限操作文件时就可能需要修改权限了  
chmod [-R] xyz 文件或目录  
例如：chmod 777 filename  , 7 = 4(r) + 2(w) + 1(x)  
Linux文件属性有两种设置方法，一种是数字()，一种是符号  
Linux文件的基本权限有9个，分别是owner/group/others三种身份和各自的read/write/execute权限  
```
r:4  w:2  x:1
```
每种身份(owner/group/others)各自的三个权限(r/w/x)分数是需要累加的，例如当前权限为 [-rwxrw-r--] 分别为：  
- owner = rwx = 4 + 2 + 1 = 7
- group = rw- = 4 + 2 + 0 = 6
- others = r-- = 4 + 0 + 0 = 4
```bash
chmod 764 filename
```

# 文件内容查看
Linux系统中使用以下命令来查看文件的内容:
- cat：由第一行开始显示文件内容
- tac：从最后一行开始显示，是cat的倒着写
- nl：显示的时候，顺道输出行号
- more：一页页的显示文件内容（空格代表翻页，enter代表向下看一行）
- less：less与more类似，但是比more好用，它可以往前翻页（空格代表翻页，enter代表向下看一行，上下键翻动行，pageUp/Down翻动页面，q退出，查找字符串用  /要查找的字符串，这是向下查询，向上查询用    ?要查询的字符串）
- head：只看头几行 ，格式head -n 显示行数 文件名
- tail：只看尾几行 ，格式同上

你可以使用man [命令]来查看各个命令的使用文档 ，如 man cp  
