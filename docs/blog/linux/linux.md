# linux

Linux，全称GNU/Linux，是一套免费使用和自由传播的类UNIX操作系统，其内核由林纳斯·本纳第克特·托瓦兹于1991年第一次释出，它主要受到Minix和Unix思想的启发，是一个基于POSIX和Unix的多用户、多任务、支持多线程和多CPU的操作系统。它能运行主要的Unix工具软件、应用程序和网络协议。它支持32位和64位硬件。Linux继承了Unix以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。Linux有上百种不同的发行版，如基于社区开发的debian、archlinux，和基于商业开发的Red Hat Enterprise Linux、SUSE、oracle linux等

## 体系架构

### 简要结构图

![linux](/linux/linux.png)

### 完整结构图

![linux](/linux/linux_1.png)

### 系统体系结构图

![linux](/linux/linux_system.png)

## 常见目录含义

| 目录 | 概述 |
|:-:|:-|
| /bin | 存放⼆进制可执⾏⽂件(ls,cat,mkdir等)，常⽤命令⼀般都在这⾥。|
| /etc | 存放系统管理和配置⽂件 |
| /home | 存放所有⽤户⽂件的根⽬录，是⽤户主⽬录的基点，⽐如⽤户user的主⽬录就是/home/user，可以⽤~user表示|
| /usr | ⽤于存放系统应⽤程序，⽐较重要的⽬录/usr/local 本地系统管理员软件安装⽬录（安装系统级的应⽤）。这是最庞⼤的⽬录，要⽤到的应⽤程序和⽂件⼏乎都在这个⽬录。/usr/x11r6 存放x window的⽬录/usr/bin 众多的应⽤程序/usr/sbin超级⽤户的⼀些管理程序/usr/doc linux⽂档/usr/include linux下开发和编译应⽤程序所需要的头⽂件/usr/lib 常⽤的动态链接库和软件包的配置⽂件/usr/man 帮助⽂档/usr/src 源代码，linux内核的源代码就放在/usr/src/linux⾥/usr/local/bin本地增加的命令/usr/local/lib 本地增加的库
| /opt | 额外安装的可选应⽤程序包所放置的位置。⼀般情况下，我们可以把tomcat等都安装到这⾥。|
| /proc | 虚拟⽂件系统⽬录，是系统内存的映射。可直接访问这个⽬录来获取系统信息。|
| /root | 超级⽤户（系统管理员）的主⽬录（特权阶级^o^）|
| /sbin | 存放⼆进制可执⾏⽂件，只有root才能访问。这⾥存放的是系统管理员使⽤的系统级别的管理命令和程序。如ifconfig等。|
| /dev |  ⽤于存放设备⽂件。|
| /mnt | 系统管理员安装临时⽂件系统的安装点，系统提供这个⽬录是让⽤户临时挂载其他的⽂件系统。|
| /boot | 存放⽤于系统引导时使⽤的各种⽂件 |
| /lib | 存放跟⽂件系统中的程序运⾏所需要的共享库及内核模块。共享库⼜叫动态链接共享库，作⽤类似windows⾥的.dll⽂件，存放了根⽂件系统程序运⾏所需的共享⽂件。 |
| /tmp | ⽤于存放各种临时⽂件，是公⽤的临时⽂件存储点。|
| /var | ⽤于存放运⾏时需要改变数据的⽂件，也是某些⼤⽂件的溢出区，⽐⽅说各种服务的⽇志⽂件（系统启动⽇志等。）等。|
| /lost+found | 这个⽬录平时是空的，系统⾮正常关机⽽留下“⽆家可归”的⽂件（windows下叫什么.chk）就在这⾥ |

## 通用命令

### 认识终端

```sh
  [root@travis ~]#
```

| 名称 | 概述 |
| :-: | :- |
| root | 为当前登录用户 |
| travis | 主机名 |
| ~ | 当前⼯作⽬录,默认是当前⽤户的家⽬录，root就是/root,普通⽤户是 /home/⽤户名 |
| #、$ | 提示符超级⽤户是 #,普通⽤户是$

### 一般命令格式

命令 [选项] [参数]

当有多个选项时，可以写在⼀起

⼀般参数有简化和完整写法两种 -a 与 --all 等效

### ls

查询⽬录中的内容

ls [选项] [⽂件或者⽬录]

选项

* -a 显示所有⽂件，包括隐藏⽂件
* -l 显示详细信息
* -d 查看⽬录本身的属性⽽⾮⼦⽂件 ls /etc/
* -h ⼈性化的⽅式显示⽂件⼤⼩
* -i 显示inode,也就是i节点

默认当前⽬录下的⽂件列表

-l 显示详细信息

```bash
drwxr-xr-x . 1 root root 800 Sep 16 00:19 logs
```

| drwxr-xr-x | . | 1 | root | root | 800 | Sep 16 00:19 | logs |
| :-: | :-: | :-: | :-: | :-: | :-: |:-: | :-: |
| ⽂件类型和权限 | ACL 权限 | 硬链接引⽤计数 | 所有者 | 所属组 | 文件大小 | 最后修改时间 | 文件名 |

#### ⽂件类型和权限

`-rw-r--r--`

* ⽂件类型 - ⽂件、d ⽬录、l 软链接⽂件
* u(所有者)、g(所属组)、o(其他⼈)
* r(read) 读取、w(write) 写⼊、x(execute) 执⾏

## 文件处理命令

### mkdir

建⽴⽬录 mkdir

* make directory

* mkdir -p [⽬录名]
  * -p 递归创建

### cd

切换所在⽬录 change directory

* cd [⽬录]
  * ~ 家⽬录
  * 家⽬录
  * -上次⽬录
  * . 当前⽬录
  * .. 上级⽬录
* 相对路径是参照当前所在⽬录
* 绝对路径是从根⽬录开始
* 按TAB键可以补全命令和⽬录

### pwd

显示当前⽬录 pwd

### rmdir

删除目录 rmdir

* 删除⽬录 remove empty directory
* rmdir [⽬录名]

### rm

删除⽂件或者⽬录 remove

* 删除⽂件或者⽬录 remove
  * rm [⽂件或者⽬录]
  * -r 删除⽬录
  * -f 强制删除
* rm -rf ⽂件或者⽬录] 递归强制删除所有⽬录

### cp

copy 复制命令

* copy 复制命令
* copy [源⽂件或者⽬录] [⽬标⽂件]
  * -r 复制⽬录,默认是复制⽂件
  * -p 连带⽂件属性复制
  * -d 若源⽂件是链接⽂件，则复制连接属性
  * -a 相当于 -rpd

### mv

* 移动⽂件或者改名 move
* mv [源⽂件或者⽬录] [⽬标⽂件]

### in

链接命令,⽣成链接⽂件 link

#### 硬连接特征

* 拥有相同的i节点和存储block块，可以看作是同⼀个⽂件
* 可以通过i节点访问
* 不能跨分区
* 不能针对⽬录使⽤
* ⼀般不使⽤

#### 软链接特征

* ln -s [源⽂件] [⽬标⽂件]
  * -s 创建软链接
* 类似Windows快捷⽅式
* 软链接拥有⾃⼰的i节点和Block块，但是数据块中只保存源⽂件的⽂件名和i节点号，并没有实际的⽂件数据
* lrwxrwxrwx l 软链接 软链接的⽂件权限都是 777
* 修改任意⼀个⽂件，另⼀个都会改变
* 删除源⽂件，软链接不能使⽤
* 软链接源⽂件必须写绝对路径

## ⽂件搜索命令

### locate

* 在后台数据库中按⽂件名搜索，速度⽐较快
* 数据保存在 /var/lib/mlocate 后台数据库，每天更新⼀次
* 可以 updatedb 命令⽴刻更新数据库
* 只能搜索⽂件名

```bash
/etc/updatedb.conf
```

建⽴索引的配置⽂件

* PRUNE_BIND_MOUNTS = "yes" 全部⽣效，开启搜索限制
* PRUNEFS 不搜索的⽂件系统
* PRUNENAMES 忽略的⽂件类型
* PRUNEPATHS 忽略的路径 /tmp

### whereis

* 搜索命令所在路径以及帮助⽂档所在位置
* whereis 命令名

```bash
whereis ls
```

* -b 只查找可执⾏⽂件
* -m 只查找帮助⽂件

### which

* 可以看到别名 `which ls`
* 能看到的都是外部安装的命令
* ⽆法查看Shell⾃带的命令，如 `which cd`

### echo $PATH

```bash
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

* 定义的是系统搜索命令的路径
* echo $PATH

### find

* ⽂件搜索命令
* find [搜索范围] [搜索条件]

#### 按名称搜索

避免⼤范围的搜索，会⾮常消耗系统资源

```bash
find / -name aaa.log
```

#### 通配符

* find是在系统当中搜索符合条件的⽂件名，如果需要匹配，使⽤通配符匹配，通配符是完全匹配
* 通配符
  * *匹配任意内容
  * ? 匹配任意⼀个字符
  * [] 匹配任意⼀个中括号内的字符

```bash
find . -name "ab[cdef]"
```

#### 不区分⼤⼩写 -i

```bash
find / -iname "ab[cdef]"
```

#### 按所有者进⾏搜索 -u

```bash
find /root -user root
find /root -nouser
```

#### grep

* 在⽂件当中匹配符合条件的字符串
* grep "10" access.log
  * -i 忽略⼤⼩写
  * -v 排除指定字符串
* find命令，在系统当中搜索符合条件的⽂件名，如果需要匹配，使⽤通配符匹配，通配符是完全匹配
* grep命令 在⽂件当中搜索符合条件的字符串，如果需要匹配，使⽤正则表达式进⾏匹配，正则表达式时包含匹配

## 压缩

```bash
.zip` `.gz` `.bz2` `.tar.gz` `.tar.bz2
```

### zip

* 压缩⽂件 zip 压缩⽂件名 源⽂件
* 压缩⽬录 zip -r 压缩⽂件名 源⽬录
* 解压 unzip 压缩⽂件名

```bash
mkdir book
touch book/1.txt
touch book/2.txt
zip -r book.zip book
unzip book.zip
```

### gzip

| 命令 | 示例 | 含义 |
| :-: | :-: | :- |
| gzip 源⽂件 | gzip a.txt | 压缩为.gz格式的压缩⽂件，源⽂件会消失 |
| gzip -c 源⽂件 > 压缩⽂件 | gzip -c  yum.txt >yum.txt.gz | 压缩为.gz格式的压缩⽂件，源⽂件不会消失 |
| gzip -r ⽬录 | gzip -r xx | 压缩⽬录下的所有⼦⽂件，但是不压缩⽬录 |
| gzip -d 压缩⽂件名 | gzip -d yum.txt.gz  | 解压缩⽂件,不保留压缩包 |
| gunzip 压缩⽂件 | gunzip yum.txt.gz | 解压缩⽂件,不保留压缩包 |

* 压缩是压缩⽬录下的⽂件

### bz2

| 命令 | 示例 | 含义 |
|:-:|:-:|:-|
|bzip2 源⽂件 | bzip2 1.txt | 压缩为.bz2格式的⽂件，不保留源⽂件 |
|bzip2 -k 源⽂件 | zip2 -k 1.txt | 压缩为.bz2格式的⽂件，保留源⽂件 |
|bzip2 -d 压缩⽂件名 | bzip2 -d 1.txt.bz2 | 解压压缩包 |
|bunzip2 压缩⽂件名 | bunzip2 1.txt.bz2 | 解压压缩包 |

* bzip2 不能压缩⽬录

### tar

* 打包命令
* tar -cvf 打包⽂件名 源⽂件
  * -c 打包
  * -v 显示过程
  * -f 指定打包后的⽂件名

```bash
tar -cvf book.tar book
gzip book.tar
bzip2 book.tar
```

* x 解打包

```bash
tar -xvf book.tar
```

## 关机重启

### w

查看登录⽤户信息

* USER 登录的⽤户名
* TTY 登录的终端 tty1 本地终端 pts/0远程终端
* FROM 登录的IP
* LOGIN 登录时间
* IDLE ⽤户闲置时间
* JCPU 该终端所有进程占⽤的时间
* PCPU 当前进程所占⽤的时间
* WHAT 正在执⾏的命令

### who

查看登录⽤户信息

* USER 登录的⽤户名
* TTY 登录的终端 tty1 本地终端 pts/0远程终端
* LOGIN 登录时间（登录的IP）

### last

查看当前登录和过去登录的⽤户信息 默认读取 /var/log/wtmp ⽂件

* ⽤户名
* 登录终端
* 登录IP
* 登录时间
* 退出时间(在线时间)

### lastlog

查看所有⽤户的最后⼀次登录时间

* ⽤户名
* 登录终端
* 登录IP
* 最后⼀次登录时间

## vi常用

* :w 保存
* :q 退出
* :! 强制保存
* :ls 列出所有的⽂件
* :n 下⼀个
* :N 上⼀个
* :15 跳转到指定⾏
* /xxx 从光标位置开始向后搜索 xxx 字符串
* ?xxx 从光标位置开始向前搜索