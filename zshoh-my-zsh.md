
## 先说下：Zsh 和 oh-my-Zsh 的关系

> Zsh 是 Shell 中的一种，什么 Shell 你可以再搜索下，简单粗暴讲就是一个：命令解释器，你输入什么命令，它就执行什么，这个东西再 Unix 世界还有其他几个。

由于 Zsh 配置门槛有点高，或者说需要专门花时间去了解 Zsh 才能配置好一个好用的 Zsh，也因为这样，用户也就相对少了。

直到有一天 oh-my-Zsh 的作者诞生，他想要整理出一个配置框架出来，让大家直接使用他的这个公认最好的 Zsh 配置，省去繁琐的配置过程。所以，oh-my-Zsh 就诞生了，它只是会了让你减少 Zsh 的配置，然后又可以好好享受 Zsh 这个 Shell。

Mac 和一般 Linux 默认的 shell 是 bash，一般人都觉得不好用，我作为一般人，也喜欢 Zsh，所以这里就用 Zsh。

> Zsh 官网：https://www.zsh.org/
oh-my-Zsh 官网：http://ohmyz.sh/

## 安装zsh

```
yum install zsh
```

![](/assets/zsh1.png)



![](/assets/zsh2.png)

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









