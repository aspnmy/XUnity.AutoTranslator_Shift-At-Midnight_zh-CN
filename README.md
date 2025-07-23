# XUnity.AutoTranslator_Shift-At-Midnight_zh-CN
- 使用自动翻译组件XUnity.AutoTranslator ,来自动翻译Shift At Midnight
Shift At Midnight，深夜超市鉴别伪人的demo挺好玩的，从官网下载以后，原生是不支持简体中文的，所以就写个指南，如何使用自动翻译组件XUnity.AutoTranslator来自动翻译英文，显示成简体中文。

## 1、安装BepInEx_win_x64_5.4.23.3.zip(这个在github中搜索一下)
## 2、安装XUnity.AutoTranslator-BepInEx-5.4.5.zip(这个在github中搜索一下)
## 3、把上面的内容安装到游戏Demo的根目录下，运行一次游戏，然后点退出。
## 4、进入自动翻译的配置ini文件进行配置：{游戏根目录}\BepInEx\config\AutoTranslatorConfig.ini
## 5、配置翻译引擎的AppID和Appkey，我使用的是baidu，如果你也想使用百度，就到【百度翻译开放平台】去注册一个开发者账户，怎么注册百度一下很多教程

```
[Baidu]
BaiduAppId=你的Appid
BaiduAppSecret=你的Appkey
DelaySeconds=1

```

## 6、配置一下默认的翻译引擎和备用引擎，及翻译的语言：我的配置是这样的

```
[Service]
Endpoint=BaiduTranslate ;主翻译引擎
FallbackEndpoint=PapagoTranslate ;备用翻译引擎

[General]
Language=zh-CN ;被翻译成的语言
FromLanguage=en ;游戏原生语言

```

## 7、保存配置文件，重启游戏，进入游戏界面后，按“Alt+0”,看看是否正确呼起AutoTranslator的配置界面，能跳出说明配置正常;
## 8、判断翻译引擎是否正常，进入游戏界面后，按“Alt+1”,看看翻译日志界面是否，正确抓取到翻译前后翻译后的字符串，如果有跳出证明翻译引擎正常。
## 9、正确显示中文字符串（不能正确显示的时候会显示成□□□，说明缺少中文字体包）。Shift At Midnight是基于Untiy 2022.3.34f1c1版本开发的，目前原生不支持简体中文，作者打包字符包的时候没有打包中文的TMP字符资源在游戏里，为了翻译成简体中文的字符正确显示，所以我们需要自己挂载一个基于Untiy 2022.3.34f1c1制作的显示简体中文的TMP字符包
### 9.1 打开Untiy 2022.3.34f1c1，导入一个中文字体otf文件，选择导出成Untiy TMP字符库(具体可以搜索引擎上找教程，比较多)。导出后复制到目录:{游戏根目录}BepInEx\Translation\zh-CN\Fonts\cnFonts.asset 中
### 9.2 修改 {游戏根目录}\BepInEx\config\AutoTranslatorConfig.ini ，[Behaviour]下找到下面两个参数指向TMP资源包

```
[Behaviour]
OverrideFontTextMeshPro=BepInEx\Translation\zh-CN\Fonts\cnFonts_01
FallbackFontTextMeshPro=BepInEx\Translation\zh-CN\Fonts\cnFonts_02

```

- FallbackFontTextMeshPro是备用字体包，如果需要配置的话，再制作一个，然后配置在ini中。
### 9.3、字体文件位置，如果你不知道存放在哪里，那就存在游戏根目录上。我自己就是存这里的，当然ini的配置文件中需要改一下参数值。

## 10、运行游戏，正确显示中文。
最后，希望作者原生支持简体中文。

## 11、相关资源包：简化大家操作，就放一个自动翻译挂载的整合包，复制到游戏Demo根目录下即可。请不要商用，保留出处即可。

- 下载本git，覆盖在游戏Demo的根目录下。翻译文件已经内置，哪怕连不上搜索引擎也可以使用。

## 12、常见问题：
### 12.1 是否可以用Untiy 最新版来制作字体文件？
为了兼容性的问题，请用游戏本体的版本来制作TMP字符包。过低过高版本都会有意外。
### 12.2 是否可以用BepInEx的其他版本来挂载？
理论上是可以的，具体请自行测试。
