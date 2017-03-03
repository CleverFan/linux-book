## zsh

> Zsh 是 Shell 中的一种，什么 Shell 你可以再搜索下，简单粗暴讲就是一个：命令解释器，你输入什么命令，它就执行什么，这个东西再 Unix 世界还有其他几个。

先看下你的 CentOS 支持哪些 shell：`cat /etc/shells`，正常结果应该是这样的：

```
/bin/sh
/bin/bash
/sbin/nologin
/bin/dash
/bin/tcsh
/bin/csh
```

> 默认 CentOS / Ubuntu / Mac 系统用的是 Bash

## Zsh 和 oh-my-Zsh 的关系

由于 Zsh 配置门槛有点高，或者说需要专门花时间去了解 Zsh 才能配置好一个好用的 Zsh，也因为这样，用户也就相对少了。

直到有一天 oh-my-Zsh 的作者诞生，他想要整理出一个配置框架出来，让大家直接使用他的这个公认最好的 Zsh 配置，省去繁琐的配置过程。所以，oh-my-Zsh 就诞生了，它只是会了让你减少 Zsh 的配置，然后又可以好好享受 Zsh 这个 Shell。

Mac 和一般 Linux 默认的 shell 是 bash，一般人都觉得不好用，我作为一般人，也喜欢 Zsh，所以这里就用 Zsh。

> Zsh 官网：[https://www.zsh.org/](https://www.zsh.org/)  
> oh-my-Zsh 官网：[http://ohmyz.sh/](http://ohmyz.sh/)

## 安装zsh

```
yum install zsh
```

![](/assets/zsh1.png)

![](/assets/zsh2.png)

> 检查下系统的 shell：`cat /etc/shells`，你会发现多了一个：`/bin/zsh`

## 安装oh-my-zsh

> 进行下一步之前，请确保安装了git。

```
wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O - | sh
```

![](/assets/omzsh1.png)

> * 在以root 用户为前提下，oh-my-zsh 的安装目录：**/root/.oh-my-zsh**
>
> * 在以 root用户为前提下，Zsh的配置文件位置：**/root/.zshrc**
>
> * 为root 用户设置 zsh 为系统默认shell：chsh -s /bin/zsh root
>
> * 如果你要重新恢复到 bash：chsh -s /bin/bash root

现在你关掉终端或是重新连上 shell，现在开头是一个箭头了，如下图：

![](/assets/omzsh2.png)

## Zsh 软件特色

* 不区分大小写智能提示。我是不喜欢大小写区分的那种人，所以用了 zsh 之后，经常按 Tab 进行提示。

* 此外，按下 tab 键显示出所有待选项后，再按一次 tab 键，即进入选择模式，进入选择模式后，按 tab 切向下一个选项，按 shift + tab 键切向上一个选项，ctrl+f/b/n/p 可以向前后左右切换。

* kill + 空格键 + Tab键，列出运行的进程，要啥哪个进程不需要再知道 PID 了，当然了 zsh，提供了让你知道 PID 的方法：  
  比如输入：kill vim，再按下 tab，会变成：kill 5643

* ls _\*/_，分层级地列出当前目录下所有文件及目录，并递归目录

* ls \*.png 查找当前目录下所有 png 文件

* ls _\*/_.png 递归查找

* zsh 的目录跳转很智能，你无需输入 cd 就可直接输入路径即可。比如：.. 表示后退一级目录，../../ 表示后退两级，依次类推。

* 在命令窗口中输入：d，将列出当前 session 访问过的所有目录，再按提示的数字即可进入相应目录。

* 给 man 命令增加结果高亮显示：

  > 编辑配置文件：vim ~/.zshrc，增加下面内容：

  ```
  # man context highlight
  export LESS_TERMCAP_mb=$'\E[01;31m'       # begin blinking
  export LESS_TERMCAP_md=$'\E[01;38;5;74m'  # begin bold
  export LESS_TERMCAP_me=$'\E[0m'           # end mode
  export LESS_TERMCAP_se=$'\E[0m'           # end standout-mode
  export LESS_TERMCAP_so=$'\E[38;5;246m'    # begin standout-mode - info box
  export LESS_TERMCAP_ue=$'\E[0m'           # end underline
  export LESS_TERMCAP_us=$'\E[04;38;5;146m' # begin underline
  ```

  刷新配置文件：`source ~/.zshrc`，重新查看 man 的命令就可以有高亮了。

## Zsh 配置

### 差异

* 我们现在增加系统变量在：/etc/profile 后，输入命令：`source /etc/profile` 之后，重启服务器发现刚刚的系统变量现在没效果。

  > 解决办法：`vim ~/.zshrc`，在该配置文件里面增加一行：`source /etc/profile`，然后刷新 zsh 的配置：`source ~/.zshrc`。

* 用bash的时候，写环境变量可能写在了bash\_profile里，但是用zsh的时候，环境变量就应该写在.zshrc里了，配置的时候注意一下。

### 插件

* 启用 oh-my-zsh 中自带的插件。

* oh-my-zsh 的插件列表介绍（太长了，用源码不精准地统计下有 149 个）：[https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins)

* 我们看下安装 oh-my-zsh 的时候自带有多少个插件：ls -l /root/.oh-my-zsh/plugins \|grep "^d"\|wc -l，我这边得到的结果是：211

* 编辑配置文件：vim /root/.zshrc，找到下图的地方，怎么安装，原作者注释写得很清楚了，别装太多了，默认 git 是安装的。

  > ![](/assets/omzshchajian.png)

### 插件推荐：

* wd\(编辑配置文件，添加上 wd 的名字：vim /root/.zshrc\)

  简单地讲就是给指定目录映射一个全局的名字，以后方便直接跳转到这个目录，比如：

  > 我常去目录：/opt/setups，每次进入该目录下都需要这样：`cd /opt/setups`  
  > 现在用 wd 给他映射一个快捷方式：`cd /opt/setups ; wd add setups`  
  > 以后我在任何目录下只要运行：`wd setups` 就自动跑到 /opt/setups 目录下了  
  > 插件官网：[https://github.com/mfaerevaag/wd](https://github.com/mfaerevaag/wd)

* autojump

  * 这个插件会记录你常去的那些目录，然后做一下权重记录，你可以用这个命令看到你的习惯：`j --stat`，如果这个里面有你的记录，那你就只要敲最后一个文件夹名字即可进入，

  * 比如我个人习惯的 program：j program，就可以直接到：/usr/program

  * 插件官网：[https://github.com/wting/autojump](https://github.com/wting/autojump)

  * 官网插件下载地址：[https://github.com/wting/autojump/downloads](https://github.com/wting/autojump/downloads)

  * 插件下载：`wget https://github.com/downloads/wting/autojump/autojump_v21.1.2.tar.gz`

  * 解压：`tar zxvf autojump_v21.1.2.tar.gz`

  * 进入解压后目录并安装：`cd autojump_v21.1.2/ ; ./install.sh`

  * 再执行下这个：`source /etc/profile.d/autojump.sh`

  * 编辑配置文件，添加上 autojump 的名字：vim /root/.zshrc

### 主题

捣搞主题和插件思路一样

* oh-my-zsh 的主题列表介绍（还是太长了）：[https://github.com/robbyrussell/oh-my-zsh/wiki/Themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)

* 我们看下安装 oh-my-zsh 的时候，自带有多少个：ls -l /root/.oh-my-zsh/themes \|grep "^-"\|wc -l，我这边得到的结果是：140

* 我个人品味地推荐的是（排名有先后）：  
  `ys`  
  `agnoster`  
  `avit`  
  `blinks`

  > ys效果：
  >
  > ![](/assets/omzshys.png)

* 编辑配置文件：vim /root/.zshrc，找到下图的地方，怎么安装，原作者注释写得很清楚了，如果你没特别的喜欢那就选择随机吧。

  > ![](/assets/omzshzhuti.png)



