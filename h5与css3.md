# HTML5

广义的 HTML5 是 html5 本身+css3+js
新特性：语义特性，本地存储特性，设备兼容特性，连接特性，网页多媒体特性，三维，图形和特效，css3 特性

## 新增语义化标签

```
<header>，头部
<nav>，导航
<article>，文章
<section>，块级
<aside>，侧边栏
<footer>，尾部
```

### 注意

- 语义化是针对搜索引擎的
- 标签可以使用多次
- ie9 中要转换成块级
- 移动端更常用

## 新增音频标签

### audio 标签

#### 音频格式

支持三种格式，ogg,mp3,wav,但是不是所有浏览器都支持，具体再查

#### 语法

```
<audio src="" controls="controls></audio>
```

#### 常见属性

- autoplay,值为 autoplay，如果出现该属性，则音频在就绪后马上播放，谷歌禁用了自动播放
- controls，值为 controls，如果出现该属性，则向用户显示控件，比如播放按钮
- loop，值为 loop，如果出现该属性，则每当音频结束时重新开始播放
- src，值为 URL，要播放音频的 URL

#### 不同格式的音频

因为不同浏览器支持不同格式，所以要为音频准备多个格式

```
<audio controls="controls>
	<source src="xxx.mp3" type="audio/mpeg">
	<source src="xxx.ogg" type="audio/ogg">
	您的浏览器太low了，不支持audio播放
</audio>
```

### 视频标签 video

#### 视频格式

支持三种格式，Ogg,Mpeg4,Webm,但是不是所有浏览器都支持，具体再查

#### 语法

```
<video src="" controls="controls></video>


<video controls="controls>
	<source src="xxx.mp4" type="video/mp4">
	<source src="xxx.ogg" type="video/ogg">
	您的浏览器太low了，不支持video播放
<video>
```

#### 常用属性

- autoplay,值为 autoplay，如果出现该属性，则视频在就绪后自动播放，谷歌禁用了自动播放，解决方案是给视频添加静音属性
- controls，值为 controls，如果出现该属性，则向用户显示控件，比如播放按钮
- loop，值为 loop，如果出现该属性，则每当音频结束时重新开始播放，循环播放
- src，值为 URL，要播放音频的 URL
- width,值为像素，设置播放器宽度
- height，值为像素设置播放器高度
- preload，值为 preload，是否等加载完再播放
- poster，加载等待的画面图片
- muted，静音播放

### 新增 input 标签

type="email",限制用户必须输入 Email 类型
type="url",限制用户必须输入 url 类型
type="date",限制用户必须输入 date 类型
type="time",限制用户必须输入 time 类型
type="month",限制用户必须输入 month 类型
type="week",限制用户必须输入 week 类型
type="number",限制用户必须输入 number 类型,重点
type="tel",限制用户必须输入 tel 类型，重点
type="search",限制用户必须输入 sarch 类型，重点
type="color",限制用户必须输入 color 类型

### 新增表单属性

required,值为 required，表示该元素的内容不能为空，必填
placeholder，值为提示文本，占位符，表单的提示信息
autofocus，值为 autofocus，自动聚焦
autocomplete，值为 on 或者 off，当用户在字段开始键入时，浏览器基于之前键入过的值应该显示出在字段中填写的选项
multiple，值为 multiple，可以多选文件提交

# CSS3

## 选择器

### 属性选择器

1. E[att]，选择具有 att 属性的 E 元素
2. E[att="val"]，选择具有 att 属性且属性值等于 val 的 E 元素
3. E[att^="val"]，选择具有 att 属性且属性值以 val 开头的 E 元素
4. E[att$="val"]，选择具有 att 属性且属性值以 val 结尾的 E 元素
5. E[att*="val"]，选择具有 att 属性且属性值中含有 val 的 E 元素
6. 类选择器，属性选择器，伪类选择器的权重都为 10

### 结构伪类选择器

1. E:first-child，匹配父元素中的第一个子元素 E
2. E:last-child，匹配父元素中的最后一个子元素 E
3. E:nth-child(n)，匹配父元素中的第 n 个子元素 E
4. E:first-of-type，指定类型 E 的第一个
5. E:last-of-type，指定类型 E 的最后一个
6. E:nth-of-type(n)，指定类型 E 的第 n 个

#### nth-child(n)

1. n 可以是数字，关键字，公式
2. n 如果是数字，就是选择第几个
3. 常见的关键字有 even 偶数，odd 奇数
4. 常见公式如下，如果 n 是公式，则从 0 开始计算，但是第 0 个元素或者超出了元素的个数会被忽略

- 2n 偶数
- 2n+1，奇数
- 5n，5 的倍数
- n+5，从第五个开始
- -n+5，前 5 个，包含第五个

#### nth-child(n)和 nth-of-type(n)区别

nth-child(n)只选择父元素第几个子元素，不管子元素是否是同一种什么类型，如果选择的第 n 个子元素时还限定了元素标签，有可能取不到
nth-of-type(n)选择指定类型的子元素

```
<style>
div span:nth-child(1){  //取不到，因为div的第一个子元素是p，不是span
	...
}

div span:nth-child(2){  //这样可以
	...
}

div span:nth-of-type(1){  //这样可以
	...
}
</style>

<div>
<p></p>
<span></span>
<span></span>
<span></span>
<span></span>
</div>
```

#### 小结

- 结构伪类选择器就是选择第几个元素
- nth-child(n)是从所有子级开始算的，可能不是同一种类型
- nth-of-type(n)是指定同一种类型的子级
- 如果是无序列表，用 nth-child(n)

### 伪元素选择器

- ::before,在元素内部的前面插入内容
- ::after，在元素内部的后面插入内容

#### 注意

before 和 after 必须有 content 属性
before 在内容的前面，after 在内容的后面
before 和 after 创建一个元素，属于行内元素
因为在 dom 里面看不见创建的元素，所以称为伪元素
伪元素和标签选择器一样权重为 1

## 2D 转换

### 移动 translate

2D 移动是 2D 转换里面的一种功能，可以改变元素在页面中的位置，类似定位

#### 语法

```
transform: translate(x,y); //x为x轴坐标，y为y轴坐标
transform: translateX(n); //沿着x轴移动n像素
transform: translateY(n);//沿着y轴移动n像素
```

#### 重点

- 定义 2D 转换中的移动，沿着 x 和 y 轴移动元素
- translate 最大的优点，不会影响到其他元素的位置
- translate 中的百分比是相对于自身元素的
- 对行内标签没有效果

#### 利用移动实现垂直居中

```
<style>
			.p {
				position: relative;
				height: 200px; /*需要垂直居中的地方的父元素一定有具体的高*/
			}

			.c {
				position: absolute;
				top: 50%;
				left: 50%;
				transform: translate(-50%,-50%);/*这里可以用margin-left，margin-top各为子元素-(具体宽高的一半)*/
			}
		</style>
	<body>
		<div class="p">
			<div class="c">12536</div>
		</div>
	</body>
```

### 旋转 rotate

2D 旋转是指让元素在 2 维平面顺时针或者逆时针旋转

#### 语法

```
transform: rotate(度数)
```

#### 重点

- rotate 里面跟度数，单位是 deg 比如 rotate（45deg)
- 角度为正时，顺时针，负时，逆时针
- 默认旋转的中心点是元素的中心点

#### 旋转 365 度的动画效果：要用到过渡

```
img{
    width: 150px;
    border-radius:50%;
    border: 5px solid pink;
    /*过渡写到本身上，谁做动画给谁加*/
    transition: all 0.3s;
}

img:hover{
    transform:rotate(365deg)
}
```

### 2D 转换中心点 transform-origin

#### 语法

```
transform-origin：x y;
```

#### 重点

- 参数 x 和 y 用空格隔开
- xy 默认的转换中心点是元素的中心点（50%，50%）
- xy 的值可以为像素或者方位名词 top，bottom，left，right，center

### 缩放 scale

#### 语法

```
transform: scale(x,y);
```

#### 注意

- x 和 y 用逗号分隔
- transform：scale(1,1),里面写的数组不跟单位，就是倍数的意思，1 是 1 倍，
- transform：scale(2,2)，宽和高都放大了 2 倍
- transform：scale(2)，只写一个参数，则第二个参数和第一个参数一样，相当于 scale（2，,2），实现等比例缩放效果
- transform：scale(0.5,0.5)，参数小于 1 时为缩小
- scale 的最大优势就是可以用 transform-origin 设置转换中心，默认是以中心点缩放，而且不影响其他盒子，传统方式修改宽和高来实现缩放效果会影响到其他盒子

### 2D 转换综合写法

同时使用多个转换，其格式为：transform:translate() rotate() scale()等
其顺序会影响转换的效果，先旋转会改变坐标轴方向
当我们同时有位移和其他属性的时候，记得要将位移放到最前面

## css3 动画 animation

### 动画的基本使用

制作动画需要两步

1. 先定义动画，用 keyframes 定义动画,类似定义类选择器

```
@keyframes 动画名称{
	/*开始状态*/
	0% {
		width: 100px;
	}
	/*结束状态*/
	100% {
		width: 200px;
	}
}
```

2. 再调用动画

```
div {
	width: 200px;
	height: 200px;
	/*调用动画*/
	animation-name: 动画名称；
	/*持续时间*/
	animation-duration: 持续时间；
}
```

2. 元素可以添加多个动画，在元素添加动画时用逗号隔开即可

### 动画序列

0%是动画的开始，100%是动画的完成，这样的规则就是动画序列
在@keyframes（关键帧）中规定某项 css 样式，就能创建由当前样式逐渐改为新样式的动画效果
动画是使元素从一种样式逐渐变化成另一种样式的效果，可以改变任意多的样式和任意多的次数
请使用百分比来规定变化发生的时间，百分比要用整数，百分比是时间的划分，或者用关键词 from 或者 to，他们等同 0%和 100%

### 动画的常见属性

- animation-name,动画名称，必须
- animation-dutration。动画持续时间，必须
- animation-timing-function，速度曲线，默认是 ease
- animation-delay,动画何时开始
- animation-iteration-count,重复次数，默认 1 次，无限用 infinite
- animation-direction,运动方向，规定动画是否在下一个周期逆向播放，默认 normal，如果要反方向用 alternate
- animation-fill-mode,动画结束状态，默认是 backwards 回到起始状态，如果想停留在结束状态用+ forwards
- animation-play-state,动画是否正在运行或暂停，默认是 running，暂停可以设置成 paused

### 动画简写属性

animation：动画名称 持续时间 运动曲线 何时开始 播放次数 是否反方向 动画起始或者结束状态
注意

- 简写属性里面不包含 animation-play-state
- 暂停动画 animation-play-state：paused，经常和鼠标经过等其他配合使用
- 想要动画走回来而不是直接跳回来：animation-direction:alternate
- 盒子动画结束后，停在结束位置：animation-fill-mode: forwards

### 速度曲线细节

animation-timing-function，速度曲线，默认是 ease
linear,动画从头到尾的速度是相同的，匀速
ease，默认状态，动画以低速开始，然后加快，在结束前变慢
ease-in，动画以低速开始
ease-out，动画以低速结束
ease-in-out，动画以低速开始和结束
steps()，指定了时间函数中的间隔数量（步长），就是分几步完成动画

## 3D 转换

3D 特点：近大远小，物体后面遮挡不可见

### 三维坐标系

x 轴：水平向右，往右是正值，往左是负值
y 轴，垂直向下，往下是正值，往上是负值
z 轴，垂直屏幕，往外面是正值，往里面是负值

### 3D 移动 translate3d

3D 移动就是在 2D 移动的基础上加了一个移动方向，Z 轴方向
transform: translateX(100px),仅仅在 x 轴移动 100px
transform: translateY(100px),仅仅在 y 轴移动 100px
transform: translateZ(100px),仅仅在 z 轴移动 100px,注意 z 轴移动一般用 px，要有透视才有效果
transform: translate3d(x,y,z)，注意 xyz 是不能省略的，如果不移动就写 0

### 3D 转换

#### 透视 perspective

1. 近大远小

- 如果想要在网页上产生 3D 效果需要透视，可以理解为 3D 物体投影到 2D 平面上
- 模拟人类的视觉位置
- 透视我们也称视距：人的眼睛到屏幕的距离
- 距离视觉点越近的在电脑平面成像越大，越远成像越小
- 透视的单位是像素

2. 透视写在被观察元素的父盒子上面

#### 3D 旋转

1. 3D 旋转指可以让元素在三维平面内沿着 x 轴，y 轴，z 轴或者自定义轴进行旋转
2. 语法

```
transform:rotateX(45deg);//沿着x轴正方向旋转45度
transform:rotateY(45deg);//沿着y轴正方向旋转45度
transform:rotateZ(45deg);//沿着Z轴正方向旋转45度
transform:rotate3d(x,y,z,deg);//沿着自定义轴旋转deg为角度，了解
```

3. 判断元素 rotateX 旋转方向，左手准则：左手的拇指指向 x 轴的正方向，其余手指的弯曲方向就是该元素沿着 x 轴旋转的正方向
4. 要实现 3D 效果要在父元素加透视
5. 判断元素 rotateY 旋转方向，左手准则：左手的拇指指向 y 轴的正方向，其余手指的弯曲方向就是该元素沿着 y 轴旋转的正方向

#### 3D 呈现 transform-style

控制子元素是否开启三维立体环境
transform-style：flat 子元素不开启 3d 立体空间，默认状态
transform-sytle：preserve-3d，子元素开启立体空间
代码写给父级，但是影响的是子盒子

# 浏览器私有前缀

主要是为了兼容老版浏览器

## 私有前缀

- -moz-：火狐
- -ms-:ie
- -webkit-: safari,chrome
- -o-: Opera

## 提倡写法

```
-moz-border-radius:10px;
-webkit-border-radius: 10px;
-o-border-radius: 10px;
border-radius:10px
```
