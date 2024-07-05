# 基于 FloatTech 的 zbp 进行二次创作！

现在你已经拥有一个可供你自定义的机器人了。

想想这个机器人的设定吧~这个过程还是很有意思的。无论是捏他已有的冻鳗角色也好、原创一个新的角色也罢。总之，让这个机器人有一个简单的形象吧！

本篇文章并不会辅助你如何去规划你的机器人形象，因为本篇文章要讲的是*通过简单修改 zbp 插件中的数据*进行的入门级自定义！

如果刚才你已经对这个没有进行过多少修改的机器人进行测试了的话，我相信你会发现机器人的台词还是挺多的。

所有东西都和别人一模一样的话就太无趣了，所以让我们对机器人的台词进行修改吧~

## 台词修改

### 以 chat 为例

根据`ctx.SendChain`来寻找机器人的台词，例如…

```go
func init() { // 插件主体
// 被喊名字
engine.OnFullMatch("", zero.OnlyToMe).SetBlock(true).
Handle(func(ctx *zero.Ctx) {
var nickname = zero.BotConfig.NickName[0]
time.Sleep(time.Second * 1)
ctx.SendChain(message.Text(
    []string{
        nickname + "在此，有何贵干~",
	"(っ●ω●)っ在~",
	"这里是" + nickname + "(っ●ω●)っ",
	nickname + "不在呢~",
    }[rand.Intn(4)],
    ))
})
// 戳一戳
```

如上，从`engine.OnFullMatch`到与其相闭合的括号结束，这是一套回复。在其他插件里，这个构造也是一样的，只不过`engine.`后面的内容会随着所需匹配回复的规则而改变。

看到`ctx.SendChain`了吗？后面跟着的就是机器人对于此内容的回复。你可以在此处进行修改。要注意的是，这里选择了切片来存储一组机器人的回复。机器人被触发这个功能时，会从这一组回复中随机抽取一句发送。**一组回复中不同的回复要用**`,`**分隔，即使到该切片最后一句，后面也要加上**`,`。

此处本插件还声明了一个变量。
```go
var nickname = zero.BotConfig.NickName[0]
```
由此，你可以简单地在回复中使用`nickname`来使用你设置的机器人昵称。

在撰写其他插件时，你也可以通过定义这条变量来使用你设置的机器人昵称。~~不直接写死的好处就是当你的插件给别人用时别人可以直接套用而不是再改内含的机器人昵称。~~

### thesaurus ——词典插件

这是一个特殊的插件。你可以通过修改它运行时导入的`kimoi.json`/`simai.yml`来修改机器人的台词。如果你已经启动一次机器人并已经开启该插件，你可以从 zbp 运行目录中的`data/Chat/`找到它。

**注意，在这个插件中，只有先 at 机器人再加上关键词机器人才能进行回复！**当然你也可以删掉规则中的`zero.OnlyToMe`来取消 at 机器人的必要性。
```go
. . .
engine.OnFullMatchGroup(chatList, zero.OnlyToMe).SetBlock(true).Handle(
. . .
```
*↑如需取消 at 机器人的必要性，在*`plugin/thesaurus/chat.go`*中找到这一行并把*`zero.OnlyToMe`*删除即可。*

?> 除了上述对台词的修改外，你还可以修改匹配的指令内容。

### 以 manager 为例

manager 是一个群管插件。我们可以通过修改指令内容来让你的群友被你踢出时更加的绚烂夺目！

```go
. . .
// 踢出群聊
engine.OnRegex(`^踢出群聊.*?(\d+)`, zero.OnlyGroup, zero.AdminPermission).SetBlock(true).
Handle(func(ctx *zero.Ctx) {
. . .
```
上面呈现了插件指令部分原来的模样。此时踢出群成员的指令是`踢出群聊 @qq`。

```go
. . .
// 踢出群聊
engine.OnRegex(`^大伊万！.*?(\d+)`, zero.OnlyGroup, zero.AdminPermission).SetBlock(true).
Handle(func(ctx *zero.Ctx) {
. . .
```
作出修改后，踢出群成员的指令就变成了`大伊万！@qq`。其他指令的修改以此类推。但是**请注意，不要修改正则，不要修改正则，不要修改正则**。这可能导致<u>***插件不可用***</u>。所以出现问题时，请及时参照原代码恢复，不然可能发生奇怪的事也说不定...

*（如果你不知道什么是正则，那么只要记住指令中除了中文字之外的内容不要动即可*

## 接下来...

暂时就那么多！如果各位有可以补充的<u>入门级</u>自定义，请提 issue 吧~