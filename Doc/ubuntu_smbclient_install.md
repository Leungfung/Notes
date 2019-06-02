# ubuntu 使用 smbclient 访问 smb

[TOC]

## smb的配置

* 安装smbclient
  ```shell
  leo@ubuntu:~$ sudo apt-get install smbclient 
  ```
  
* 查看文件服务器地址下的目录
  ```shell
  leo@ubuntu:~$ smbclient -L 192.168.2.1
  WARNING: The "syslog" option is deprecated
  Enter WORKGROUP\leo's password: 
  
  	Sharename       Type      Comment
  	---------       ----      -------
  	sda2            Disk      
  	IPC$            IPC       IPC Service (Samba 3.0.25b)
  Reconnecting with SMB1 for workgroup listing.
  
  	Server               Comment
  	---------            -------
  
  	Workgroup            Master
  	---------            -------
  
  ```
  
* 连接目录

  ```shell
  leo@ubuntu:~$ smbclient //192.168.2.1/sda2
  WARNING: The "syslog" option is deprecated
  Enter WORKGROUP\leo's password: 
  Try "help" to get a list of possible commands.
  smb: \> 
  ```

  如果需要制定用户登录

  ```shell
  leo@ubuntu:~$ smbclient //192.168.2.1/sda2 -U leo
  ```

  -U 指定用户，leo smb的用户名

* 查看smb目录

  ```shell
  smb: \aria2\> ls
    .                                   D        0  Sun Jun  2 01:19:55 2019
    ..                                  D        0  Thu Jan  1 08:00:07 1970
    Xilinx_Vivado_SDK_2019.1_0524_1430.tar.gz      N 22964656463  Sun Jun  2 01:19:44 2019
  		22964656463 blocks of size 1024. 22964656463 blocks available
  
  ```

## 拷贝文件到本地

```shell
smb: \aria2\> get Xilinx_Vivado_SDK_2019.1_0524_1430.tar.gz Xilinx_Vivado_SDK_2019.1_0524_1430.tar.gz
```

## 常用命令

```shell
#执行所用的SHELL命令，或让用户进入 SHELL提示符
$ ![shell command]
#切换到服务器端的指定目录，如未指定，则 smbclient 返回当前本地目录
$ cd [DIR]
#切换到客户端指定的目录；
$ lcd [DIR]
#列出当前目录下的文件；
$ dir 
或 
$ ls 
#退出smbclient
$ exit
或
$ quit
#从服务器上下载file1，并以文件名file2存在本地机上；如果不想改名，可以把file2省略
$ get file1  file2
#从服务器上下载多个文件；
$ mget file1 file2 file3  filen
#在服务器上创建目录
$ md DIR
$ mkdir DIR     
#删除服务器上的目录
$ rd DIR
或
$ rmdir DIR      
#向服务器上传一个文件file1,传到服务器上改名为file2；
$ put file1 file2      
#向服务器上传多个文件
$ mput file1 file2 filen  
```


## smbclient命令详解

**smbclient命令**属于samba套件，它提供一种命令行使用交互式方式访问samba服务器的共享资源。

### 语法

```shell
smbclient(选项)(参数)
```

### 选项

```html
-B<ip地址>：传送广播数据包时所用的IP地址；
-d<排错层级>：指定记录文件所记载事件的详细程度；
-E：将信息送到标准错误输出设备；
-h：显示帮助；
-i<范围>：设置NetBIOS名称范围；
-I<IP地址>：指定服务器的IP地址；
-l<记录文件>：指定记录文件的名称；
-L：显示服务器端所分享出来的所有资源；
-M<NetBIOS名称>：可利用WinPopup协议，将信息送给选项中所指定的主机；
-n<NetBIOS名称>：指定用户端所要使用的NetBIOS名称；
-N：不用询问密码；
-O<连接槽选项>：设置用户端TCP连接槽的选项；
-p<TCP连接端口>：指定服务器端TCP连接端口编号；
-R<名称解析顺序>：设置NetBIOS名称解析的顺序；
-s<目录>：指定smb.conf所在的目录；
-t<服务器字码>：设置用何种字符码来解析服务器端的文件名称；
-T<tar选项>：备份服务器端分享的全部文件，并打包成tar格式的文件；
-U<用户名称>：指定用户名称；
-w<工作群组>：指定工作群组名称。
```

### 参数

smb服务器：指定要连接的smb服务器。

### 实例

**列出某个IP地址所提供的共享文件夹**

```shell
smbclient -L 198.168.0.1 -U username%password
```