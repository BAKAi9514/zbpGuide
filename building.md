# 搭建步骤

> 得到一个搭载了 ZeroBot-Plugin 的 qq 机器人需要`连接QQ的东西`和`ZeroBot-Plugin本体`。

## 连接QQ的东西

现在是后 go-cqhttp 时代，比较流行的代替 gocq 的东西有`LLOneBot`和`NapCatQQ`之类。

### LLOneBot

LLOneBot 支持到最新版本的 QQ。请避免使用 9.9.7(21804) 之前的版本，以免出现意料之外的问题。

**更多问题或详细配置请参考 [官方文档](https://llonebot.github.io/zh-CN/guide/getting-started)，养成勤看文档少问问题的好习惯！**

#### Windows 安装

找到 [项目下载地址](https://github.com/LLOneBot/LLOneBot/releases)，下载`LLOneBot.zip`双击运行即可，之后打开QQ的设置，看到了 LLOneBot 就代表安装成功了。

#### Linux 安装

使用安装脚本安装 [LiteLoaderQQNT](https://github.com/Mzdyl/LiteLoaderQQNT_Install/releases) 或参考 [这个](https://github.com/LLOneBot/llonebot-docker) 安装 docker 版本。若你的 Linux 没有图形化界面或者你的 Linux 上的 QQ 出现各种问题，请使用下文将介绍的`NapCatQQ`。

#### 启动前不可或缺的配置

遵循 [文档](https://llonebot.github.io/zh-CN/guide/configuration#%E6%AD%A3%E5%90%91WS%E9%85%8D%E7%BD%AE) 的指示配置好 **ws 正向连接**，等会 zbp 会接上来。

> **更多问题或详细配置请参考 [官方文档](https://llonebot.github.io/zh-CN/guide/getting-started)，养成勤看文档少问问题的好习惯！**

> **更多问题或详细配置请参考 [官方文档](https://llonebot.github.io/zh-CN/guide/getting-started)，养成勤看文档少问问题的好习惯！**

> **更多问题或详细配置请参考 [官方文档](https://llonebot.github.io/zh-CN/guide/getting-started)，养成勤看文档少问问题的好习惯！**

### NapCatQQ

**勤看 [官方文档](https://napneko.github.io/zh-CN/guide/getting-started)！**

首先 [安装 NTQQ](https://napneko.github.io/zh-CN/guide/getting-started#%E5%AE%89%E8%A3%85-qq)：Windows 和有图形界面的 Linux 不用多说（[↓近期开始要多说的部分↓](https://napneko.github.io/zh-CN/guide/BootWay03)）；<u>无图形界面的</u> Linux 下载好`.deb`文件，执行如下命令：

```shell
sudo apt install libgbm1 libasound2
sudo apt install ./这里是文件名.deb
```

其次 [点击安装 NapCatQQ](https://github.com/NapNeko/NapCatQQ/releases) /或使用一键脚本`curl -o napcat.sh https://fastly.jsdelivr.net/gh/NapNeko/NapCat-Installer@master/script/install.sh && sudo bash napcat.sh`进行安装。（更多安装方式 [见](https://napneko.github.io/zh-CN/guide/getting-started#%E5%90%AF%E5%8A%A8)）

NTQQ 和 NapCat 都安装完成之后，打开 NapCat 的`config`目录，找到名为`onebot11_<你的QQ号>.json`的文件（如`onebot11_1234567.json`）；如果没有此文件可以复制`onebot11.json`重命名为`onebot11_<你的QQ号>.json`；找到以下项目并改成以下配置。

```json
{
  ···
  "ws": {
    // 是否启用正向websocket服务
    "enable": true,
    // 正向websocket服务监听的 ip 地址，为空则监听所有地址
    "host": "127.0.0.1",
    // 正向websocket服务端口
    "port": 6700
  },
  ···
}
```

（就是配置正向 ws 连接为`ws://127.0.0.1:6700`）

为了以后开发/使用/排查问题方便，推荐再打开NapCat的`config`目录，找到名为`napcat_<你的QQ号>.json`的文件（如`napcat_1234567.json`），并改成以下配置。

```json
{
  // 是否开启文件日志
  "fileLog": true,
  // 是否开启控制台日志
  "consoleLog": true,
  // 日志等级, 可选值: debug, info, error
  "fileLogLevel": "debug",
  "consoleLogLevel": "debug"
}
```

（就是将日志等级全部改为`debug`）

**勤看 [官方文档](https://napneko.github.io/zh-CN/guide/getting-started)！**
**勤看 [官方文档](https://napneko.github.io/zh-CN/guide/getting-started)！**
**勤看 [官方文档](https://napneko.github.io/zh-CN/guide/getting-started)！**

> `连接 QQ 的东西`安装完成后，可以登陆一次（操作全程有命令行指示）。至此，`连接 QQ 的东西`配置完毕，可以开始安装 zbp 了。

## ZeroBot-Plugin本体

**勤看 [项目界面 Readme.md](https://github.com/FloatTech/ZeroBot-Plugin)！**

记得要同时开着`连接 QQ 的东西`才能正常使用机器人哦~

### 发行版安装

在 [此处](https://github.com/FloatTech/ZeroBot-Plugin/releases) 找到符合你操作系统的版本并下载，其中包含已有的全部插件，运行即可使用。

不过由于已编译内容，配置机器人名字及主人就需要启动时使用命令行指令或新建`config.json`并进行编辑。鉴于每次启动都需要输入命令行指令/额外写一个启动脚本肯定不如直接编辑配置文件来得方便，**此处推荐编辑配置文件**，内容如下。

```json
{
  "zero": {
    "nickname": ["机器人的名字", "可以有多个", "真的"],
    "command_prefix": "/",//只能有一个的指令前缀
    "super_users": [123456789],//机器人主人qq
    "ring_len": 4096,//接收消息环缓冲区大小，0为不设缓冲，并发处理
    "latency": 233000000,//全局处理延时 (ms)
    "max_process_time": 240000000000,//最大处理时间 (min)
    "mark_message": true//是否自动标记消息为已读
  },
  "ws": [{ "Url": "ws://127.0.0.1:6700", "AccessToken": "" }],//鉴于你已经跟着我的引导将正向ws配置为了6700接口，此处不用改
  "wss": null
}
```

### 本地直接安装

1. 安装 [GoLang 环境](https://studygolang.com/dl)。**注意：zbp 只能使用1.21以下版本的 GoLang，下载时请务必注意版本。**
2. 下载 [本项目源码](https://github.com/FloatTech/ZeroBot-Plugin/releases)（名为`Source code`的文件）。
3. 编辑`main.go`，按注释指示添加机器人主人qq/修改机器人名字。
4. Windows下双击`run.bat`文件，Linux下使用`run.sh`运行 zbp。

### 本地编译安装

> 为什么不讲 github actions 在线编译呢？~~因为...你不觉得用了就会被开合机器人主人是谁吗~~

1. 安装 [GoLang 环境](https://studygolang.com/dl)。**注意：zbp 只能使用1.21以下版本的 GoLang，下载时请务必注意版本。**
2. `git clone`本项目，并下载所需包。
```bash
git clone --depth=1 https://github.com/FloatTech/ZeroBot-Plugin.git
cd ZeroBot-Plugin
go version
go env -w GOPROXY=https://goproxy.cn,direct
go env -w GO111MODULE=auto
go mod tidy
```
3. 编辑`main.go`，按注释指示添加机器人主人qq/修改机器人名字。
4. 在`main.go`所在文件夹下进行编译。以下为编译指令示例：
```bash
# 本机平台
go build -ldflags "-s -w" -o zerobot -trimpath
# x64 Linux 平台 如各种云服务器
GOOS=linux GOARCH=amd64 go build -ldflags "-s -w" -o zerobot -trimpath
# x64 Windows 平台 如大多数家用电脑
GOOS=windows GOARCH=amd64 go build -ldflags "-s -w" -o zerobot.exe -trimpath
# armv6 Linux 平台 如树莓派 zero W
GOOS=linux GOARCH=arm GOARM=6 CGO_ENABLED=0 go build -ldflags "-s -w" -o zerobot -trimpath
# （由于引入了github.com/fumiama/sqlite3，本项不再可用）mips Linux 平台 如 路由器 wndr4300
GOOS=linux GOARCH=mips GOMIPS=softfloat CGO_ENABLED=0 go build -ldflags "-s -w" -o zerobot -trimpath
```
5. 运行你编译出来的名为`zerobot`或`zerobot.exe`的文件。

> 至此，zbp 安装完毕。`连接QQ的东西`和`ZeroBot-Plugin本体`同时运行就可以使用机器人啦~