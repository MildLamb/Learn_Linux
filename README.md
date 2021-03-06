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
cd .. ：返回上一级目录  
  
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
- less：less与more类似，但是比more好用，它可以往前翻页（空格代表翻页，enter代表向下看一行，上下键翻动行，pageUp/Down翻动页面，按q退出，查找字符串用  /要查找的字符串，这是向下查询，向上查询用    ?要查询的字符串，按n查询下一个结果，按N查询上一个结果）
- head：只看头几行 ，格式head -n 显示行数 文件名
- tail：只看尾几行 ，格式同上

你可以使用man [命令]来查看各个命令的使用文档 ，如 man cp  

## Linux链接的概念
Linux的链接分为两种：硬链接和软链接  
硬链接：A---B，假设B是A的硬链接，那么它们两个指向了同一个文件，允许一个文件拥有多个路径(在删除源文件的时候，系统则将链接数减1，当链接数为0的时候，inode就会被系统回收，文件的内容才会被删除。)  
软链接：类似Windows下的快捷方式，删除源文件，快捷方式也访问不了  
  
创建硬链接ln 谁 被谁链接   
创建软连接ln -s 谁 被谁链接  
创建文件 touch  
输入字符串 echo  ,echo "内容" >> 文件名  
```
[root@iZ2zedwea74ejj95zb9sh0Z /]# cd home
[root@iZ2zedwea74ejj95zb9sh0Z home]# clear
[root@iZ2zedwea74ejj95zb9sh0Z home]# touch f1  # 创建一个文件f1
[root@iZ2zedwea74ejj95zb9sh0Z home]# ls
f1  mildlamb  myimage  tomcat
[root@iZ2zedwea74ejj95zb9sh0Z home]# ln f1 f2  # 创建一个硬链接f2
[root@iZ2zedwea74ejj95zb9sh0Z home]# ls
f1  f2  mildlamb  myimage  tomcat
[root@iZ2zedwea74ejj95zb9sh0Z home]# ln -s f1 f3  # 创建一个软链接f3
[root@iZ2zedwea74ejj95zb9sh0Z home]# ls
f1  f2  f3  mildlamb  myimage  tomcat
[root@iZ2zedwea74ejj95zb9sh0Z home]# ll
total 12
-rw-r--r-- 2 root root    0 Aug 28 15:16 f1
-rw-r--r-- 2 root root    0 Aug 28 15:16 f2
lrwxrwxrwx 1 root root    2 Aug 28 15:17 f3 -> f1
drwxr-xr-x 2 root root 4096 Aug 28 11:54 mildlamb
drwxr-xr-x 2 root root 4096 Aug 28 11:29 myimage
drwxr-xr-x 3 root root 4096 Aug 28 11:41 tomcat
[root@iZ2zedwea74ejj95zb9sh0Z home]# echo "I love Kindred" >> f1  # 给f1文件中写入一些字符串
[root@iZ2zedwea74ejj95zb9sh0Z home]# clear
[root@iZ2zedwea74ejj95zb9sh0Z home]# ll
total 20
-rw-r--r-- 2 root root   15 Aug 28 15:17 f1
-rw-r--r-- 2 root root   15 Aug 28 15:17 f2
lrwxrwxrwx 1 root root    2 Aug 28 15:17 f3 -> f1
drwxr-xr-x 2 root root 4096 Aug 28 11:54 mildlamb
drwxr-xr-x 2 root root 4096 Aug 28 11:29 myimage
drwxr-xr-x 3 root root 4096 Aug 28 11:41 tomcat
[root@iZ2zedwea74ejj95zb9sh0Z home]# cat f1   # 查看各个文件内容
I love Kindred
[root@iZ2zedwea74ejj95zb9sh0Z home]# cat f2
I love Kindred
[root@iZ2zedwea74ejj95zb9sh0Z home]# cat f3
I love Kindred
[root@iZ2zedwea74ejj95zb9sh0Z home]# rm -rf f1   # 删除源文件f1
[root@iZ2zedwea74ejj95zb9sh0Z home]# ls
f2  f3  mildlamb  myimage  tomcat
[root@iZ2zedwea74ejj95zb9sh0Z home]# cat f2     # 硬链接依旧可以查看
I love Kindred
[root@iZ2zedwea74ejj95zb9sh0Z home]# cat f3     # 软连接不能查看了
cat: f3: No such file or directory
```

# Vim编辑器
vi/vim共分为三种模式，分别是命令模式(Command mode),输入模式(Insert mdoe)和底线命令模式(Lastline mode)  

使用： vim 文件名 ，若文件不存在则是新建文件，若文件存在，则是修改文件  

**命令模式：**  
用户刚刚启动vi/vim，便进入了命令模式  
此状态下敲击键盘动作会被Vim识别为命令，而非输入字符。比如我们此时按下i，便会进入输入模式  
- i:切换到输入模式，以输入字符
- x：删除当前光标所在处的字符
- : ：切换到底线命令模式，如果是编辑模式需要先退出编辑模式(ESC)

|命令 |	说明|
|:--:|:--:|
|h|	左移|
|l|	右移|
|j|	下移|
|k|	上移|
|w|	移动到下一个单词的开头|
|e|	移动到当前单词的结尾|
|b|	移动到上一个单词的开头|
|ge|	移动到前一个单词的结尾|
|^|	移动到行头|
|$|	移动到行尾|
|f<字母>|	向后搜索<字母>并跳转到第一个匹配的位置|
|F<字母>|	向前搜索<字母>并跳转到第一个匹配的位置|
|t<字母>|	向后搜索<字母>并跳转到第一个匹配位置之前的字母|
|T<字母>|	向前搜索<字母>并跳转到第一个匹配位置之后的字母|
|shift+zz|	退出vim|
|x|	删除游标所在的字符|
|3x|	删除3个连续字符，以此类推|
|X|	删除游标所在的前一个字符|
|Delete|	同x|
|dd|	删除整行|
|2dd|	向下删除2行，以此类推|
|dw|	删除一个单词（不适用中文）|
|daw(delete a word)|	删除一个单词|
|dnw(n替换为相应数字)|	删除n个单词|
|d$或D|	删除至行尾|
|d^|	删除至行首|
|dG|	删除到文档结尾处|
|d1G|	删除至文档首部|
|.(小数点)|	重复上一次的命令操作|
|gg|	游标移动到第一行|
|G|	游标移动到最后一行|
|nG|	游标移动到第n行（如果默认没有显示行号，请先进入命令行模式，输入:set nu以显示行号）|
|Ctrl+o|	快速回到上一次（跳转前）光标所在位置|
|yy|	复制游标所在的整行|
|3yy|	向下复制3行，以此类推|
|y^|	复制至行首，不含光标所在处字符|
|yw|	复制一个单词|
|y2w|	复制两个单词|
|yG|	复制至文本末|
|y1G|	复制至文本开头|
|p|	粘贴至光标后|
|P|	粘贴至光标前|
|ddp||	剪切并粘贴|
|r+<待替换字母>|	将游标所在字母替换为指定字母|
|R|	连续替换，直到按下Esc|
|cc|	替换整行，即删除游标所在行，并进入插入模式|
|cw|	替换一个单词。即删除一个单词，并进入插入模式|
|C（大写）|	替换游标以后至行末|
|~|	反转游标所在字母大小写|
|u(n)|	撤销一次或n次操作|
|U（大写）|	撤销当前行的所有修改|
|Ctrl+r|	redo，即撤销undo的操作|
|>>|	整行向右缩进|
|<<|	整行向左回退|
|/+<需要查找的字符串>+回车|	向下查找(进入查找之后，输入n和N可以继续查找，n是查找下一个内容，N查找上一个内容，命令行模式下输入noh回车可取消搜索)|
|?+<需要查找的字符串>+回车|	向上查找(进入查找之后，输入n和N可以继续查找，n是查找下一个内容，N查找上一个内容，命令行模式下输入noh回车可取消搜索)|
|\\*|	寻找游标所在处的单词|
|数字 + space | 当前光标跳动数字个字符 |
|数字 + enter | 当前行跳动数字个行 |



命令模式只有一些最基本的命令，因此要依靠底线命令模式获取更多命令  

**输入模式:**  
可以编辑  
|命令|	说明|
|:--:|:--:|
|i|	在当前光标处进行编辑|
|I|	在行首插入|
|A|	在行末插入|
|a|	在光标后插入编辑|
|o|	在当前行后插入一个新行|
|O|	在当前行前插入一个新行|
|cw|	替换从光标所在位置到一个单词的结尾字符|

**底线命令模式:**  
在命令模式下按:(英文冒号)进入底线命令模式，光标移动到最后，可以输入一些底线命令了  
- q:退出程序
- w:保存文件
- 直接wq:保存并退出

|命令|	说明|
|:--:|:--:|
|:q!|	强制退出vim，不保存|
|:q|	退出vim|
|:wq!|	强制保存并退出vim|
|:w| <文件路径>	另存为|
|:saveas| <文件路径>	另存为|
|:x|	保存并退出vim|
|:wq|	保存并退出vim|
|:set nu|	显示行号|
|:set shiftwidth=10|	设置缩进为10个字符，以此类推（输入Esc回到普通模式，再次尝试>>看缩进是否变化）|
|:ce(center)|	本行内容居中|
|:ri(right)|	本行内容居右|
|:le(left)|	本行内容居左|

# 用户管理
- 查看用户的配置 cat /etc/passwd

- 添加账户 useradd
  - -c:指定一段注释性描述
  - -d：指定用户主目录，如果词目录不存在，则同时使用-m选项，可以创建主目录
  - -g：用户组 指定用户所属的用户组
  - -G：用户组 指定用户所属的附加组
  - -m：使用者目录如不存在则自动建立
  - -s：shell文件 指定用户的登录shell
  - -u：用户号 指定用户的用户号，如同时有-o选项，则可以重复使用其他用户的标识

创建用户实操： 
```bash
[root@VM-16-14-centos home]# useradd -m wildwolf
```
- 删除用户 userdel
userdel -r 用户名称    ：删除用户的时候连同该用户的目录一起删除
```bash
[root@VM-16-14-centos home]# userdel -r wildwolf
```
- 修改用户 usermod
  - -c:指定一段注释性描述
  - -d：指定用户主目录，如果词目录不存在，则同时使用-m选项，可以创建主目录
  - -g：用户组 指定用户所属的用户组
  - -G：用户组 指定用户所属的附加组
  - -m：使用者目录如不存在则自动建立
  - -s：shell文件 指定用户的登录shell
  - -u：用户号 指定用户的用户号，如同时有-o选项，则可以重复使用其他用户的标识  

 格式：usermod 修改上面的什么参数 改成什么 对谁修改
 
- 切换用户
  1. 切换用户的命令为：  su username    【username是你的用户名】
  2. 从普通用户切换到root用户，还可以使用命令： sudo su
  3. 在终端输入exit或logout或使用快捷方式ctrl+d，可以退回到原来用户，其实ctrl+d也是执行的exit命令
  4. 在切换用户时，如果想在切换用户之后使用新用户的工作环境，可以在su和username之间加-，例如【su - root】
  5. $表示普通用户
  6. #表示超级用户，也就是root用户
```bash
[root@VM-16-14-centos home]#  
```
[当前用户名@主机名 当前目录]

- 切换用户实操
```bash
[root@VM-16-14-centos home]# su wildwolf
[wildwolf@VM-16-14-centos home]$ 
```
- 查看主机名和修改主机名
```bash
[wildwolf@VM-16-14-centos home]$ hostname
VM-16-14-centos
[wildwolf@VM-16-14-centos home]$ hostname newhostname
```
- 修改用户密码
```bash
[root@VM-16-14-centos home]# Changing password for user yourusername
```
- 锁定用户(-l锁定  -u解锁)
```bash
[root@VM-16-14-centos home]# passwd -l yourusername
```
## 用户组管理
实际是对 /etc/group文件的更新  
创建一个用户组  groupadd  
删除一个用户组  groupdel  
修改用户组信息  groupmod  
```bash
[root@EngulfMissing ~]# groupadd -g 520 gnardada      # 添加用户组   -g 指定编号，如果不指定，就是自增1
[root@EngulfMissing ~]# groupdel gnardada             # 删除用户组   
[root@EngulfMissing ~]# groupmod -g 1216 -n gnar gnardada   # 修改用户组    -g 编号  -n 名字  最后是修改哪个用户组
```

- 用户组切换 
```bash
newgrp 组名
```

**用户文件查看**
/etc/passwd  
用户名:口令:用户标识号:组标识号:注释性描述:主目录:登录shell
```bash
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
chrony:x:998:996::/var/lib/chrony:/sbin/nologin
nscd:x:28:28:NSCD Daemon:/:/sbin/nologin
tcpdump:x:72:72::/:/sbin/nologin
kindred:x:1000:1000::/home/kindred:/bin/bash
```


### 磁盘管理
- df：列出文件系统整体使用量  加-h 可以以M的形式展示  不加是字节大小显示 
- du：检查磁盘空间使用量    du -sm /* : 检查根目录下每个目录所占用的容量

```bash
[root@VM-16-14-centos ~]# df
Filesystem     1K-blocks    Used Available Use% Mounted on
devtmpfs         1928480       0   1928480   0% /dev
tmpfs            1940096      24   1940072   1% /dev/shm
tmpfs            1940096     520   1939576   1% /run
tmpfs            1940096       0   1940096   0% /sys/fs/cgroup
/dev/vda1       82437508 6367652  72614352   9% /
tmpfs             388020       0    388020   0% /run/user/0
[root@VM-16-14-centos ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
devtmpfs        1.9G     0  1.9G   0% /dev
tmpfs           1.9G   24K  1.9G   1% /dev/shm
tmpfs           1.9G  520K  1.9G   1% /run
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/vda1        79G  6.1G   70G   9% /
tmpfs           379M     0  379M   0% /run/user/0
```

```bash
[root@VM-16-14-centos home]# du
16	./wildwolf
8	./lighthouse/.ssh
24	./lighthouse
16	./mildlamb
629820	.
[root@VM-16-14-centos home]# du -a
4	./wildwolf/.bashrc
4	./wildwolf/.bash_logout
4	./wildwolf/.bash_profile
16	./wildwolf
4	./lighthouse/.bashrc
4	./lighthouse/.bash_logout
4	./lighthouse/.ssh/authorized_keys
8	./lighthouse/.ssh
4	./lighthouse/.bash_profile
24	./lighthouse
4	./mildlamb/.bashrc
4	./mildlamb/.bash_logout
4	./mildlamb/.bash_profile
16	./mildlamb
629760	./mysql-5.7.26-linux-glibc2.12-x86_64.tar.gz
629820	.
```
- 检查根目录下，每个目录所占用的容量
```bash
[root@VM-16-14-centos home]# du -sm /*
0	/bin
123	/boot
134	/data
0	/dev
37	/etc
616	/home
0	/lib
0	/lib64
1	/lost+found
1	/media
1	/mnt
127	/opt
du: cannot access ‘/proc/21770/task/21770/fd/4’: No such file or directory
du: cannot access ‘/proc/21770/task/21770/fdinfo/4’: No such file or directory
du: cannot access ‘/proc/21770/fd/4’: No such file or directory
du: cannot access ‘/proc/21770/fdinfo/4’: No such file or directory
0	/proc
1	/root
1	/run
0	/sbin
1	/srv
0	/sys
21	/tmp
4873	/usr
238	/var
```
- 挂载mount
```bash
[root@VM-16-14-centos home]# mount /dev/Gnar /mnt/Gnar
```
将外部设备 Gnar  挂载到 mnt目录的Gnar上，来实现访问
- 卸载挂载设备 ：umount -f [挂载位置]    -f：强制卸载

# 进程管理
ps：查看当前系统中正在执行的各种进程的信息  
- ps -xx：  
  - -a：显示当前终端运行的所有的进程信息
  - -u：以用户的信息显示进程
  - -x：显示后台运行进程的参数

```bash
# ps -aux  查看所有的进程
ps -aux|
# | 在linux中叫做管道符   A|B  A的结果作为B的条件
# grep 查找文件中符合条件的字符串
```bash
[root@VM-16-14-centos home]# ps -aux|grep mysql
root      6965  0.0  0.0  12800  1756 ?        S    Dec02   0:00 /bin/sh /usr/local/mysql-5.7.26/bin/mysqld_safe --datadir=/data/mysql --pid-file=/data/mysql/mysql.pid
mysql     7156  0.0  5.1 1340840 201576 ?      Sl   Dec02   0:21 /usr/local/mysql-5.7.26/bin/mysqld --basedir=/usr/local/mysql-5.7.26 --datadir=/data/mysql --plugin-dir=/usr/local/mysql-5.7.26/lib/plugin --user=mysql --log-error=/data/mysql/mysql.err --pid-file=/data/mysql/mysql.pid --socket=/tmp/mysql.sock --port=3306
root     26995  0.0  0.0 115932  1008 pts/1    S+   10:26   0:00 grep --color=auto mysql
```

- ps -ef：可以查看到父进程的信息
```bash
ps -ef|grep mysql
```
- 线程树显示进程 pstree
  - -p：显示父id
  - -u：显示用户组
```bash
pstree -pu
```
- 结束进程，等价于windows的结束进程
```bash
kill -9 pid
```
