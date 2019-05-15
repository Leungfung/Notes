# MAC OSX 环境安装Dokuwiki

[TOC]

## 配置 Mac OSX 中 Apache 服务器 

### 启动 Apache 服务器中模块

- 检查 Mac OSX 中 Apache 服务器版本。终端中输入 httpd -v :
  ```shell
  $ httpd -v
  Server version: Apache/2.4.27 (Unix)
  Server built:   Jul 15 2017 15:41:46
  $ 
  ```

- 启动 Apache 服务器
  * 在终端输入 sudo apachectl start 即可启动 Apache。
    ```shell
    $ sudo apachectl start
    ```
  * 启动后，在浏览器中输入 http://127.0.0.1 或 http://localhost 如果看到 It Works! 页面那么 Apache 就启动成功了。
  * Apache 默认站点的根目录为系统级根目录 /Library/WebServer/Documents。
  * 启动后，你可以通过编辑 /etc/apache2/httpd.conf 文件来修改 Apache 配置。

- 备份 httpd.conf，打开终端输入以下命令:
  ```shell
  $ sudo cp /private/etc/apache2/httpd.conf /private/etc/apache2/httpd.conf.bak
  ```

- 打开 httpd.conf 文件
  ```shell
  $ sudo vi /private/etc/apache2/httpd.conf
  ```

- 修改 httpd.conf 文件内容,查找以下代码；
  - 启用PHP模块；
    * 代码: 
      ```php
      #LoadModule php7_module libexec/apache2/libphp7.so
      ```
    * 修改为:
      ```php
      LoadModule php7_module libexec/apache2/libphp7.so
      ```
  - 启用用户自定义站点目录,用户目录建立方式见《在用户目录下创建 Sites 目录》；
    * 代码：
      ```php
      #LoadModule userdir_module libexec/apache2/mod_userdir.so
      ```

    * 修改为：
      ```php
      LoadModule userdir_module libexec/apache2/mod_userdir.so
      ```

    * 代码：
      ```
      # User home directories
      #Include /private/etc/apache2/extra/httpd-userdir.conf
      ```
    * 修改为：
      ```
      # User home directories
      Include /private/etc/apache2/extra/httpd-userdir.conf
      ```

    * 保存 httpd.conf 修改：按下 :wq 保存修改退出编辑；

    * 编辑 /etc/apache2/extra/httpd-userdir.conf 文件,
      ```shell
      $ cd /etc/apache2/extra
      $ ls
      $ sudo vi httpd-userdir.conf
      ```

    * 找到下列代码，并将前面的注释符号 # 删除：
      ```c
      #Include /private/etc/apache2/users/*.conf
      ```

    * 代码修改为
      ```c
      Include /private/etc/apache2/users/*.conf
      ```

    * 保存 httpd.conf 修改：按下 :wq 保存修改退出编辑；

- 可以选择先停止 Apache 服务后再次启动使得配置生效 在终端输入: sudo apachectl stop , sudo apachectl start 
  ```shell
  $ sudo apachectl stop
  $ sudo apachectl start
  ```

- 或者重新启动 Apache 使得配置生效,在终端输入: sudo apachectl restart  
  ```shell
  $ sudo apachectl restart
  ```


  - 一般情况建议用户建立自己的站点目录(用户级根目录)，用于存放wiki数据而不适用系统默认的目录。具体建立操作：
    - 在用户目录下创建 Sites 目录
      * 进入本机用户目录 cd /Users/lyj/(注释：lyj为本机用户名对应的目录);
        ```shell
        $ cd /Users/lyj/
        ```
      * 查看是否存在 Sites 目录 ls 旧的 Mac 系统中如果该目录已存在，则略过以下步骤
        ```shell
        $ ls
        Applications		Library			STM32Cube
        Desktop			    Movies			Sites
        Dev			        Music			Texas Instruments
        Documents		    Pictures		ti
        Downloads		    Public			workspace_v7
        ```
      * 创建 Sites 目录
        ```shell
        $ mkdir Sites
        $ touch Sites/.localized
        ```
    - 检查 username.conf 文件
      * 进入 cd /etc/apache2/users 检查目录下是否存在 username.conf 文件（注释：username 为当前用户名例如本机为 lyj）
        ```shell
        $ cd /etc/apache2/users
        $ ls
        Guest.conf       lyj.conf
        ```
      * 如果没有则创建一个 sudo touch username.conf，并修改文件权限 sudo chmod 644 username.conf。
        ```shell
        $ sudo touch username.conf
        $ sudo chmod 644 username.conf
        ```
      * 创建之后，打开  username.conf 文件，sudo vi username.conf 将下面的配置信息写入文件，username 依然为当前用户名
        ```shell
        $ sudo vi username.conf
        ```
      * 在文件中输入以下内容
        * Apache 2.2
          ``` 
          <Directory "/Users/lyj/Sites/">
          Options Indexes MultiViews
          AllowOverride All
          # OSX 10.9 / Apache 2.2
          Order from deny, allow
          </Directory>
          ```
        * Apache 2.4
          ```
          <Directory "/Users/lyj/Sites/">
          Options Indexes MultiViews
          AllowOverride All
          # OSX 10.10 / Apache 2.4
          Require all granted
          </Directory>
          ```
    - 在 Apache 中启用 用户目录，方法见《启用用户自定义站点目录》


## 下载安装Dokuwiki
  - 在Safari中下载 [dokuwiki-c5525093cf2c4f47e2e5d2439fe13964.tar](http://download.dokuwiki.org/)文件会保存到 ~/Downloads
  - 解压下载文件到~/Site(站点)文件夹, 并改名为“dokuwiki”:
    ```shell
    $ cd ~/Downloads && tar -zxvf dokuwiki-c5525093cf2c4f47e2e5d2439fe13964.tar
    $ mv dokuwiki-c5525093cf2c4f47e2e5d2439fe13964 ~/Sites/dokuwiki
    $ cd ~/Sites/dokuwiki
    $ sudo chown -R www data conf lib/plugins
    ```
## 配置Dokuwiki
  - 打开 Safari 浏览器 http://localhost/~your_username/dokuwiki/install.php 例如本机地址为：http://localhost/~lyj/dokuwiki/install.php
  - 按画面指示完成 WIKI Name、用户名、密码、访问权限设置后，点击完成安装设置；
  - 安装完毕按系统提示删除 install.php 文件
  - 点击：http://localhost/~lyj/dokuwiki/doku.php 可以开始WIKI的使用；

