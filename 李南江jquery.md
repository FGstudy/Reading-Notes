## jQuery基础
### 入口函数
1. 入口函数的写法
```
//原生js写法
window.onload = function(event){
	...
}

//jQuery写法
$(document).ready(function(){
	
});

```
2. 原生js与jQuery入口函数的区别
+ 加载模式不同，原生JS会等到DOM元素加载完毕,并且图片也加载完毕才会执行，jQuery会等到DOM元素加载完毕,但不会等到图片也加载完毕就会执行
+ 原生的JS如果编写了多个入口函数,后面编写的会覆盖前面编写的，jQuery中编写多个入口函数,后面的不会覆盖前面的
3. 入口函数的其他写法
```
// 1.第一种写法
        $(document).ready(function () {
            // alert("hello lnj");
        });

        // 2.第二种写法
        jQuery(document).ready(function () {
            // alert("hello lnj");
        });

        // 3.第三种写法(推荐)
        $(function () {
            // alert("hello lnj");
        });
        // 4.第四种写法
        jQuery(function () {
            alert("hello lnj");
        });
```
4. 如果使用的其他框架中也使用了$，则可能会导致冲突问题，解决方法
+ 释放$的使用权， 注意点: 释放操作jQuery.noConflict();必须在编写其它jQuery代码之前编写，释放之后就不能再使用$,改为使用jQuery，
+ 自定义一个访问符号，例如nj= jQuery.noConflict();
### 核心函数
1. $()；里面可以接收参数类型，
+ 接收一个函数，例如入口函数
+ 接收一个字符串
	+ 接收一个字符串选择器，返回一个jQuery对象, 对象中保存了找到的DOM元素
	+ 接收一个字符串代码片段，返回一个jQuery对象, 对象中保存了创建的DOM元素
```
var $box1 = $(".box1");
var $box2 = $("#box2");
console.log($box1);
console.log($box2);
var $p = $("<p>我是段落</p>");
console.log($p);
$box1.append($p);
```
+ 接收一个DOM元素，该元素会被包装成一个jQuery对象返回
```
ar span = document.getElementsByTagName("span")[0];
console.log(span);
var $span = $(span);
console.log($span);
```
### jQuery对象
1. jQuery对象是一个伪数组
2. 伪数组就是有0到length-1的属性, 并且有length属性的对象
### 静态方法与实例方法
1. 在js中静态方法就是直接添加到类上面的，实例方法是直接添加到类的原型上面的
+ 静态方法通过类名调用，实例方法通过实例调用
2. 静态方法each方法
+ 原生js的forEach方法，接收两个参数，第一个参数是遍历到的元素，第二个参数是当前遍历到的索引，注意该方法可能遍历数组，不能遍历伪数组
```
arr.forEach(function (value, index) {
    console.log(index, value);
});
```
+ 利用jQuery的each静态方法遍历数组,接收两个参数，接收一个参数是处理数组元素的函数，注意 jQuery的each方法是可以遍历伪数组的
```
$.each(arr, function (index, value) {
	console.log(index, value);
```
3. 静态方法map方法
+ 利用原生JS的map方法遍历，接收三个参数：第一个参数: 当前遍历到的元素，第二个参数: 当前遍历到的索引，第三个参数: 当前被遍历的数组
    +注意点: 和原生的forEach一样,不能遍历的伪数组
+ 利用jQuery的map静态方法遍历数组，第一个参数: 要遍历的数组 第二个参数: 每遍历一个元素之后执行的回调函数
    + 回调函数的参数:第一个参数: 遍历到的元素，第二个参数: 遍历到的索引
    + 注意点:和jQuery中的each静态方法一样, map静态方法也可以遍历伪数组
```
$.map(arr, function (value, index) {
     console.log(index, value);
 });
```
4. jQuery的map和each的区别
+ 返回值不同
	+ each静态方法默认的返回值就是, 遍历谁就返回谁
	+ map静态方法默认的返回值是一个空数组‘
+ 对数组的处理不同
	+ each静态方法不支持在回调函数中对遍历的数组进行处理
	+ map静态方法可以在回调函数中通过return对遍历的数组进行处理, 然后生成一个新的数组返回
5. 其他静态方法
+  $.trim();
	+ 作用: 去除字符串两端的空格
	+ 参数: 需要去除空格的字符串
	+ 返回值: 去除空格之后的字符串
+ $.isWindow();
	+ 作用: 判断传入的对象是否是window对象
	+ 返回值: true/false
+ $.isArray();
	+ 作用: 判断传入的对象是否是真数组
	+ 返回值: true/false
+ $.isFunction();
	+ 作用: 判断传入的对象是否是函数
	+ 返回值: true/false
	+ jQuery框架本质上是一个函数(function( window, undefined ) {})( window );
6. $.holdReady(true); 作用: 暂停ready执行，$.holdReady(false);取消暂停 
### 选择器
大部分跟css选择器一样，可以查文档
1. :empty 作用:找到既没有文本内容也没有子元素的指定元素
```
var $div = $("div:empty");
console.log($div);
```
2. :parent 作用: 找到有文本内容或有子元素的指定元素
```
var $div = $("div:parent");
console.log($div);
```
3. :contains(text) 作用: 找到包含指定文本内容的指定元素
```
var $div = $("div:contains('hello')");
console.log($div);
```
4. :has(selector) 作用: 找到包含指定子元素的指定元素
```
var $div = $("div:has('span')");
console.log($div);
```
### 属性和属性节点
#### 原生js
1. 属性：对象身上保存的变量就是属性
2. 操作属性
+ 对象.属性名称 = 值;
+ 对象.属性名称;
+ 对象["属性名称"] = 值;
+ 对象["属性名称"];
3. 属性节点:在编写HTML代码时,在HTML标签中添加的属性就是属性节点,例如
```
<span name = "it666"></span> //name就是属性节点
```
4. 查看属性和属性节点：在浏览器中找到span这个DOM元素之后, 展开看到的都是属性，在attributes属性中保存的所有内容都是属性节点
+ 如何找到这个元素？在浏览器f12后，点开source，在最左边选中要查看的文档后，看最右边上面的watch，如果watch为空白，则可以点击上面的+按钮，再输入document.getElementsByTagName("span");后回车，就能找到dom元素
5. 如何操作属性节点:
+ DOM元素.setAttribute("属性名称", "值");
+ DOM元素.getAttribute("属性名称");
6. 属性和属性节点有什么区别:任何对象都有属性, 但是只有DOM对象才有属性节点
#### jQuery操作属性和属性节点
1. attr(name|pro|key,val|fn)
+ 作用: 获取或者设置属性节点的值
+ 参数：可以传递一个参数, 也可以传递两个参数
	+ 如果传递一个参数, 代表获取属性节点的值
	+ 如果传递两个参数, 代表设置属性节点的值
+ 注意
	+ 如果是获取:无论找到多少个元素, 都只会返回第一个元素指定的属性节点的值
	+ 如果是设置:找到多少个元素就会设置多少个元素
	+ 如果是设置: 如果设置的属性节点不存在, 那么系统会自动新增
2. removeAttr(name)， 删除属性节点，注意点:会删除所有找到元素指定的属性节点
3. prop方法，特点和attr方法一致，注意 prop方法不仅能够操作属性, 他还能操作属性节点
4. removeProp方法，特点和removeAttr方法一致
5. 官方推荐在操作属性节点时,具有 true 和 false 两个属性的属性节点，如 checked, selected 或者 disabled 使用prop()，其他的使用 attr()
### 操作类
1. addClass(class|fn)
+ 作用: 添加一个类
+ 如果要添加多个, 多个类名之间用空格隔开即可
2. removeClass([class|fn])
+ 作用: 删除一个类
+ 如果想删除多个, 多个类名之间用空格隔开即可
3. toggleClass(class|fn[,sw])
+ 作用: 切换类
+ 有就删除, 没有就添加
### 文本值相关
1. html([val|fn])
+ 和原生JS中的innerHTML一模一样
2. text([val|fn])
+ 和原生JS中的innerText一模一样
3. val([val|fn|arr])
+ 和原生JS中的value一模一样
### css
#### 操作样式css
1. 逐个设置
```
$("div").css("width","100px");
$("div").css("height",100px);
```
2. 链式设置，注意点: 链式操作如果大于3步, 建议分开
```
$("div").css("width","100px").css("height","100px");
```
3. 批量设置
```
$("div").css({
	width: 100px,
	height: 100px
})
```
4. 获取CSS样式值
```
$("div").css("width");

```
#### 位置与尺寸
1. 获取元素的宽度 
```
//获取
$(".father").width();
//设置
$(".father").width("100px")
```
2. offset([coordinates])
+ 作用: 获取元素距离窗口的偏移位
```
//获取元素距离窗口左边的偏移位
console.log($(".son").offset().left);
//设置素距离窗口左边的偏移位
$(".son").offset({
	left:10 //注意没有单位
})
``` 
3. position()
+ 作用: 获取元素距离定位元素的偏移位
+ position方法只能获取不能设置,如果需要设置可以通过css方法设置
```
$(".son").css({
	left:"10px"
});
```
#### 滚动偏移
1. 获取滚动的偏移位，$(".scroll").scrollTop()
2. 获取网页滚动的偏移位，
+ 注意点: 为了保证浏览器的兼容, 获取网页滚动的偏移位需要按照如下写法
```
$("body").scrollTop() + $("html").scrollTop();
```
3. 设置滚动的偏移位, $(".scroll").scrollTop(300);注意这里传数字值而不是字符串
4. 设置网页滚动偏移位
+ 注意点: 为了保证浏览器的兼容, 设置网页滚动偏移位的时候必须按照如下写法
```
$("body,html").scrollTop(300)
```
### 事件
#### 事件绑定
1. eventName(fn); 编码效率略高/ 部分事件jQuery没有实现,所以不能添加,jq实现的事件可以查API
```
$("button").click(function(){
	alert("hello");
})
```
2. on(eventName, fn); 编码效率略低/ 所有js事件都可以添加，还可以添加自定义事件和事件命名空间
```
$("button").on("click",function(){
	alert("hello");
})
```
3. 上面两个方法可以添加多个相同或者不同类型的事件,不会覆盖
#### 事件移除
1. 移除事件使用off方法
+ 如果不传递参数, 会移除所有的事件， $("button").off();
+ 传递一个参数, 会移除所有指定类型的事件，$("button").off("click");
+ 传递两个参数, 会移除所有指定类型的指定事件， $("button").off("click", test1);
#### 事件冒泡和默认行为
1. 什么是事件冒泡，事件触发顺序是由内到外的，虽然只点击子元素，但是它的父元素也会触发相应的事件
2. 如何阻止事件冒泡，注意阻止事件冒泡的方法要写在子元素里
+ 设置事件函数返回值为false
```
$(".son").click(function(event){ //每触发一个事件都会产生一个event对象
	//return false;
	event.stopPropagation(); //注意这两个阻止方法都要在子元素里面写
})
```
+ 使用 event.stopPropagation();
3. 什么是默认行为，就是一个标签自带的默认行为，比如点击a标签会跳转
4. 如何阻止默认行为，
+ 设置事件函数返回值为false
+ 使用event.preventDefault();
```
 $("a").click(function (event) {
                alert("弹出注册框");
                // return false;
                event.preventDefault();
            });
```
#### 事件自动触发
1. trigger: 如果利用trigger自动触发事件,会触发事件冒泡，会触发默认行为
2. triggerHandler: 如果利用triggerHandler自动触发事件, 不会触发事件冒泡，不会触发默认行为
```
$(".son").click(function(){
	alert("son");
})
$(".son").trigger("click"); //原来要点击才能触发，现在是不用点击，自动触发
$(".son").triggerHandler("click")
```
3. 注意，a标签有个特别之处，如果利用trigger自动触发事件后不会触发默认行为，如果想要想让a触发默认行为，则需要在a标签中放一个span标签，然后对span标签设置事件，自动触发也要设置到span上,写成下面的样子
```
 $("span").click(function () {
                alert("a");
            });
 $("span").trigger("click");
```
#### 自定义事件
1. 两个条件
+  事件必须是通过on绑定的
+  事件必须通过trigger或者triggerHandler来触发
```
 $(".son").on("myClick", function () {
                alert("son");
            });
            $(".son").triggerHandler("myClick");
```
#### 事件命名空间,多人协作时注意
1. 两个条件
+  事件必须是通过on绑定的
+  事件必须通过trigger或者triggerHandler来触发
```
 $(".son").on("click.zs", function () {
	alert("click1");
});
 $(".son").on("click.ls", function () {
	alert("click2");
});
// $(".son").trigger("click.zs");
$(".son").trigger("click.ls");
```
2. 利用trigger触发子元素带命名空间的事件, 那么父元素带相同命名空间的事件也会被触发. 而父元素没有命名空间的事件不会被触发
3. 利用trigger触发子元素不带命名空间的事件,那么子元素所有相同类型的事件和父元素所有相同类型的事件都会被触发
#### 事件委托
1. 什么是事件委托?请别人帮忙做事情, 然后将做完的结果反馈给我们
2. 在jQuery中,如果通过核心函数找到的元素不止一个, 那么在添加事件的时候,jQuery会遍历所有找到的元素,给所有找到的元素添加事件
```
$("ul>li").click(function () {
     console.log($(this).html());
 });
```
3. 事件委托示例
+ 解析： 以下代码的含义, 让ul帮li监听click事件 之所以能够监听, 是因为入口函数执行的时候ul就已经存在了, 所以能够添加事件，之所以this是li,是因为我们点击的是li, 而li没有click事件, 所以事件冒泡传递给了ul,ul响应了事件, 既然事件是从li传递过来的,所以ul必然指定this是谁
```
$("ul").delegate("li", "click", function () {
	console.log($(this).html());
});
```
#### 移入移出事件
1.  mouseover/mouseout事件, 子元素被移入移出也会触发父元素的事件
2.  mouseenter/mouseleave事件, 子元素被移入移出不会触发父元素的事件
3. hover事件,接收两个参数，都是函数作为参数，第一个参数的函数是移入事件的，第二个参数的函数是移出事件的，如果只传了一个函数说明触发移入移出事件
### 动画效果
#### 基本
1. show([s,[e],[fn]])，显示隐藏的匹配元素。第一个参数是速度，一般用毫秒值，第二个参数可选表示效果默认是"swing"（加速），可用参数"linear"（匀速），第三个参数是回调函数，在动画完成时执行，
2. hide([s,[e],[fn]])，隐藏显示的元素，参数基本同上
3. toggle([s,[e],[fn]]),如果元素是可见的，切换为隐藏的；如果元素是隐藏的，切换为可见的。
#### 滑动
1. slideDown([s],[e],[fn])
2. slideUp([s,[e],[fn]])
3. slideToggle([s],[e],[fn])
#### 淡入淡出
1. fadeIn([s],[e],[fn])
2. fadeOut([s],[e],[fn])
3. fadeTo([[s],o,[e],[fn]]) ，可以设置淡到什么程度
4. fadeToggle([s,[e],[fn]])，如果元素是可见的，切换为淡出的；如果元素是隐藏的，切换为淡入的
#### 自定义
1. animate(p,[s],[e],[fn])，
+ 第一个参数: 接收一个对象, 可以在对象中修改属性
	+  在jQuery的{}中可以同时修改多个属性, 多个属性的动画也会同时执行
+ 第二个参数: 指定动画时长
+ 第三个参数: 指定动画节奏, 默认就是swing
+ 第四个参数: 动画执行完毕之后的回调函数
#### stop,delay
1. stop([c],[j])
2. delay(d,[q])，用于告诉系统延迟时长
3. finish([queue]),等同于stop
4. stop的参数不同，效果也不同
+ 立即停止当前动画, 继续执行后续的动画
```
// $("div").stop();
// $("div").stop(false);
// $("div").stop(false, false);

```
+ 立即停止当前和后续所有的动画    
```
// $("div").stop(true);
 // $("div").stop(true, false);
```
+ 立即完成当前的, 继续执行后续动画
```
$("div").stop(false, true);
```
+ 立即完成当前的, 并且停止后续所有的
```
 $("div").stop(true, true);
```
### 节点相关
#### 添加节点
1. 内部插入
+ 会将元素添加到指定元素内部的最后      append(content|fn)，appendTo(content)
+ 会将元素添加到指定元素内部的最前面     prepend(content|fn)， prependTo(content)
2. 外部插入
+ 会将元素添加到指定元素同级的后面       after(content|fn)
+ 会将元素添加到指定元素同级的前面       before(content|fn)    
3. 外部插入，与2的写法相反            insertAfter(content)，insertBefore(content)
#### 删除节点
1. remove([expr])删除指定元素
2. empty() 删除指定元素的内容和子元素, 指定元素自身不会被删除
3. detach([expr])跟remove一样
4. detach与remove的区别：
+ 利用remove删除之后再重新添加,原有的事件无法响应
+ 利用detach删除之后再重新添加,原有事件可以响应   
#### 替换节点
1. 替换所有匹配的元素为指定的元素        replaceWith(content|fn)，  replaceAll(selector)
#### 复制节点
1. clone([Even[,deepEven]]) 如果传入false就是浅复制, 如果传入true就是深复制
+ 浅复制只会复制元素, 不会复制元素的事件 
+ 深复制会复制元素, 而且还会复制元素的事件
## jQuery原理
### jQuery的基本结构
1. jQuery的本质是一个闭包
2. jQuery为什么要使用闭包来实现?
+ 为了避免多个框架的冲突
3. jQuery如何让外界访问内部定义的局部变量
+ window.xxx = xxx;
4. jQuery为什么要给自己传递一个window参数?
+ 为了方便后期压缩代码
+ 为了提升查找的效率
5. jQuery为什么要给自己接收一个undefined参数?
+ 为了方便后期压缩代码
+ IE9以下的浏览器undefined可以被修改, 为了保证内部使用的undefined不被修改, 所以需要接收一个正确的undefined
```
//用原生js实现jQuery框架
(function( window, undefined ) {
    var njQuery = function(selector) {
        return new njQuery.prototype.init(selector);
    }
    njQuery.prototype = {
        constructor: njQuery,
        init: function (selector) {
           
    njQuery.prototype.init.prototype = njQuery.prototype;
    window.njQuery = window.$ = njQuery;
})( window );
```
### jQuery的入口函数	
#### jQuery的入口函数传入不同类型的参数的情况
1. 传入 '' null undefined NaN  0  false, 返回空的jQuery对象
2. 字符串:
+ 代码片段:会将创建好的DOM元素存储到jQuery对象中返回
+ 选择器: 会将找到的所有元素存储到jQuery对象中返回
3. 数组:会将数组中存储的元素依次存储到jQuery对象中返回，无论是真数组还是伪数组
4. 除上述类型以外的:会将传入的数据存储到jQuery对象中返回，
+ 传入对象会将传入的对象存储到jQuery对象中返回，
+ 传入基本类型数据就将基本类型数据存储到jQuery对象中返回，
+ 传入DOM元素会将传入的DOM元素存储到jQuery对象中返回
#### 用原生js实现入口函数，并实现上述功能
具体可以查看H:\教学视频\jQuery\jQuery原理\js\njQuery-1.0.0.js，以下记录几个点
1. 实现传入 '' null undefined NaN  0  false, 返回空的jQuery对象
```
if(!selector){
	return this;
}
```
2. 实现传入代码片段将创建好的DOM元素存储到jQuery对象中返回
```
// 1.根据代码片段创建所有的元素
	var temp = document.createElement("div");
	temp.innerHTML = selector;

	/* 原始写法：不建议使用
	// 2.将创建好的一级元素添加到jQuery当中
	for(var i = 0; i < temp.children.length; i++){
		this[i] = temp.children[i];
	}
	// 3.给jQuery对象添加length属性
	this.length = temp.children.length;
	*/
	//进阶写法，推荐使用
	[].push.apply(this, temp.children);
	// 此时此刻的this是njQuery对象
	// 4.返回加工好的this(jQuery)
	// return this;

```
3. 实现传入选择器会将找到的所有元素存储到jQuery对象中返回
```
var res = document.querySelectorAll(selector);
// 2.将找到的元素添加到njQuery上
[].push.apply(this, res);
// 3.返回加工上的this
// return this;
```
4. 实现传入数组会将数组中存储的元素依次存储到jQuery对象中返回
```
 // 将自定义的伪数组转换为真数组
var arr = [].slice.call(selector);
// 将真数组转换为伪数组
[].push.apply(this, arr);
// return this;
```
5. 实现传入其他类型将传入的数据存储到jQuery对象中返回
```
this[0] = selector;
this.length = 1;
// return this;
```
### apply和call方法
#### 基本知识
1. apply和call方法的作用:专门用于修改方法内部的this
2. 格式:
+ call(对象, 参数1, 参数2, ...);
+ apply(对象, [数组]);
3. 示例
```
function sum(a, b) {
	console.log(this);
	console.log(a + b);
}
// window.sum.call(obj, 1, 2);
// window.sum.apply(obj, [3, 5]);
/*
1.通过window.sum找到sum方法
2.通过apply(obj)将找到的sum方法内部的this修改为自定义的对象
3.将传入数组中的元素依次取出, 传递给形参
*/
```
#### 真伪数组转换
1. 如果想将伪数组转换为真数组那么可以使用如下方法
``` 
/*如果slice方法什么参数都没有传递, 会将数组中的元素放到一个新的数组中原样返回,而下式中slice方法即没有传参*/
var arr = [].slice.call(obj);
```
2. 如果想将真数组转换为伪数组那么可以使用如下方法
```
 /*
1.通过[].push找到数组中的push方法
2.通过apply(obj)将找到的push方法内部的this修改为自定义的对象
3.将传入数组中的元素依次取出, 传递给形参
*/
[].push.apply(this, arr);
```
### jQuery监听DOM加载
1. onload事件会等到DOM元素加载完毕, 并且还会等到资源也加载完毕才会执行， DOMContentLoaded事件只会等到DOM元素加载完毕就会执行回调，注意DOMContentLoaded事件IE8不支持
2.  document.readyState属性有如下的状态
+ uninitialized - 还未开始载入
+ loading - 载入中
+ interactive - 已加载，文档与用户可以开始交互
+ complete - 载入完成
3. onreadystatechange事件就是专门用于监document.readyState属性的改变的
4. 原生js实现jQuery的ready方法
```
ready: function (fn) {
	// 判断DOM是否加载完毕
	if(document.readyState == "complete"){
		fn();
	}else if(document.addEventListener){
		document.addEventListener("DOMContentLoaded", function () {
			fn();
		});
	}else{
		document.attachEvent("onreadystatechange", function () {
			if(document.readyState == "complete"){
				fn();
			}
		});
	}
}
```
### jQuery原型上的属性和方法
#### 属性与方法列表
1. jquery 获取jQ版本号
2. selector 实例默认的选择器取值
3. length 实例默认的长度
4. push 给实例添加新元素
5. sort 对实例中的元素进行排序
6. splice 按照指定下标指定数量删除元素，也可以替换删除的元素 
7. toArray 把实例转换为数组返回
8. get  获取指定下标的元素，获取的是原生DOM 
9. eq 获取指定下标的元素，获取的是jQuery类型的实例对象
10. first 获取实例中的第一个元素，是jQuery类型的实例对象
11. last 获取实例中的最后一个元素，是jQuery类型的实例对象 
12. each 遍历实例，把遍历到的数据传给回调使用
13. map  遍历实例，把遍历到的数据传给回调使用，然后把回调的返回值收集起来组成一个新的数组返回
#### 原生js实现jquery属性与方法
1. 具体可以参考H:\教学视频\jQuery\jQuery原理\js\njQuery-1.1.0.js
```
// [].push找到数组的push方法
// 冒号前面的push将来由njQuery对象调用
// 相当于 [].push.apply(this);
push: [].push,
sort: [].sort,
splice: [].splice,

toArray: function () {
	return [].slice.call(this);
},

get: function (num) {
	// 没有传递参数
	if(arguments.length === 0){
		return this.toArray();
	}
	// 传递不是负数
	else if(num >= 0){
		return this[num];
	}
	// 传递负数
	else{
		return this[this.length + num];
	}
},

eq: function (num) {
	// 没有传递参数
	if(arguments.length === 0){
		return new njQuery();
	}else{
		return njQuery(this.get(num));
	}
},

 first: function () {
	return this.eq(0);
},
last: function () {
	return this.eq(-1);
},

```
2. 当属性与方法过多时，可以利用对象来进行分类
```
njQuery.extend = njQuery.prototype.extend = function (obj) {
	for(var key in obj){
		this[key] = obj[key];
	}
}

njQuery.extend({
	isString : function(str){
		return typeof str === "string"
	},
	isHTML : function(str){
		return str.charAt(0) === "<" &&
			str.charAt(str.length - 1) === ">" &&
			str.length >= 3;
	}
});
```
#### jquery插件
1. 想要编写jQuery插件，入口可以
```
;(function($,window){
	要编写的代码
})(jQuery,window);
```
2. 如果想分类到extend里
```
;(function ($, window) {
    $.extend({
        addCookie: function (){}
    });
})(jQuery, window);
```
## ajax
### PHP
#### PHP的基础语法
1. 以<?php开头，以?>结尾（可选）
2. 注释同js：//或者/**/
3. 定义变量：$num = 10; 即在变量名前加上美元符号
4. 定义集合：
+ 数组，
```
$arr = array(1, 3, 5);
//数组长度是count（$arr）
//取出数组元素 $arr[$index],如 $arr[$1]
```
+ 对象
```
$obj = array("name"=>"fg","age"=>"23");
```
1. 打印内容：
+ 对于除数组和对象外的数据，直接使用echo，注意如果是打印从数组或对象中取出的某个元素也可以使用echo
```
echo $num;
```
+ 对于数组或对象
```
$arr = array(1, 3, 5);
print_r($arr);
```
6. 循环if/switch/三目/for/while,基本与js相同
#### PHP的运行
1. 运行
+ 注意点: 后端编写的代码不能直接运行, 只能放到服务器对应的文件夹下，通过服务器运行
+ 如何通过服务器运行: 通过ip地址找到服务器对应的文件夹, 然后再找到对应的文件运行，注意默认情况下通过ip地址找到的是www文件夹下的index.php文件，需要将此文件重命名为其他文件名或者删除此文件才可以找到其他文件夹
2. 服务端返回浏览器的是php程序的执行结果
+ 注意: 执行结果中有中文, 必须在php文件顶部设置
header("content-type:text/html; charset=utf-8");
+ 浏览器访问http服务器,接收到响应时,会根据响应报文头的内容进行一些具体的操作,在php中,我们能够使用 header来设置这些内容
3. php中如果需要返回XML或json的数据，并且该数据存储在文件中，可以使用
```
echo file_get_contents("文件地址");
```
### get和post
#### 基本知识
1. 可以通过form标签的method属性指定发送请求的类型
```
//action是提交路径
<form action="02-get-post.php" method="post">
</form>
```
2. 如果是get请求会将提交的数据拼接到URL后面如?userName=lnj&userPwd=123456
3. 如果是post请求会将提交的数据放到请求头中
4. GET请求和POST请求的异同
+ 相同点:
都是将数据提交到远程服务器
+ 不同点:
	+ 提交数据存储的位置不同，
  		+ GET请求会将数据放到URL后面
  		+ POST请求会将数据放到请求头中
	+ 提交数据大小限制不同
		+ GET请求对数据有大小限制
		+ POST请求对数据没有大小限制

5. GET/POST请求应用场景
+ GET请求用于提交非敏感数据和小数据
+ POST请求用于提交敏感数据和大数据
#### 上传文件
1. 上传文件一般使用POST提交，因为大小无限制
2. 上传文件必须在form标签里设置enctype="multipart/form-data"
```
<form action="03-post-file.php" method="post" enctype="multipart/form-data">
	<input type="file" name="upFile">/<br>
	<input type="submit" value="上传"><br>
</form>
```
3. 上传的文件在PHP中可以通过$_FILES获取
```
print_r($_FILES);
/*
输出的是:Array ( [upFile] => Array ( [name] => v2-ff3166fc98e3127127040f0c22be3d91_hd.jpg [type] => image/jpeg [tmp_name] => D:\wamp64\tmp\phpD7C.tmp [error] => 0 [size] => 49168 ) )
通过$_FILES返回的是一个对象，对象里有upFile对象，可以通过这个对象获取名字地址等信息
*/
```
4. PHP中文件默认会上传到一个临时目录, 接收完毕之后会自动删除，如果需要找到该文件则要移动文件
```
// 1.获取上传文件对应的对象
$fileInfo = $_FILES["upFile"];
// 2.获取上传文件的名称
$fileName = $fileInfo["name"];
// 3.获取上传文件保存的临时路径
$filePath = $fileInfo["tmp_name"];
// 4.移动文件
move_uploaded_file($filePath, "./source/".$fileName);
```
5. 默认情况下服务器对上传文件的大小是有限制的, 如果想修改上传文件的限制可以修改php.ini文件
+ file_uploads = On   ; 是否允许上传文件 On/Off 默认是On
+ upload_max_filesize = 2048M       ; 上传文件的最大限制
+ post_max_size = 2048M             ; 通过Post提交的最多数据
+ 
+ max_execution_time = 30000      ; 脚本最长的执行时间 单位为秒
+ max_input_time = 30000          ; 接收提交的数据的时间限制 单位+ 为秒
+ memory_limit = 2048M            ; 最大的内存消耗
### ajax知识
#### 基础
1. AJAX 是与服务器交换数据并更新部分网页的艺术，在不重新加载整个页面的情况下。
2. 如何使用ajax
+ 1.创建一个异步对象
+ 2.设置请求方式和请求地址
	+ method：请求的类型；GET 或 POST
	+ url：文件在服务器上的位置
	+ async：true（异步）或 false（同步）,ajax永远为true
+ 3.发送请求
+ 4.监听状态的变化
	+ 0: 请求未初始化
	+ 1: 服务器连接已建立
	+ 2: 请求已接收
	+ 3: 请求处理中
	+ 4: 请求已完成，且响应已就绪
+ 5.处理返回的结果
```
// 基础版ajax使用
	var xmlhttp=new XMLHttpRequest();
	xmlhttp.open("GET", "04-ajax-get.php", true);
	xmlhttp.send();
	xmlhttp.onreadystatechange = function (ev2) {
		if(xmlhttp.readyState === 4){
			// 判断是否请求成功
			if(xmlhttp.status >= 200 && xmlhttp.status < 300 ||xmlhttp.status === 304){
				// 5.处理返回的结果
				console.log("接收到服务器返回的数据");
			}else{
				console.log("没有接收到服务器返回的数据");
			}

		}
	}

// 进阶版ajax使用
var xhr;
if (window.XMLHttpRequest)
{//兼容 code for IE7+, Firefox, Chrome, Opera, Safari
	xhr=new XMLHttpRequest();
}
else
{// 兼容code for IE6, IE5
	xhr=new ActiveXObject("Microsoft.XMLHTTP");
}
/*
在IE浏览器中, 如果通过Ajax发送GET请求, 那么IE浏览器认为
同一个URL只有一个结果
*/
xhr.open("GET","05-ajax-get.txt?t="+(new Date().getTime()),true);
xhr.send();
xhr.onreadystatechange = function (ev2) {
	if(xhr.readyState === 4){
		if(xhr.status >= 200 && xhr.status < 300 ||
		xhr.status === 304){
			/*需要获得来自服务器的响应，请使用 XMLHttpRequest 对象的 responseText 或 responseXML 属性。*/
			alert(xhr.responseText);
		}else{
			alert("请求失败");
		}
	}
}

```
3. 注意在IE浏览器中, 如果通过Ajax发送GET请求, 那么IE浏览器认为
同一个URL只有一个结果，所以为了避免冲突，URL后加上？t=xxxx，所获取的网页相同
4. 获取不同的数字的两种方式
+ Math.random()
+ new Date().getTime()
1. 在URL中是不可以出现中文的, 如果出现了中文需要转码，可以调用encodeURIComponent方法，URL中只可以出现字母/数字/下划线/ASCII码
#### 自己封装的ajax
可查看D:\wamp64\www\Ajax\myAjax.js或者D:\wamp64\www\Ajax\myAjax2.js
#### xml
1. 如果PHP中需要返回XML数据, 也必须在PHP文件顶部设置
```
header("content-type:text/xml; charset=utf-8");
```
2. 如果PHP中返回的是XML数据，则在js里调用自己封装的ajax函数或者直接使用ajax时，需要注意获取的是xhr.responseXML，而不是 xhr.responseText
#### json
1. json文件可以使用txt后缀名
2. json写法类似对象
3. json转对象使用JSON.parse(json数据)，但需要注意在低版本的IE中, 不可以使用原生的JSON.parse方法, 但是可以使用json2.js这个框架来兼容
4. 对象转json使用JSON.stringify(js对象)
5. 如果PHP中返回的是JSON数据，则在js里调用自己封装的ajax函数或者直接使用ajax时，需要注意获取的是 xhr.responseText，获取到json数据后，需要转成js对象，再对该对象进行操作
6. 如果后端返回的是一个非标准的json字符串，但是需要把它转换成标准的json字符串，可以使用eval（）将非标准json字符串作为参数传进去，但是需要注意要在非标准字符串两端加上小括号
```
//这是一个非标准字符串转成标准json字符串
var msg = "{error: 0, id: 4, time: 1570609574, acc: 0, ref: 0}";
var obj = eval("("+msg+")");//注意这个小括号
```
#### cookie
1. cookie: 会话跟踪技术 客户端,session:  会话跟踪技术  服务端
2. cookie作用:将网页中的数据保存到浏览器中
3. cookie生命周期:
+ 默认情况下生命周期是一次会话(浏览器被关闭)
+ 如果通过expires=设置了过期时间, 并且过期时间没有过期, 那么下次打开浏览器还是存在
+ 如果通过expires=设置了过期时间, 并且过期时间已经过期了,那么会立即删除保存的数据
4. cookie注意点:
+ cookie默认不会保存任何的数据
+ cookie不能一次性保存多条数据, 要想保存多条数据,只能一条一条的设置
+ cookie有大小和个数的限制
	+ 个数限制: 20~50
	+ 大小限制: 4KB左右
5. cookie作用范围:
+ 同一个浏览器的同一个路径下访问
+ 如果在同一个浏览器中, 默认情况下下一级路径就可以访问
+ 如果在同一个浏览器中, 想让上一级目录也能访问保存的cookie, 那么需要添加一个path属性才可以;
```
document.cookie = "name=zs;path=/;";
```
+ URL相同但是域名不同的也无法访问，如果想要访问需要添加domain属性才可以
```
/*例如:
我们在www.it666.com下面保存了一个cookie,
那么我们在edu.it666.com中是无法访问的
如果想在edu.it666.com中也能访问, 那么我们需要再添加一个domain属性才可以;*/

document.cookie = "name=zs;path=/;domain=it666.com;";
```
6. 设置或访问cookie可以直接通过ocument.cookie,注意设置cookie信息的格式要以键值对
```
alert(document.cookie);
document.cookie = "name=lnj;age=33;gender=male;";
```
7. 有关cookie操作的封装在D:\wamp64\www\Ajax\16-cookie-封装.html
+ window.location.pathname可设置或返回当前 URL 的路径部分，例如
在http://127.0.0.1/Ajax/16-cookie-%e5%b0%81%e8%a3%85.html中返回/Ajax/16-cookie-%e5%b0%81%e8%a3%85.html

8. 查看cookie：在谷歌浏览器控制台Application,在找到cookie，点开后选择想要查看的地址
9. cookie的弊端：只能在本地使用
#### hash
1. hash即URL中"#"字符后面的部分。
2. hash值的改变不会导致页面重新加载。
3. 通过window.location.hash属性获取和设置hash值。

## 其他
### 在微博小案例中想让浏览器记住当前页码
#### 使用cookie
1. 先导入自己写的cookie插件，里面封装了增加cookie，获取cookie，删除cookie的方法
2. 在监听页码点击的时候，增加一条cookie，以保存当前点击的页码
```
 $.addCookie("pageNumber",$(this).html());
```
3. 设置获取页面时需要传入的参数为number，而number则为cookie存储的页码
```
var number = $.getCookie("pageNumber") || 1;
 getMsgList(number);
 function getMsgList(number){
        $(".messageList").html("");
        $.ajax ({
            type:"get",
            url:"weibo.php",
            data:"act=get&page="+number,
            success:function(msg){
                var obj = eval("("+msg+")");
                $.each(obj,function(key,value){
                      // 根据内容创建节点
                var $weibo = createEle(value);
                $weibo.get(0).obj = value;
                // 插入微博
                $(".messageList").append($weibo);
                })
            },
            error:function(xhr){
                alert(xhr.status);
            }
        })
    }
```
#### 使用hash
1. 设置hash为当前页码
```
window.location.hash = $(this).html();
```
2. 设置获取页面时需要传入的参数为number，而number则为hash存储的页码
```
//因为默认情况下取得的hash为#number，所以只取number如下
var number = window.location.hash.substring(1) || 1;
```
