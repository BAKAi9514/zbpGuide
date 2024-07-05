# 功能列表
> 在编译时，以下功能除插件控制外，均可通过注释`main.go`中的相应`import`而物理禁用，减小插件体积。

> 通过插件控制，还可动态管理某个功能在某个群的打开/关闭。

> 插件的优先级为`import`的先后顺序。

> `webui`默认禁用不编译，打开后会增加程序体积。

 
### 插件控制 

- [x] /响应 (在发送的群/用户开始工作)

- [x] /沉默 (在发送的群/用户停止工作)

- [x] /全局响应 (在所有位置开始工作，无视单独的沉默)

- [x] /全局沉默 (在所有本应沉默的位置停止工作，显式指定启用的位置不受影响)

- [x] /启用 xxx (在发送的群/用户启用xxx)

- [x] /禁用 xxx (在发送的群/用户禁用xxx)

- [x] /此处启用所有插件

- [x] /此处禁用所有插件

- [x] /全局启用 xxx

- [x] /全局禁用 xxx

- [x] /还原 xxx (在发送的群/用户还原xxx的开启状态到初始状态)

  - 注：当全局未配置或与默认相同时，状态取决于单独配置，后备为默认配置；当全局与默认不同时，状态取决于全局配置，单独配置失效。

- [x] /改变默认启用状态 xxx

- [x] /禁止 service qq1 qq2... (禁止 qqs 使用服务 service)

- [x] /允许 service qq1 qq2... (重新允许 qqs 使用服务 service)

- [x] /封禁 qq1 qq2... (禁止 qqs 使用全部服务)

- [x] /解封 qq1 qq2... (允许 qqs 使用全部服务)

- [x] /用法 xxx

- [x] /服务列表

- [x] /设置服务列表显示行数 xx (默认值为 9, 该设置仅运行时有效, zbp 重启后重置)

- [x] (默认禁用) /设置webui用户名 zerobot 密码 123456

- [x] (默认禁用) /webui启动

- [x] (默认禁用) /webui停止

- [x] @Bot 插件冲突检测 (会在本群发送一条消息并在约 1s 后撤回以检测其它同类 bot 中已启用的插件并禁用)

 
 
### 动态加载插件 

  `import _ "github.com/FloatTech/ZeroBot-Plugin-Dynamic/dyloader"`

  - 本功能需要`cgo`，故已分离出主线。详见[ZeroBot-Plugin-Dynamic](https://github.com/FloatTech/ZeroBot-Plugin-Dynamic)

 

## *高优先级*
 
### 聊天 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/chat"`

- [x] [BOT名字]

- [x] [戳一戳BOT]

- [x] 空调开

- [x] 空调关

- [x] 群温度

- [x] 设置温度[正整数]

 
 
### 聊天时长统计 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/chatcount"`

- [x] 查询水群@xxx

- [x] 查看水群排名

 
 
### 睡眠管理 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/sleep_manage"`

- [x] 早安 | 晚安

 
 
### ATRI 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/atri"
  `
- [x] 具体指令看 /用法 atri

  - 注：本插件基于 [ATRI](https://github.com/Kyomotoi/ATRI) ，为 Golang 移植版

 
 
### 群管 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/manager"`

- [x] 禁言[@xxx][分钟]

- [x] 解除禁言[@xxx]

- [x] 我要自闭 | 禅定 x [分钟 | 小时 | 天]

- [x] 开启全员禁言

- [x] 解除全员禁言

- [x] 升为管理[@xxx]

- [x] 取消管理[@xxx]

- [x] 修改名片[@xxx][xxx]

- [x] 修改头衔[@xxx][xxx]

- [x] 申请头衔[xxx]

- [x] 踢出群聊[@xxx]

- [x] 退出群聊[群号]@Bot

- [x] \*入群欢迎

- [x] \*退群通知

- [x] 设置欢迎语[欢迎~]  可选添加 [{at}] [{nickname}] [{avatar}] [{id}]

- [x] 在[MM]月[dd]日的[hh]点[mm]分时(用[url])提醒大家[xxx]

- [x] 在[MM]月[每周 | 周几]的[hh]点[mm]分时(用[url])提醒大家[xxx]

- [x] 取消在[MM]月[dd]日的[hh]点[mm]分的提醒

- [x] 取消在[MM]月[每周 | 周几]的[hh]点[mm]分的提醒

- [x] 在"cron"时(用[url])提醒大家[xxx]

- [x] 取消在"cron"的提醒

- [x] 列出所有提醒

- [x] 翻牌
  
- [x] 赞我

- [x] [开启 | 关闭]入群验证

- [x] [开启 | 关闭]gist加群自动审批

- [x] 对信息回复:[设置 | 取消]精华

- [x] 取消精华 [信息ID]

- [x] /精华列表

  - [ ] 同意好友请求

- [x] 对信息回复: 撤回

  - [ ] 警告[@xxx]

  - 注：使用gist加群自动审批，请在群介绍添加以下说明，同时开启`需要回答问题并由管理员审核`：加群请在github新建一个gist，其文件名为本群群号的字符串的md5(小写)，内容为一行，是当前unix时间戳(10分钟内有效)。然后请将您的用户名和gist哈希(小写)按照username/gisthash的格式填写到回答即可。

  - 设置欢迎语可选添加参数说明：{at}可在发送时艾特被欢迎者 {nickname}是被欢迎者名字 {avatar}是被欢迎者头像 {uid}是被欢迎者QQ号 {gid}是当前群群号 {groupname} 是当前群群名

 
 
### 定时指令触发器 

  `import _ "github.com/FloatTech/zbputils/job"`

  - 注意：触发器具有限速，每 2s 仅允许最多一次触发

- [x] 记录以"完全匹配关键词"触发的(代表我执行的)指令

- [x] 取消以"完全匹配关键词"触发的(代表我执行的)指令

- [x] 记录在"cron"触发的(别名xxx的)指令

- [x] 取消在"cron"触发的指令

- [x] 查看所有触发指令

- [x] 查看在"cron"触发的指令

- [x] 查看以"完全匹配关键词"触发的(代表我执行的)指令

- [x] 注入指令结果：任意指令

- [x] 执行指令：任意指令

  - 注：任意指令可以使用形如`?::参数1提示语::1!`,`?::参数2提示语::2!`,`?::?可选参数3提示语，不回答将填入空值::3!`,`!::从url获取的参数::4!`,`!::?可选的从url获取的参数，出错将填入空值::5!`的未定参数，在注入时一一匹配

  - 一些示例

> 每日9:30推送摸鱼人日历

```
记录在"30 9 * * *"触发的指令
run[CQ:image,file=https://api.vvhan.com/api/moyu]
```

> 每日12:00以1/2概率执行coser指令

```python
记录在"0 12 * * *"触发的指令
注入指令结果：>runcoderaw py
from random import random
if random() > 0.5: print('coser')
else: print('今天没有coser哦~')
```

> 每日15:00询问设置定时者否想看coser

```python
记录在"0 15 * * *"触发的指令
注入指令结果：>runcoderaw py
if '?::想看coser吗？::1!' == '想': print('coser')
else: print('好吧')
```

> 自行编写简易的选择困难症助手小插件

```python
记录以"简易的选择困难症助手"触发的指令
执行指令：>runcoderaw py
from random import random
if random() > 0.5: print('您最终会选?::请输入您的选择1::1!')
else: print('您最终会选?::请输入您的选择2::2!')
简易的选择困难症助手
```

> 自行编写随机b站404页趣图插件

```python
记录以"随机b站404页趣图"触发的代表我执行的指令
注入指令结果：>runcoderaw py
import json
j = json.loads(r'''!::https://api.iyk0.com/bili_chart::1!''')
print("run[CQ:image,file="+j["img"]+"]")
随机b站404页趣图
```

![随机b站404页趣图](https://user-images.githubusercontent.com/41315874/157371451-c09ad3bb-c61a-4a42-9c47-fab3305bc0f8.png)

- [x] [我|大家|有人][说|问][正则表达式]你[答|说|做|执行][模版]

- [x] [查看|看看][我|大家|有人][说|问][正则表达式]

- [x] 删除[大家|有人|我][说|问|让你做|让你执行][正则表达式]

  - 注：模版是指含有`$1` `$2`这样的未定参数，会在正则匹配时按顺序填入子匹配对应值

 

## *中优先级*
 
### ahsai tts 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/ahsai"`

- [x] 使[ 伊織弓鶴 | 紲星あかり | 結月ゆかり | 京町セイカ |東北きりたん | 東北イタコ | ついなちゃん標準語 | ついなちゃん関西弁 | 音街ウナ | 琴葉茜 | 吉田くん | 民安ともえ | 桜乃そら | 月読アイ | 琴葉葵 | 東北ずん子 | 月読ショウタ | 水奈瀬コウ ]说(日语)

 
 
### AIfalse 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/ai_false"`

- [x] 查询计算机当前活跃度: [检查身体 | 自检 | 启动自检 | 系统状态]

- [x] 设置默认限速为每 m [分钟 | 秒] n 次触发

 
 
### AIWife 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/aiwife"`

- [x] waifu | 随机waifu(从[100000个AI生成的waifu](https://www.thiswaifudoesnotexist.net/)中随机一位)

 
 
### 支付宝到账语音 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/alipayvoice"`

- [x] 支付宝到账 1

 
 
### 触发者撤回时也自动撤回 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/autowithdraw"`

- [x] 撤回一条消息

 
 
### base16384加解密 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/b14"`

- [x] 加密xxx

- [x] 解密xxx

- [x] 用yyy加密xxx

- [x] 用yyy解密xxx

 
 
### 百度内容审核 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/baiduaudit"`

- [x] 获取BDAkey

- [x] 配置BDAKey [API Key] [Secret Key]

- [x] 获取BDAkey

- [x] [开启|关闭]内容审核

- [x] [开启|关闭]撤回提示

- [x] [开启|关闭]详细提示

- [x] [开启|关闭]撤回禁言

- [x] [开启|关闭]禁言累加

- [x] [开启|关闭]文本检测

- [x] [开启|关闭]图像检测

- [x] 设置最大禁言时间[分钟，默认:60,最大43200]

- [x] 设置每次累加时间[分钟，默认:1]

- [x] 设置撤回禁言时间[分钟，默认:1]

- [x] 查看检测类型

- [x] 查看检测配置

- [x] 测试文本检测[文本内容]

- [x] 测试图像检测[图片]

- [x] 设置检测类型[类型编号]

- [x] 设置不检测类型[类型编号]

    检测类型编号列表:[1:违禁违规|2:文本色情|3:敏感信息|4:恶意推广|5:低俗辱骂|6:恶意推广-联系方式|7:恶意推广-软文推广]
 
 
### base64卦加解密 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/base64gua"`

- [x] 六十四卦加密xxx

- [x] 六十四卦解密xxx

- [x] 六十四卦用yyy加密xxx

- [x] 六十四卦用yyy解密xxx

 
 
### base天城文加解密 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/baseamasiro"`

- [x] 天城文加密xxx

- [x] 天城文解密xxx

- [x] 天城文用yyy加密xxx

- [x] 天城文用yyy解密xxx

 
 
### bilibili 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/bilibili"`

- [x] >vup info [xxx]

- [x] >user info [xxx]

- [x] 查成分 [xxx]

- [x] 查弹幕 [xxx] 2 (最后一个参数是页码)

- [x] 设置b站cookie b_ut=7;buvid3=0;i-wanna-go-back=-1;innersign=0; (最好把cookie设全)

    获取Cookie可以使用[这个工具](https://github.com/XiaoMiku01/login_bili_go)
    
- [x] 更新vup

 
 
### b站动态、专栏、视频、直播解析 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/bilibili"`

- [x] t.bilibili.com/642277677329285174 | bilibili.com/read/cv17134450 | bilibili.com/video/BV13B4y1x7pS | live.bilibili.com/22603245

 
 
### b站动态、直播推送,需要配合job一起使用 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/bilibili"`

- [x] 添加b站订阅[uid|name]

- [x] 取消b站订阅[uid|name]
  
- [x] 取消b站动态订阅[uid|name]
  
- [x] 取消b站直播订阅[uid|name]
  
- [x] b站推送列表
  
- [x] 拉取b站推送 (使用job执行定时任务------记录在"@every 5m"触发的指令) 

 
 
### 书评 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/book_review"`

- [x] 书评[xxx]

- [x] 随机书评

 
 
### 选择困难症帮手 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/choose"`

- [x] 选择[选择项1]还是[选项2]还是[更多选项]

 
 
### 抽象话 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/chouxianghua"`

- [x] 抽象翻译[xxx]

 
 
### 英文字符翻转 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/chrev"`

- [x] 翻转 I love you

 
 
### coser 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/coser" `

- [x] coser

 
 
### cp短打 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/cpstory"`

- [x] 组cp[@xxx][@xxx]

- [x] 磕cp大老师 雪乃

 
 
### 今日早报 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/dailynews"`

- [x] 今日早报

 
 
### DeepDanbooru二次元图标签识别 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/danbooru"`

- [x] 鉴赏图片[图片]

 
 
### 嘉然 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/diana"`

- [x] 小作文

- [x] 发大病

- [x] 教你一篇小作文[作文]

 
 
### 程序员做饭指南 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/dish"`

- [x] 怎么做 | 烹饪[菜名]

- [x] 随机菜谱 | 随便做点菜

 
 
### 多功能抽签 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/drawlots"`

  支持图包文件夹和gif抽签

- [x] (刷新)抽签列表
  
- [x] 抽[签名]签
  
- [x] 看签[gif签名]
	
- [x] 加签[签名][gif图片]
	
- [x] 删签[gif签名]

 
 
### 漂流瓶 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/drift_bottle"`

- [x] @Bot pick (随机捞一个漂流瓶)

- [x] @Bot throw xxx (投递内容xxx,支持图片文字,投递内容需要大于10个字符或者带有图片)

 
 
### 合成emoji 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/emojimix"`

- [x] [emoji][emoji]

 
 
### 好友申请及群聊邀请事件处理 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/event"`

- [x] [开启|关闭]自动同意[申请|邀请|主人]

- [x] [同意|拒绝][申请|邀请][flag]

  - flag跟随事件一起发送, 默认同意主人的事件

 
 
### 渲染任意文字到图片 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/font"`

- [x] (用[终末体|终末变体|紫罗兰体|樱酥体|Consolas体|粗苹方体|未来荧黑体|Gugi体|八丸体|Impact体|猫啃体|苹方体])渲染(抖动)文字xxx

 
 
### 每日运势 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/fortune"`

- [x] 运势 | 抽签

- [x] 设置底图[车万 DC4 爱因斯坦 星空列车 樱云之恋 富婆妹 李清歌 公主连结 原神 明日方舟 碧蓝航线 碧蓝幻想 战双 阴阳师 赛马娘 东方归言录 奇异恩典 夏日口袋 ASoul Hololive]

 
 
### 笑话 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/funny"`

- [x] 讲个笑话[@xxx|qq号|人名] | 夸夸[@xxx|qq号|人名]

 
 
### 原神抽卡 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/genshin"`

- [x] 切换原神卡池

- [x] 原神十连

 
 
### gif 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/gif"`

- [x] 爬[@xxx]

- [x] 摸[@xxx]

- [x] 搓[@xxx]

  - 注：更多指令见项目 --> https://github.com/FloatTech/ZeroBot-Plugin-Gif

 
 
### GitHub仓库搜索 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/github"`

- [x] >github [xxx]

- [x] >github -p [xxx]

 
 
### 猜歌 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/guessmusic"`

  猜歌插件（该插件依赖ffmpeg）
	
  ---------主 人 指 令---------
- [x] 设置猜歌歌库路径 [绝对路径]
- [x] [创建/删除]歌单 [歌单名称]
- [x] 下载歌曲[歌曲名称/网易云歌曲ID]到[歌单名称]
	
  -------管 理 员 指 令--------
- [x] 设置猜歌默认歌单 [歌单名称]
- [x] 上传歌曲[群文件的音乐名]到[歌单名称]
	
  ------公 用 指 令------
- [x] 歌单列表
- [x] [个人/团队]猜歌
	
  ------插 件 扩 展------
	
  - 本插件内置了[NeteaseCloudMusicApi](https://binaryify.github.io/NeteaseCloudMusicApi/#/)框架的一些功能
- [x] 设置猜歌API帮助
- [x] 设置猜歌API [API首页网址]
- [x] 猜歌[开启/关闭][歌单/歌词]自动下载
  - [ ] 登录网易云
- [x] 歌单信息 [网易云歌单链接/ID]
- [x] [歌单名称]绑定网易云[网易云歌单链接/ID]
- [x] 下载歌单[网易云歌单链接/ID]到[歌单名称]
- [x] 解除绑定 [歌单名称]

 
 
### 一言 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/hitokoto"`

- [x] 一言[xxx]
  
- [x] 系列一言

 
 
### 炉石 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/hs"`

- [x] 搜卡[xxxx]

- [x] [卡组代码xxx]

  - 注：更多搜卡指令参数：https://hs.fbigame.com/misc/searchhelp

 
 
### 百人一首 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/hyaku"`

- [x] 百人一首

- [x] 百人一首之n

 
 
### 注入指令 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/inject"`

- [x] run[CQ码]

 
 
### 煎蛋网无聊图 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/jandan"`

- [x] 来份[屌|弔|吊]图

- [x] 更新[屌|弔|吊]图

 
 
### 日语听力学习材料 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/jptingroom"`

- [x] 随机日语听力
  
- [x] 随机日语歌曲
  
- [x] 日语听力 xxx
  
- [x] 日语歌曲 xxx

 
 
### 疯狂星期四 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/kfccrazythursday"`

- [x] 疯狂星期四

 
 
### kokomi原神面板 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/kokomi"`

- [x] kokomi菜单

- [x] XX面板

  - 注:本插件未并入主仓库,需自行安装(须源码方式运行才能添加插件),安装地址[kokomi-原神面板查询插件](https://github.com/lianhong2758/kokomi-plugin) 

 
 
### lolicon 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/lolicon"`

- [x] 随机图片

- [x] 随机图片 萝莉|少女

- [x] 设置随机图片地址[http...]

  - 每一小时发一张图
```
记录在"@every 1h"触发的指令
来份萝莉
```

 
 
### 桑帛云 API 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/lolimi"`

- [x] 随机妹子

- [x] 随机绕口令

- [x] 颜值鉴定[图片]
  
- [x] 随机情话

- [x] 发病 嘉然

- [x] 让[嘉然|塔菲|东雪莲|懒羊羊|科比|孙笑川|陈泽|丁真|空|荧|派蒙|纳西妲|阿贝多|温迪|枫原万叶|钟离|荒泷一斗|八重神子|艾尔海森|提纳里|迪希雅|卡维|宵宫|莱依拉|赛诺|诺艾尔|托马|凝光|莫娜|北斗|神里绫华|雷电将军|芭芭拉|鹿野院平藏|五郎|迪奥娜|凯亚|安柏|班尼特|琴|柯莱|夜兰|妮露|辛焱|珐露珊|魈|香菱|达达利亚|砂糖|早柚|云堇|刻晴|丽莎|迪卢克|烟绯|重云|珊瑚宫心海|胡桃|可莉|流浪者|久岐忍|神里绫人|甘雨|戴因斯雷布|优菈|菲谢尔|行秋|白术|九条裟罗|雷泽|申鹤|迪娜泽黛|凯瑟琳|多莉|坎蒂丝|萍姥姥|罗莎莉亚|留云借风真君|绮良良|瑶瑶|七七|奥兹|米卡|夏洛蒂|埃洛伊|博士|女士|大慈树王|三月七|娜塔莎|希露瓦|虎克|克拉拉|丹恒|希儿|布洛妮娅|瓦尔特|杰帕德|佩拉|姬子|艾丝妲|白露|星|穹|桑博|伦纳德|停云|罗刹|卡芙卡|彦卿|史瓦罗|螺丝咕姆|阿兰|银狼|素裳|丹枢|黑塔|景元|帕姆|可可利亚|半夏|符玄|公输师傅|奥列格|青雀|大毫|青镞|费斯曼|绿芙蓉|镜流|信使|丽塔|失落迷迭|缭乱星棘|伊甸|伏特加女孩|狂热蓝调|莉莉娅|萝莎莉娅|八重樱|八重霞|卡莲|第六夜想曲|卡萝尔|姬子|极地战刃|布洛妮娅|次生银翼|理之律者|真理之律者|迷城骇兔|希儿|魇夜星渊|黑希儿|帕朵菲莉丝|天元骑英|幽兰黛尔|德丽莎|月下初拥|朔夜观星|暮光骑士|明日香|李素裳|格蕾修|梅比乌斯|渡鸦|人之律者|爱莉希雅|爱衣|天穹游侠|琪亚娜|空之律者|终焉之律者|薪炎之律者|云墨丹心|符华|识之律者|维尔薇|始源之律者|芽衣|雷之律者|苏莎娜|阿波尼亚|陆景和|莫弈|夏彦|左然]说我测尼玛

 
 
### MagicPrompt-Stable-Diffusion吟唱提示 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/magicprompt"`

- [x] 吟唱提示[xxxx]

 
 
### 钓鱼模拟器 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/mcfish"`

- [x] 钓鱼商店
- [x] 购买xxx [数量]
- [x] 出售[xxx [数量]|所有垃圾]
- [x] 钓鱼背包
- [x] 装备[xx竿|三叉戟|美西螈]
- [x] 附魔[诱钓|海之眷顾]
- [x] 修复鱼竿
- [x] 合成[xx竿|三叉戟]
- [x] 进行钓鱼
- [x] 进行n次钓鱼

 
 
### 简易midi音乐制作 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/midicreate"`

- [x] midi制作 CCGGAAGR FFEEDDCR GGFFEEDR GGFFEEDR CCGGAAGR FFEEDDCR

- [x] 个人听音练习
  
- [x] 团队听音练习
  
- [x] *.mid (midi 转 txt)
  
- [x] midi制作*.txt (txt 转 midi)
  
- [x] 设置音色40 (0~127)

- [x] 注: 该插件需要安装timidity, linux安装脚本可参考 https://gitcode.net/anto_july/midi/-/raw/master/timidity.sh, windows安装脚本可参考 https://gitcode.net/anto_july/midi/-/raw/master/timidity.bat?inline=false, windows需要管理员模式运行
  
- [x] 符号说明: C5是中央C,后面不写数字,默认接5,Cb6<1,b代表降调,#代表升调,6比5高八度,<1代表音长×2,<3代表音长×8,<-1代表音长×0.5,<-3代表音长×0.125,R是休止符

 
 
### 日韩 VITS 模型拟声 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/moegoe"`

- [x] 让[派蒙|空|荧|阿贝多|枫原万叶|温迪|八重神子|纳西妲|钟离|诺艾尔|凝光|托马|北斗|莫娜|荒泷一斗|提纳里|芭芭拉|艾尔海森|雷电将军|赛诺|琴|班尼特|五郎|神里绫华|迪希雅|夜兰|辛焱|安柏|宵宫|云堇|妮露|烟绯|鹿野院平藏|凯亚|达达利亚|迪卢克|可莉|早柚|香菱|重云|刻晴|久岐忍|珊瑚宫心海|迪奥娜|戴因斯雷布|魈|神里绫人|丽莎|优菈|凯瑟琳|雷泽|菲谢尔|九条裟罗|甘雨|行秋|胡桃|迪娜泽黛|柯莱|申鹤|砂糖|萍姥姥|奥兹|罗莎莉亚|式大将|哲平|坎蒂丝|托克|留云借风真君|昆钧|塞琉斯|多莉|大肉丸|莱依拉|散兵|拉赫曼|杜拉夫|阿守|玛乔丽|纳比尔|海芭夏|九条镰治|阿娜耶|阿晃|阿扎尔|七七|博士|白术|埃洛伊|大慈树王|女士|丽塔|失落迷迭|缭乱星棘|伊甸|伏特加女孩|狂热蓝调|莉莉娅|萝莎莉娅|八重樱|八重霞|卡莲|第六夜想曲|卡萝尔|姬子|极地战刃|布洛妮娅|次生银翼|理之律者|迷城骇兔|希儿|魇夜星渊|黑希儿|帕朵菲莉丝|天元骑英|幽兰黛尔|德丽莎|月下初拥|朔夜观星|暮光骑士|明日香|李素裳|格蕾修|梅比乌斯|渡鸦|人之律者|爱莉希雅|爱衣|天穹游侠|琪亚娜|空之律者|薪炎之律者|云墨丹心|符华|识之律者|维尔薇|芽衣|雷之律者|阿波尼亚]说(中文)

 
 
### 摸鱼 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/moyu"`

- [x] /启用 moyu

- [x] /禁用 moyu

```
记录在"0 10 * * *"触发的指令
摸鱼提醒
```

 
 
### 摸鱼人日历 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/moyu_calendar"`

- [x] /启用 moyucalendar

- [x] /禁用 moyucalendar

```
记录在"30 8 * * *"触发的指令
摸鱼人日历
```

 
 
### 点歌 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/music"`

- [x] 点歌[xxx]

- [x] 网易点歌[xxx]

- [x] 酷我点歌[xxx]

- [x] 酷狗点歌[xxx]

 
 
### 本地涩图 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/nativesetu"`

- [x] 本地[xxx]

- [x] 刷新本地[xxx]

- [x] 设置本地setu绝对路径[xxx]

- [x] 刷新所有本地setu

- [x] 所有本地setu分类

  - 注：刷新文件夹较慢，请耐心等待刷新完成，会提示“成功”。

 
 
### 抽wife 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/nativewife"`

- [x] 抽wife[@xxx]

- [x] 添加wife[名字][图片]

- [x] 删除wife[名字]

- [x] [让 | 不让]所有人均可添加wife

  - 注：不同群添加后不会重叠

 
 
### 拼音首字母释义工具 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/nbnhhsh"`

- [x] ?? [缩写]

 
 
### 日语语法学习 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/nihongo"`

- [x] 日语语法 [xxx] (使用tag随机)
  
- [x] 搜索日语语法 [xxx]

 
 
### 小说 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/novel" `

- [x] 小说[xxx]

  - 设置小说配置 zerobot 123456

  - 下载小说30298

  - 注: 建议去https://www.23qb.com/ 注册一个账号, 小说下载有积分限制

 
 
### nsfw图片识别 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/nsfw"`

- [x] nsfw打分[图片]

- [x] 当图片属于非 neutral 类别时自动发送评价(默认禁用，启用输入 /启用 nsfwauto)

 
 
### 浅草寺求签 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/omikuji"`

- [x] 求签 | 占卜

- [x] 解签

 
 
### 抽扑克 
  
  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/poker"`

- [x] 抽扑克牌

 
 
### 一群一天一夫一妻制群老婆 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/qqwife"`

  - 引入好感度系统，好感度越高，自由恋爱成功率越高
  
- [x] 设置CD为xx小时

- [x] [允许|禁止]自由恋爱

- [x] [允许|禁止]牛头人

- [x] 娶群友

- [x] [娶|嫁][@对方QQ]
  
- [x] 当[对方Q号|@对方QQ]的小三

- [x] 做媒 @攻方QQ @受方QQ
  
- [x] 买礼物给[对方Q号|@对方QQ]

- [x] 群老婆列表

- [x] 查好感度[对方Q号|@对方QQ]

- [x] 好感度列表

- [x] 重置花名册

 
 
### qq空间表白墙 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/qzone"`

- [x] 登录QQ空间 (Cookie过期很快, 要经常登录)
  
- [x] 发说说[xxx]
  
- [x] (匿名)发表白墙[xxx]
  
- [x] [ 同意 | 拒绝 ]表白墙 1,2,3 (最后一个参数是表白墙的序号数组, 用英文逗号连接)
  
- [x] 查看[ 等待 | 同意 | 拒绝 | 所有 ]表白墙 0 (最后一个参数是页码, 建议私聊审稿)

 
 
### Real-CUGAN清晰术 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/realcugan"`

- [x] 清晰术(双重吟唱|三重吟唱|四重吟唱)(强力术式|中等术式|弱术式|不变式|原式)[图片]

 
 
### 投胎 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/reborn"`

- [x] reborn

  - 注：本插件来源于[tgbot](https://github.com/YukariChiba/tgbot/blob/main/modules/Reborn.py)

 
 
### 打劫 

`import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/robbery"`

- [x] 打劫[对方Q号|@对方QQ]

 
 
### 在线代码运行 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/runcode"`

- [x] >runcode [language] help

- [x] >runcode [language] [code block]

- [x] >runcoderaw [language] [code block]

 
 
### 搜图 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/saucenao"`

- [x] 以图搜图 | 搜索图片 | 以图识图[图片]

- [x] 搜图[P站图片ID]

- [x] 设置 saucenao api key [apikey]

 
 
### 签到得分 

`import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/score"` 

- [x] 签到
- [x] 获得签到背景[@xxx] | 获得签到背景
- [x] 设置签到预设(0~3)
- [x] 查看等级排名
  - 注:跨群排行
- [x] 查看我的钱包
- [x] 查看钱包排名
  - 注:本群排行，若群人数太多不建议使用该功能!!!

 
 
### 沙雕app 

`import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/shadiao"`

- [x] 哄我
- [x] 渣我
- [x] 来碗绿茶
- [x] 发个朋友圈
- [x] 来碗毒鸡汤
- [x] 讲个段子
- [x] 马丁路德骂我

 
 
### shindan 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/shindan"`

- [x] 今天是什么少女[@xxx]

- [x] 异世界转生[@xxx]

- [x] 卖萌[@xxx]

- [x] 今日老婆[@xxx]

- [x] 黄油角色[@xxx]

 
 
### steam 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/steam"`

- [x] steam[添加|删除]订阅xxxxx

- [x] steam查询订阅

- [x] steam绑定 api key xxxxxxx

- [x] 查看apikey

- [x] 拉取steam订阅 (使用job执行定时任务------记录在"@every 1m"触发的指令) 

 
 
### 抽塔罗牌 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/tarot"`

- [x] 抽[塔罗牌|大阿卡纳|小阿卡纳]
- [x] 抽n张[塔罗牌|大阿卡纳|小阿卡纳]
- [x] 解塔罗牌[牌名]
- [x] [塔罗|大阿卡纳|小阿卡纳|混合]牌阵[圣三角|时间之流|四要素|五牌阵|吉普赛十字|马蹄|六芒星]

 
 
### 舔狗日记 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/tiangou"`

- [x] 舔狗日记

 
 
### 搜番 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/tracemoe"`

- [x] 搜番 | 搜索番剧[图片]

 
 
### 翻译 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/translation"`

- [x] >TL 你好

 
 
### vits猫雷 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/vitsnyaru"`

- [x] 让猫雷说[xxxx]

 
 
### vtb语录 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/vtb_quotation"`

- [x] vtb语录

- [x] 随机vtb

- [x] 更新vtb

 
 
### 钱包 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/wallet"`

- [x] 查看我的钱包

- [x] 查看钱包排名

 
 
### 据意查句 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/wantquotes"`

- [x] 据意查句 大海
  
- [x] 登录据意查句 

 
 
### 星际战甲 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/warframeapi"`

- [x] wf时间同步
  
- [x] [金星|地球|火卫二]平原状态
  
- [x] .wm [物品名称]
  
- [x] 仲裁
  
- [x] 警报
  
- [x] 每日特惠
 
 
### 百度文心AI 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/wenxinAI"`

  基于百度文心API的一些功能

  key申请链接：https://wenxin.baidu.com/moduleApi/key
  
- [x] 为[自己/本群/QQ号/群+群号]设置文心key [API Key] [Secret Key]
  
- [x] 为[自己/本群/QQ号/群+群号]设置画图key [API Key] [Secret Key]
  
  例：“为10086设置画图key 123 456”；“为群10010设置画图key 789 101”
  
  文心key和画图key的API key 可以是相同的，只是文心key日限为200，画图日限为50，以此作区别。
  
- [x] 文心作文 (x字的)[作文题目]
  
- [x] 文心提案 (x字的)[文案标题]
  
- [x] 文心摘要 (x字的)[文章内容]
  
- [x] 文心小说 (x字的)[小说上文]
  
- [x] 文心对联 [上联]
  
- [x] 文心问答 [问题]
	
- [x] 文心补全 [带“_”的填空题]
  
- [x] 文心自定义 [prompt]

- [x] [bot名称]画几张[图片描述]的[图片类型][图片尺寸]

  指令示例：

  - 文心作文 我的椛椛机器人

  - 文心作文 300字的我的椛椛机器人

  - 椛椛帮我画几张金凤凰，背景绚烂，高饱和，古风，仙境，高清，4K，古风的油画方图

 
 
### 抽老婆 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/wife"`

- [x] 抽老婆

 
 
### 聊天热词 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/word_count"`

- [x] 热词 [群号] [消息数目]|热词 123456 1000

 
 
### 猜单词 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/wordle"`

- [x] 个人猜单词

- [x] 团队猜单词

- [x] 团队六阶猜单词

- [x] 团队七阶猜单词

 
 
### 鬼东西 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/wtf"`

- [x] 鬼东西列表

- [x] 查询鬼东西[序号][@xxx]

  - 注：由于需要科学，默认注释。

 
 
### 一些游戏王插件 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/ygo"`
  
##### 白鸽API卡查
	    
###### `"github.com/FloatTech/ZeroBot-Plugin/plugin/ygo/ygocdb.go"`
- [x] /ydp [xxx]
- [x] /yds [xxx]
- [x] /ydb [xxx]
  - 注：[xxx]为搜索内容;p:返回一张图片;s:返回一张效果描述;b:高级搜索
	
##### 集换社卡价查询

###### `"github.com/FloatTech/ZeroBot-Plugin/plugin/ygo/ygotrade.go"`
- [x] 查卡价 [卡名]
- [x] 查卡价 [卡名] -r [稀有度 稀有度 ...]
- [x] 查卡店  [卡名]
- [x] 查卡店  [卡名] -r [稀有度]
  - 注：卡店只支持单个稀有度查询
	
 
 
### 月幕galgame图 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/ymgal"`

- [x] 随机galCG

- [x] 随机gal表情包

- [x] galCG[xxx]

- [x] gal表情包[xxx]

- [x] 更新gal

 
 
### 遇见API 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/yujn"`
  
- [x] 小姐姐视频
- [x] 小姐姐视频2
- [x] 黑丝视频
- [x] 白丝视频
- [x] 欲梦视频
- [x] 甜妹视频
- [x] 双倍快乐
- [x] 纯情女高
- [x] 萝莉视频
- [x] 玉足视频
- [x] 帅哥视频
- [x] 热舞视频
- [x] 吊带视频
- [x] 汉服视频
- [x] 极品狱卒
- [x] 清纯视频
- [x] 快手变装
- [x] 抖音变装
- [x] 萌娃视频
- [x] 穿搭视频
- [x] 完美身材
- [x] 御姐撒娇
- [x] 绿茶语音
- [x] 怼人语音
- [x] 随机骚话
- [x] 随机污句子
- [x] 随机美句
- [x] 土味情话   
- [x] 让[lulu]说我测尼玛

 

## *低优先级*

 
### 骂人 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/curse"`

- [x] 骂我

- [x] 大力骂我

 
 
### 人工智能回复 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/aireply"`

- [x] @Bot 任意文本(任意一句话回复)

- [x] 设置文字回复模式[婧枫|沫沫|青云客|小爱|ChatGPT]

- [x] 设置 ChatGPT api key xxx

 
 
### 词典匹配回复 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/thesaurus"`

- [x] 切换[kimo|傲娇|可爱]词库
- [x] 设置词库触发概率0.x (0<x<9)

 
 
### 打断复读 

  `import _ "github.com/FloatTech/ZeroBot-Plugin/plugin/breakrepeat"`

- [x] (打断三次以上的复读)