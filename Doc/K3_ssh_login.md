# K3 ssh 登陆方法

[TOC]

## 登陆地址

默认地址：192.168.2.1

## 登陆方式

```shell
# 登入 Admin
# 用户名：admin
# 密码：本机路由管理密码
leo@bogon  ~  ssh admin@192.168.2.1
# 在此输入密码(密码不显示)回车结束输入
admin@192.168.2.1's password:
[K3 /tmp/media/nand]# vi set_webshell.sh
[K3 /tmp/media/nand]#
# 登入 root
# 用户名：root
# 密码：admin
leo@bogon  ~  ssh root@192.168.2.1
The authenticity of host '192.168.2.1 (192.168.2.1)' can't be established.
ECDSA key fingerprint is SHA256:skj7Mo00a1eYyjvS5EGiHuUbyPBbsvAsVbtiMTg/xxk.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.2.1' (ECDSA) to the list of known hosts.
root@192.168.2.1's password:
Permission denied, please try again.
root@192.168.2.1's password:

---------------------------------------------------
     Product : K3   FW Version: V2.1D
---------------------------------------------------
[K3 /]# ls
bin    etc    mcu    mnt    proc   sbin   tmp    var
dev    lib    media  opt    root   sys    usr    www
```

## 软件包管理工具OPKG

Opkg 是一个轻量快速的套件管理系统，目前已成为 Opensource 界嵌入式系统标准。常用于路由、交换机等嵌入式设备中，用来管理软件包的安装升级与下载。

**常用命令**

* `opkg update` 更新可以获取的软件包列表
* `opkg upgrade` 对已经安装的软件包升级
* `opkg list` 获取软件列表
* `opkg install` 安装指定的软件包
* `opkg remove` 卸载已经安装的指定的软件包

## 安装git

```shell
[K3 /tmp/share/sda2]# opkg install git
Installing git (2.15.1-1) to root...
Downloading http://pkg.entware.net/binaries/armv7/git_2.15.1-1_armv7soft.ipk
Installing libc (2.23-6) to root...
Downloading http://pkg.entware.net/binaries/armv7/libc_2.23-6_armv7soft.ipk
Installing libgcc (6.3.0-6) to root...
Downloading http://pkg.entware.net/binaries/armv7/libgcc_6.3.0-6_armv7soft.ipk
Installing libssp (6.3.0-6) to root...
Downloading http://pkg.entware.net/binaries/armv7/libssp_6.3.0-6_armv7soft.ipk
Installing librt (2.23-6) to root...
Downloading http://pkg.entware.net/binaries/armv7/librt_2.23-6_armv7soft.ipk
Installing libpthread (2.23-6) to root...
Downloading http://pkg.entware.net/binaries/armv7/libpthread_2.23-6_armv7soft.ipk
Installing libopenssl (1.0.2n-1) to root...
Downloading http://pkg.entware.net/binaries/armv7/libopenssl_1.0.2n-1_armv7soft.ipk
Installing zlib (1.2.11-1) to root...
Downloading http://pkg.entware.net/binaries/armv7/zlib_1.2.11-1_armv7soft.ipk
Configuring libgcc.
Configuring libc.
Configuring libpthread.
Configuring librt.
Configuring libssp.
Configuring zlib.
Configuring libopenssl.
Configuring git.
```

## 建立裸库

```shell
# 远程机打开git服务
leo@bogon  ~  git daemon --export-all --disable=receive-pack --base-path=/Users/leo/repo /Users/leo/repo
# 克隆裸库
K3 /tmp/share/sda2/git_repo/firmware]# git clone --bare git://192.168.2.8/firmware/xxxx_fw.git
```



## macOS 终端里神秘的 bogon 及解决方法

Mac 下的终端经常有时候前面的计算机名会错误的显示成 bogon. 这是因为终端会先向 DNS 请求查询当前 IP 的反向域名解析的结果，如果查询不到再显示我们设置的计算机名。而由于我们的 DNS 错误地将保留地址反向的 NS 查询结果返回了 bogon. 其中 bogon 本应该用来指虚假的 IP 地址，而非保留 IP 地址。因此就出现了会时不时地打印 bogon 这种奇怪名字作为计算机名的现象了。那么如何让终端只显示我们想要的计算机名而不总是从 DNS 返回结果呢？

解决方案：
在终端中执行以下命令即可（需要输入一次管理员密码）

```shell
1 sudo hostname your-desired-host-name
2 sudo scutil --set LocalHostName $(hostname)
3 sudo scutil --set HostName $(hostname)
```