# FAQ
本文档收集了部分用户在使用 uTools 过程中遇到的问题，如果这里没有你遇到的问题，可以在 uTools 官方论坛里发帖寻求帮助。

## 安装
### 安装时遇到了「进度条卡在一半」的情况怎么办？<Badge text="Windows"/>
导致这个问题的原因可能是由于旧版本的 uTools 未卸载干净，可尝试按照以下步骤进行处理。
1. 检查「程序与功能」界面中是否还有旧版本 uTools 安装项存在，如果存在旧版本，先卸载旧版本再重新安装新版本 uTools。
2. 注册表残留问题 参考 https://yuanliao.info/d/2030
3. 检查 uTools 安装程序是否被「360」、「火绒」等杀毒软件阻止安装，请将 uTools 安装程序放入杀毒软件白名单后再重新安装新版本 uTools。

### 安装时遇到了「无法打开 uTools，因为 Apple 无法检查是否包含恶意软体」的情况怎么办？<Badge text="macOS"/>
依次打开「系统偏好设置」→「安全性与隐私」→「通用」，选择「仍要安装」即可。

### 安装时遇到了「A JavaScript error occurred in the main process」的情况怎么办？<Badge text="Linux"/>
参考 [Aksuru](https://yuanliao.info/u/51376)、[littlezhong](https://yuanliao.info/u/51839) 和 [microcheiria](https://yuanliao.info/u/34323) 在 uTools 论坛中提出的 [解决方案](https://yuanliao.info/d/1865)。

## 使用
### 如何使用「管理员」权限打开软件？<Badge text="Windows"/>
在 uTools 列表里选中要打开的软件，使用快捷键 `Ctrl + 回车（Enter）`打开即可。

### uTools 搜不到绿色软件？
1. 找到该绿色软件的主程序，复制后呼出 uTools 输入框或拖动该文件到 uTools 输入框中，即可看到「加入到 uTools 搜索启动」的选项，确认后可在 uTools 列表中搜索到该软件。（文件和文件夹也可以添加）

## 插件
### 「剪贴板」插件安装失败怎么办？
「剪贴板」插件由于实现原理特殊，不支持离线安装，请在联网环境下从插件中心安装后再离线使用。

## 付费
### uTools 会收费吗？
uTools 目前采用会员付费制，基础功能永久免费使用。会员用户可以享受到包括「数据同步」、「超级面板」等功能。

### 可以在公司环境使用吗？
可以在任意环境使用 uTools，无须获得额外的授权。

## 其他
### 为什么任务管理器中会有这么多名为「uTools」的进程？
这些进程大部分为 uTools 的插件进程，uTools 的每个插件都会创建一个独立的进程来运行，目的是为了避免一个插件运行出错后导致其他插件甚至整个软件无法使用。
> 在uTools主输入框输入`clear`，可以清理所有正在运行的插件.

### uTools 是否会开源？
uTools 为商业软件，暂无开源计划。
