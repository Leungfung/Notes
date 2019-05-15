# Mac OSX 下软件包管理器 brew

使用Mac的同学一定都会需要软件包管理工具的，在Mac上brew是个不错的选择。

在国内使用brew通常会应为网络的限制造成下载软件包速度非常缓慢甚至无法下载。

下面的操作可以将brew内使用的github源替换为国内的镜像源提升访问速度。

访问[brew官网](https://brew.sh/index_zh-cn.html)网页上会有详细的安装介绍，还是多国语言版哦！

偷懒的小伙伴就复制以下内容粘贴至终端直接运行:

安装brew：

```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

替换源：

```shell
#替换brew源 
#原始源可以使用 git remote -v 查看
cd "$(brew --repo)"
git remote set-url origin https://mirrors.ustc.edu.cn/brew.git

#替换核心仓库源
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" 
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

#替换Cask源，该源提供mac应用及大型二进制可执行文件
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask"
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git

#替换Bottles源,该源提供预编译二进制软件包
#请根据自己终端选择以下内容
#bash
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile

#zsh
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.zshrc
source ~/.zshrc

#更新brew
brew update
```