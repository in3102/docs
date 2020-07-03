[TOC]

# FAQ
本文档收集了部分用户在使用 uTools 过程中遇到的问题，如果这里没有你遇到的问题，可以在 uTools 官方论坛里发帖寻求帮助。

## 安装
### `win` 安装时遇到了「进度条卡在一半」的情况怎么办？
导致这个问题的原因可能是由于旧版本的 uTools 未卸载干净，可尝试按照以下步骤进行处理。
1. 检查「程序与功能」界面中是否还有旧版本 uTools 安装项存在，如果存在旧版本，先卸载旧版本再重新安装新版本 uTools。
2. 如果没有在第1步中找到旧版本安装项，则使用「Everything」等搜索工具全盘查找带有「uTools」字样的文件或文件夹，将它们全部删除后再重新安装新版本 uTools。
3. 检查 uTools 安装程序是否被「360」、「火绒」等杀毒软件阻止安装，请将 uTools 安装程序放入杀毒软件白名单后再重新安装新版本 uTools。

### `mac` 安装时遇到了「无法打开 uTools，因为 Apple 无法检查是否包含恶意软体」的情况怎么办？
依次打开「系统偏好设置」→「安全性与隐私」→「通用」，选择「仍要安装」即可。

### `linux` 安装时遇到了「A JavaScript error occurred in the main process」的情况怎么办？
以下引用 [Aksuru](https://yuanliao.info/u/51376)、[littlezhong](https://yuanliao.info/u/51839) 和 [microcheiria](https://yuanliao.info/u/34323) 在 uTools 论坛中提出的 [解决方案](https://yuanliao.info/d/1865), 仅供参考.
> ubuntu 16.04 LTS碰到同样问题，已解决。
> libcryto是libssl1里边的，可以通过dpkg -S libcrypto.so查看版本，我的机器返回的是：
> >libssl-dev:amd64: /usr/lib/x86_64-linux-gnu/libcrypto.so
> >libssl1.0.0:amd64: /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
>
> 系统版本是1.0.0，要解决这个问题需要安装1.1版本的openssl，但是1.1不在16.04的repository里，所以需要手动安装，不过最好不要通过deb安装，可能搞乱系统，所以我是本地编译安装然后指定路径运行utools的方法解决的，具体过程如下：
> 首先新建一个希望安装openssl的文件夹，例如`mkdir $HOME/openssl`,
> 然后从https://launchpad.net/ubuntu/+source/openssl 下载1.1版本的源文件，选择`1.1.0g-2ubuntu4 -> > openssl_1.1.0g.orig.tar.gz`
> 解压出来，
> > cd openssl-1.1.0g
> > ./config --prefix=\$HOME/openssl --openssldir=\$HOME/openssl
> > make
> > make test
> > make install
>
> 如果报错应该是dependencies问题，我是直接成功了，可以在`openssl/lib`里看到libcrypto.so.1.1。
> 安装好了之后下一步就是要指定路径运行了，首先把openssl的安装路径加入到环境变量里，我用的是zshrc，所以在`$HOME/.> zshrc`里加入一行：
> `export LD_LIBRARY_PATH="/home/your_user_name/openssl/lib:$LD_LIBRARY_PATH"`，bashrc同理，加完以后记得> source刷新一下。
> 接下来需要更改utools的desktop文件，`utools.desktop`文件可以在`/usr/share/applications`找到，然后对其中EXEC一行> 进行如下修改：
> `EXEC=env LD_LIBRARY_PATH=/home/your-user-name/openssl/lib:$LD_LIBRARY_PATH /opt/uTools/utools %U`
> 另外如果有`Try Exec`的话记得注释掉。
> 然后应该问题就解决了。

> 你运行一下看看desktop文件有没有报错:
> `desktop-file-validate utools.desktop`
> 我是提示"\$"要改为"\\\\$", 然后就可以图标启动了

> 感谢帮助,通过`desktop-file-validate`解决问题.
> 我原来加入的代码段为:
> `Exec=env LD_LIBRARY_PATH=/home/your-user-name/openssl/lib:$LD_LIBRARY_PATH /opt/uTools/utools  %U`
> 修改后,添加引号""及\后就可以运行了:
> `Exec=env "LD_LIBRARY_PATH=/home/your-user-name/openssl/lib:\\$LD_LIBRARY_PATH" /opt/uTools/utools`

## 使用
### `win` 如何使用「管理员」权限打开软件？
在 uTools 列表里选中要打开的软件，使用快捷键 `Ctrl + 回车（Enter）`打开即可。

### uTools 中如何搜到可直接运行的绿色软件？
1. 找到该绿色软件的主程序（可以是启动程序的「快捷方式」），复制后激活 uTools 输入框或拖动该文件到 uTools 输入框中，即可看到「加入到 uTools 本地应用搜索」的选项，确认后可在 uTools 列表中搜索到该软件。
> - 上述的「主程序」文件支持 `.exe`、`.bat`、`.lnk`（即「快捷方式」）和 `.app`（macOS）等4种格式。
> - 添加的主程序文件在被移动或删除后会自动移出 uTools 的搜索列表，无需手动操作。
2. 在 uTools 的设置中可以配置「自定义应用目录」指定一个目录，将绿色软件的主程序放入该目录后会自动被 uTools 检索到。
> 为了防止 uTools 索引大量无用的可执行文件，「自定义应用目录」指定的目录中仅支持`.lnk`和`.app`两种文件格式。

## 插件
### 如何在没有网络的情况下安装 uTools 插件？
在 [插件下载页面](https://api.u-tools.cn/Plugins/Developer/allPlugins) 下载对应的插件安装文件，复制安装文件后激活 uTools 的输入框或直接将安装文件拖入 uTools 的输入框即可看到安装插件的选项。

### 「剪贴板」插件安装失败怎么办？
「剪贴板」插件由于实现原理特殊，不支持离线安装，请在联网环境下从插件中心安装后再离线使用。

## 付费
### uTools 会收费吗？
uTools 目前采用会员付费制，基础功能永久免费使用，会员用户可以享受到包括「数据同步」、「语音面板」等需要服务器资源或付费接口支持的功能。

## 其他
### 为什么任务管理器中会有这么多名为「uTools」的进程？
这些进程大部分为 uTools 的插件进程，uTools 的每个插件都会创建一个独立的进程来运行，目的是为了避免一个插件运行出错后导致其他插件甚至整个软件无法使用。
> 在uTools主输入框输入`clear`，可以清理所有正在运行的插件.

### uTools 是否会开源？
uTools 为商业软件，暂无开源计划。
