# fguby-live2D
![Travis](https://img.shields.io/badge/live2D-2.1.0-ff69b4.svg?labelColor=blueviolet)
![Travis](https://img.shields.io/badge/-javascript-important.svg)

一个配置并不复杂，功能一直在完善的插件，如果各位喜欢，请给我一颗star吧，感激不尽
### φ(≧ω≦*)♪
> 基于官方2.1.0版本的Api开发。

#### 支持功能如下：
- ✅  - 多模型装载
- ✅  - 自定义事件行为
- ✅  - 姐妹花
- ✅  - 快速换衣


> 更多示例正在开发，第一次加载可能会有些慢，见谅~

> 还想要更多吗？请点击
[二次元传送门](https://www.live2d.com/ja/ "live2D")

<h6>简单的几个页面示例</h6>


一 [二次元姐妹花](http://www.midoriya.co:8088/static/sisters.html "live2D")

一 [干物妹小埋：お兄ちゃん](http://www.midoriya.co:8088/static/xiaomai.html "live2D")


一 [多模型装载，点击按钮可切换](http://www.midoriya.co:8088/static/live2D.html "live2D")

一 [药水制作师：快速换装小萝莉](http://www.midoriya.co:8088/static/pio.html "live2D")


---

### 快速开始

<h6>1⃣ 直接使用git命令下载。</h6>


```
git clone https://github.com/fguby/live2D.git
```


<h6>2⃣ 下载压缩包，然后解压。</h6>


### 页面引用

<h6>1️⃣引入核心文件,例如</h6>

```javascript
<script src="js/live2d.min.js"></script>

```
<h6>2️⃣引入配置项js文件。</h6>

```javascript
<script src="js/LAppDefine.js"></script>
```

<h6>3️⃣html页面放置对应的canvas，例如这样：</h6>

```html
<canvas id="mycanvas" width="300" height="500"></canvas>
```

<h6>4️⃣调用初始化的函数,例如：</h6>

```html
<body onload="InitLive2D()">
```

> ~~模型出不来？~~

> YES.😑

或者，请看看自己具体项目里的路径，然后进行修改？

---


#### (๑•̀ㅂ•́)و✧
#### 配置文件LAppDefine.js详解


属性 | 值/含义
---|---
DEBUG_LOG | true/false。是否在console里打印日志。
CANVAS_ID | 页面canvas元素的id值。
IS_SCROLL_SCALE | 是否开启滚轮缩放
VIEW_MAX_SCALE | 画面最大缩放级别
VIEW_MIN_SCALE | 画面最小缩放级别
IS_BIND_BUTTON | 是否绑定切换模型按钮
BUTTON_ID | 绑定按钮的id值，确认绑定时此值才有效。
IS_BAN_BUTTON | 是否开启模型加载过程间的按钮禁用功能。
BAN_BUTTON_CLASS | 按钮禁止状态时的class值，可自定义样式
NORMAL_BUTTON_CLASS | 按钮恢复正常时的class值
TEXURE_CHANGE_MODE | 衣服切换模式，random-随机，sequence-顺序
TEXURE_BUTTON_ID | 换衣绑定的元素id属性，目前仅支持点击触发


<h6>一个完整的LAppDefine.js里最重要的属性：</h6>

```
MODELS:
[
    ["model/haru/haru.model.json"],
    ["model/xiaomai/xiaomai.model.json"],
    ["model/wanko/wanko.model.json"],
    ["model/shizuku/shizuku.model.json"],
    ["model/haru/haru_01.model.json","model/haru/haru_02.model.json"],
    ["model/Epsilon2.1/Epsilon2.1.model.json"],
    ["model/Pio/model.json"]
],
```

> MODELS负责模型json文件的统一配置，如果想要配置自己的多个模型，只需要在这里进行添加即可。（单模型只需添加一个就好)

<h6>❗这里的路径请使用相对路径配置，具体根据对应的实际情况自行配置。</h6>


---
<br> 

> #### 如何同时加载两个模型？


```javascript
//写法如下
MODELS:
[
    [模型1的路径，模型2的路径]
]
```

###### MODELS里的每一个数组成员即使配置超出两个的模型，也只会取前两个，另外双模型的加载现在暂不支持换衣功能。

<br>

> #### 如何配置以及开启换衣功能？

```javascript
//具体配置如下
//1.
IS_START_TEXURE_CHANGE : true,
//2.
TEXURE_CHANGE_MODE : "sequence",
//3.
TEXURE_BUTTON_ID : "button_id",

```
###### 如上，1开启换衣功能的选项，2设置换衣的模式，sequence-顺序，random-随机，3则是设置页面上换衣按钮的id值。

> ##### **在进行这些设置之前，你还需要确保的是：**
>  > 页面按钮元素的放置。
>
>  > 模型json文件的处理。
>
>  > 确保模型已经顺利加载出现。


###### 关于模型json文件的配置，这里以药水制作师的model.json文件举例。


```
"textures":[
    "textures/pajamas-costume.png",
    "textures/Animal Costume Racoon.png",
    "textures/Akiba Idol Costume.png",
    "textures/Goddess Costume Pink.png"
],
```
将需要更换的png图片全都配置在这里，数组的顺序默认就是顺序更换时的顺序。

> 另外需要注意，有些模型虽然配置了多个textures元素，但是是用数张图片配置一个模型，这类的模型目前不支持换衣功能。


---

> #### 如何自定义表情、动作？

一 [干物妹小埋：お兄ちゃん](http://www.midoriya.co:8088/static/xiaomai.html "live2D")

> 想要在对应事件里驱动模型产生对应动作以及表情可以点击上方链接参考，我在页面上放置了三个按钮，分别对应着小埋哭、拿可乐、拿薯片的动作和表情。

写法很简单，只需要调用LAppModel的startAppointMotion函数即可。

例如：


```javascript
var model = new LAppModel();
model.startAppointMotion("start",3,10);
```
参数详解 ⬇️

#### (1)“start”，这个参数为动作组。

查看model.json文件时，motions字段里会有类似以下的写法出现:


```
"idle":[
	{"file":"mtn/I_SURPRISE_W.mtn"},
	{"file":"mtn/I_SURPRISE_W.mtn"},
	......
]
```
> 这个“idle”所代表的就是一系列动作的数组,使用live2D官方的live 2D Viewer可以很方便的查看每个mtn文件所代表的动作是什么。

一 [live2D viewer传送门](https://www.baidu.com/s?wd=live2D%20Viewer "live2D")

另外，我所默认的空闲状态的模型表情以及动作的切换都是在idle动作组里随机触发。

如果你想在这个基础上修改，也很简单。

> 1⃣ 修改LAppDefine里的MOTION_GROUP_IDLE的值，将它设置为你想要触发的动作组。
> 
> 2⃣修改具体model.json文件里的motions字段属性，将你喜欢的动作分成一组，然后设置为1⃣**里的名称**。

<br>

#### (2) 第二个参数3 ，动作的优先级程度。

LAppDefin里设定了四个动作的优先级常量，如下:

```
// 动作优先级常量
PRIORITY_NONE : 0,
PRIORITY_IDLE : 1,
PRIORITY_NORMAL : 2,
PRIORITY_FORCE : 3,
```
3代表优先级最高的动作。

如果你想在页面上某类事件发生后设定一个必定立即触发的动作，可以使用PRIORITY_FORCE来触发动作。

#### （3）第三个参数10，代表动作组里的第(10 + 1)个动作，数组从0开始。

如果你想触发动作组里的某个指定动作，可以传递该参数。如果忽略该参数，则默认从动作组里随机选取动作。

例如：

```javascript
"start":
[
    {"file":"mtn/I_ANGRY.mtn"},
    {"file":"mtn/I_ANGRY_S.mtn"},
    {"file":"mtn/I_ANGRY_W.mtn"},
    {"file":"mtn/I_FUN.mtn"},
    {"file":"mtn/I_FUN_S.mtn"},
    {"file":"mtn/I_FUN_W.mtn"}
]
```

如果我想立即触发start动作组里的I_ANGRY_S.mtn这个动作。


```javascript
model.startAppointMotion("start",3,1);
```

---



> 基于以上的自由开发：
> 
> - 定制各种事件，触发模型的动作以及表情。
> 
(以小埋的动作举例)
>
> - 在深夜时间触发黑眼圈这个动作，自定义提醒的提示信息。
> - 在周六日可以提高可乐、薯片动作的优先级，设定为经常触发。
> - 空闲时间太久可以手动触发哭泣表情，在这基础上可以开发与评论、聊天等系统连接的事件。
> - 等等等。

#### 未完待续。。。

> 2019.04.21 00:30
>
> 跪求✨⭐🌟💫💥💥
>
>(°ー°〃)
