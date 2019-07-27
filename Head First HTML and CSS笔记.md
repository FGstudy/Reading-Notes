
1、元素=开始标记+内容+结束标记
2、向上链接到父文件夹（以当前页面所在文件位置为基准）里的文件时 <a href="../文件名.html"></a>
3、<q></q>表短引用，作为现有段落的一部分，可以给引用内容加上双引号
4、<blockquote></blockquote>表示长引用，又叫块引用，会单独显示，有段落效果（行距和缩进）不带双引号
5、<em></em>使内容变成斜体字，标记重点强调的文本
6、块block元素和内联inline元素
块元素：<h1></h1> 、 <h2></h2>....<h6></h6>、 <p></p>、 <blockquote></blockquote>、<ol></ol>、<ul></ul>
		特点:都单独显示，前后都有换行（浏览器自动插入换行符），将内容分块显示
		块元素通常作为web页面中的主要构建模块
内联元素：<q></q>、<a></a>、<em></em>、<li></li>
		特点：显示在所在的段落中
		内联元素旺旺用来标记小段内容
设计页面时，一般先从块元素开始，完善页面时再加入内联元素
7、设计为没有任何内容的元素成为void元素，需要使用void元素时，如<br /> <img />只需要使用一个开始标记
8、列表：第一步，将每个列表项放在一个<li></li>元素中，这个是内联元素
第二步，用<ol></ol>(有序)或者<ul></ul>(无序)包围列表项，这个是块元素
9、特殊字符>----&gt;   <----&lt;  &----&amp;  空格----&nbsp;		
10、<strong></strong>标记特别强调的文本，默认效果为加粗（同<b></b>效果）
11、小知识：物理标签和逻辑标签---<strong></strong>和<b></b>、<em></em>和<i></i>这两对的区别
(1)<strong></strong>和<b></b>：这两个标签显示的效果都是加粗，
而区别就在于<b></b>是一个实体标签，它所包围的字符将被设为bold（粗体），而<strong>标签是一个逻辑标签，它的作用是加强字符的语气，一般来说，
加强字符的语气是通过将字符变为bold（粗体）来实现的。<strong></strong>标签可以通过css改变样式比如字体红色、夹下划线等达到强调的目的。
从网站优化方面分析，最主要的区别应该是<strong> </strong>内的内容比起<b></b>的内容应该更容易被网络蜘蛛抓取，也就是更容易使网站被用户搜索到，
一些语音阅读器也会根据它在阅读时加强语气。
(2)<em></em>和<i></i>的效果都显示斜体，道理同上，<i></i>仅仅表示字体是斜体，<em></em>则表示强调，通过字体变为斜体体现
(3)<strong></strong>和<em></em>相比，<strong> 标签和 <em> 标签一样，用于强调文本，但它强调的程度更强一些。
(4)由上，物理元素所强调的是一种物理行为，只是告诉浏览器该怎么显示，没有什么实际含义，
逻辑元素，他强调文档逻辑，告诉浏览器这些文字有怎么样的重要性。
12、<a title=""></a> 超链接标签里面有个title属性，效果是鼠标放上去的时候有显示这个文字信息，
更重要的是对视力障碍者使用屏幕阅读器时会读出来，而不是一个字一个字的读网址，
建议title属性值和链接到的web页面的title元素值相同
链接使用技巧：简洁、有意义、不要把链接放在一起
13、<a herf="#id名或者name名"></a> 可以链接到某个点
无论是绝对路径还是相对路径，要链接到一个页面上的特定目标，只需要要在链接最后加上#，再加山个目标标识符
14、使用target打开新窗口，<a target="_blank" href=""></a>此时浏览器会打开一个新窗口显示页面
15、<img src="url或相对路径" / > void元素标签，提供了一个途径，可以通过它指定在页面上显示的图像的位置
注意：<img />指向图像，二图像并不是HTML的一部分，HTML页面是纯文本，而图像是单独存在的
16、<img  alt="描述图像的文字"/>的alt属性：如果图像不能显示(一般是路径错误)，就显示这个文本，这是img的必要属性
17、HTML5：活的，会不断改变会发展的HTML标准，是HTML最后一个版本
向后兼容性：可以继续向HTML增加新的内容，浏览器会支持新的内容，也会支持原有的内容
18、<meta charset="utf-8">:告诉浏览器关于页面的一些信息,biru zifuji 
要放到<head>元素中所有元素之上

二、css部分

19、css文件里没有style标签，如果将css写到外部文件上，HTML文件里就不用写style标签，
而是<link rel="stylesheet"  href="css文件路径"/>（link是个void元素）

20、没怎么用过的css属性
letter-spacing:字母间距
line-height:行间距
list-style：列表中列表的外观
font-family:字体系列,其实就是个字体优先列表
			有5个字体系列，
			sans-serif,没有衬线（字母末端用来装饰的小细线）的字体，比serif在屏幕上更容易识读，包含Verdana、Arialblack、trebuchet、 MS Arial、Geneva等
			serif,有衬线的字体，包括times、times new roman、georgia等
			monospace,固定宽度的字符（i和m占的宽度一样）一般用来显示软件代码，包括：courier、courier new，andale mono等
			cursive,看似手写的字体，会在标题中使用，包括comic sans、apple chancery等
			fantasy，某种风格的装饰字体，包括last ninja、impact等
			建议：font-family的值包括一个候选字体列表（2-4）种字体，通常都来自同一个系列，最后放一个通用的字体系列名称（就serif这些）
			输入多个字体名时用逗号隔开，浏览器会优先从第一个字体开始,如果字体名称包含多个单词，只要在字体名两边加上引号
			另外，还可以自定义字体，
font-size：字体大小，
			px:按像素指定字体大小,px要紧跟像素数后面不能有空格，用px指的是字母的高度（单词中的字母最高部分和最低部分的差距）
			%：按百分比指定字体大小，百分比是相对于父元素的字体而言
			em:按相对比例指定字体大小，，例如font-size：1.2em 就是指是父元素字体大小的1.2倍
			关键字：如small、medium、large等
			建议：选择一个关键字指定body的字体大小（small或medium），使用em或百分数指定其他
			理由：想整体放大或缩小时只需要修改body的就行了，还有利于用户调整字体大小
			小知识：标题的默认大小，
			<h1></h1>默认body的200%
			<h2></h2>默认body的150%
			<h3></h3>默认body的120%
			<h4></h4>默认body的100%
			<h5></h5>默认body的90%
			<h6></h6>默认body的60%
color：
		web颜色是按构成颜色的红绿蓝三个颜色所占数量指定，每种颜色指定一个从0到100%的数值
		混合起来得到最终的颜色
		css指定颜色的方法：
		颜色名，
		十六进制码：以#开头，一共6个数字，每组2位数字分别表示红绿蓝分量
		rgb取色：有两种方式，一种按百分比，例如background-color：rgb(80%,40%,10%),分别对应红绿蓝的百分比    
			一种按数值，例如background-color：rgb(204,102,0),分别对应红绿蓝的数值，红绿蓝数值范围0-255，204=255*80%
font-weight:字体粗细
			bold
			normal:当元素默认设置为bold或者从父元素继承了粗体时，可以去掉粗体样式
			bolder
			lighter
text-decoration：给文本增加装饰，值有none，underlying（下划线）overline line-through（删除线）
21、内置css规则：
			@font-face：可以获取一个web字体
			@important：允许导入其它css文件
			@media：允许创建特定于某些媒体类型的css规则，如印刷页、桌面屏幕、手机等
22、调整行高：line-height属性，类似字体大小属性，可以按像素、em、百分比来指定
23、盒模型：从css的角度看，所有元素都可以看成是一个盒子，每个盒子包括内容区、内边距、边框、外边距
	内容区：存放内容，盒子的大小正好包含所有内容，在内容区，内容和盒子边缘之间没有空间，
	常用属性--line-height,font-style,font-family,color,background-color,background-image
	内边距：内容和边框之间，通过css可以控制上下左右内边距的宽度，内边距在内容周围增加额外的空间
	常用属性--padding
	边框：边框包围内边距，他是围绕内容的一条线，可以有不同的宽度颜色和样式
	常用属性--border-color,border-width,border-style,border-radius
	外边距：包围着边框，利用外边距可以在同一个页面上的不同元素之间增加空间，提供元素之间的间距
	常用属性--margin

	注意1：内边距和外边距都用来提供更多可见的空间，不能给内边距和外边距指定颜色，也不能加装饰，但由于他们是
		透明的，他们会呈现背景颜色或背景图片，注意背景颜色或图片会延申到内边距下面，不会延申到外边距
	注意2：background-image一般写法，例如：background-image：url(img/1.jpg);   
		它会受background-position和background-repeat的影响
		其中background-position设置图像位置，可以按像素、百分数、关键字（top、left、right等）指定
		background-repeat控制图像的平铺，值为no-repeat时图像显示一次，不重复，repeat-x图像只在水平方向上重复
		值为repeat-y在垂直方向上重复，值为inherit按父元素的设置来处理，值为repeat在水平和垂直方向重复这也是默认行为
	注意3：border-style：控制边框样式，有8种样式solid(实线)dotted(虚线)dashed(破折线)double(双线)
			groove(槽线)outset(外凸)inset(内凹)ridge(脊线)
	注意4：border-radius控制边框角弧度，可以对四个角单独设置
	注意5：边框不继承
24、类与id的命名：类名要以一个字母开头，可以包含字母、数字或_字符。但不能有空格
				id名可以以一个数字或字母开头，可以包含字母、数字、和_字符，但不能有空格
25、使用多个样式表，在HTML文件里可以链接多个样式表，但是顺序很重要，后面的会覆盖前面的
26、在<link />元素里可以增加属性media ，例如：<link href="css/1.css" rel="stylesheet" media="screen and (max-device-width:480px)" >
	media属性指定应用这个样式表的设备类型，通过创建一个媒体查询来指定设备类型，媒体查询要与设备匹配，上例中查询了有屏幕的设备并且屏幕宽度不超过480像素
	媒体查询中有很多属性可以用如min-device-width,max-device-width,orientation(显示方向，可以是横向或纵向),
27、要为css指定特有属性的设备，另一种方法是写在css里，使用css的内置规则@media，
	例如@media screen and (max-device-width:480px){ #test {margin:50px},
	格式：@media 媒体查询{css属性设置}
28、<div></div>允许你为块级内容创建逻辑划分，将页面划分为逻辑区或逻辑分组，逻辑区就是页面上彼此相关的一组元素。创建逻辑区有助于标识主内容区和页眉页脚
		它不仅相当于逻辑容器，可以将相关元素放在一起，还相当于图形容器。它是纯粹的结构，在页面中没有默认外观或样式但可以对它指定样式
		div中的width属性指的是内容区的宽度，如果使用百分数来指定，则为元素所在容器宽度的一个百分比，
		而整个盒子的宽度=左右内边距+左右外边距+左右边框+内容区宽度
		注意1：text-align会对块元素中所有内联内容对齐，但这个属性只能在块元素上使用，不能在内联元素上使用
		另外，text-align对<div>中的块元素起作用是因为这些块元素继承了<div>的这个属性
		注意2：line-height属性可以对它直接设置一个数字，例如line-height：1；表示<div></div>中各个元素的行高是自己字体大小的1倍
		注意3：属性简写，如内边距padding-top：0px;padding-right：20px;padding-bottom：20px;padding-left：10px;
		可以简写为padding：0px 20px 20px 10px;，如果上和下相等，左和右相等：padding：0px 20px；如果四个值相同时，padding：20px;
		外边距同理
		border和background类似，顺序任意。如border-width：thin;border-style:solid;border-color:red;可以写成border:thin solid red;
		background-color:white;background-image:url(img/1.jpg);background-repeat:repeat-x;可以写成background：white url(img/1.jpg) repeat-x;
		需要特别留意的是字体的简写，字体的所有属性 font-family、font-size、font-style、font-weight、font-variant、line-height等，简写时格式
		font：font-style font-variant font-weight font-size/line-height font-family
		其中前三个是可选的，必须出现在font-size的前面，font-size必须出现，
		line-height可选，但如果出现要在font-size后面加/，最后要有字体系列（字体名称用逗号隔开）
29、<span></span>采取于<div></div>类似的方式建立内联内容的逻辑分组
30、标记使用的原则:使用与内容含义最接近的元素来标记内容
31、对内联元素的属性操作注意：可以设置内联元素的宽度、外边距、内边距、边框
（1）可能注意不到宽度的改变
（2）与块元素不同，内联元素四周都增加外边距，只能看到左右两边增加空间
（3）内联元素的上下内边距不会影响包围它的其他内联元素的间距，内边距会与其他内联元素重叠
（4）图像表现更象块元素
32、对链接指定样式,a:状态
	a:link{color:green;}应用于未访问状态的链接
	a:visited{color:red;}应用于已访问的链接
	a:hover{color:yellow;}应用于悬停在链接上时
	a:focus{color:blue;}应用于焦点放在链接上时，就是按键盘来访问链接
	a:active{color:blue;}链接被点击的时刻
33、伪类：用于当已有元素处于的某个状态时，为其添加对应的样式，即根据元素的状态指定元素的样式，这个状态是根据用户行为而动态变化的
	允许你根据浏览器的决定（确定元素属于哪些”类“）来指定这些元素的样式，如link和first-child
	可以根据访问者使用页面时发生的情况对元素指定样式，如hover
34、计算选择器特定性（优先级），从三个数字000开始，如果选择器包含id，第一个0+1分
	选择器包含类或伪类，第二个数字+1分，选择器包含元素，第三个数字+1分
	注意如果是h1,h2要拆成两个 每个得分是001.分最高的优先级最高
35、浏览器并排放置两个内联元素时，如果他们都有外边距，浏览器会在元素之间创建足够的空间
	例如，左边的元素外边距20px,右边的元素外边距10px，则这两个元素之间有30px间距
36、浏览器上下放置两个块元素时，它会将它们共同的外边距折叠在一起，折叠的外边距高度就是最大的外边距高度，即它们共同的外边距是两个外边距中较大的那个外边距
37、只要两个垂直外边距碰到一起，他们就会折叠，即使是一个元素嵌套在另一个元素中也不例外，但是如果外面的元素有一个边框，那么两个元素的外边距就不会碰到一起，也就不会折叠
38、流是浏览器在页面上摆放HTML元素所用的方法，它从HTML文件最上面开始，从上到下沿着元素流逐个显示所遇到的各个元素
	文本虽然不是元素，但是因为要让他流入页面，要确定一行能流入多少，所以当作内联元素
	块元素从上向下流，各元素之间有一个换行，默认每个块元素会占浏览器窗口的整个宽度
	内联元素在块元素内部从左上方流向右下方，如果需要多行，浏览器会换行，在垂直方向上扩张外围块元素，来包含这些内联元素
	
39、浮动：对于所有的浮动元素都必须有一个宽度。
		对于一个块元素，即使宽度调整后，旁边留出很大的空白区域，也不会有元素上移到它旁边，因为块元素前后有换行
		如果想让其他元素上移上来，那就可以对这个块元素设置float属性，例如float：right；
		当浏览器遇到这个浮动元素的时候，会把它尽可能放最右边，还会从流中删除这个段落，就好像它浮在页面上一样
		由于这个浮动段落已经从正常的流里删除，所以其他元素全都填在这里，好像没有这个段落一样
		注意，此时这些其他元素是在浮动元素的下方（是立体的三维的下方）
		不过对内联元素定位时，他们会考虑浮动元素的边界，因此会围绕着浮动元素
	嵌套在块元素中的内联元素围绕着浮动元素，内联元素会注意浮动元素的边界，而块元素则正常流向页面（当设置了clear时例外）
40、两栏式布局，尽量不要浮动主内容区，因为浮动需要设置宽度，而当主内容区固定宽度后，
	如果浏览器窗口大小改变，而主内容宽度不变，页面的其他部分随着窗口改变时，页面看起来比较糟糕
	但是，另一方面，不浮动主内容区有一个缺陷，浮动另一个块元素，需要将浮动元素的HTML代码移动到主内容区HTML代码上面，
	如果用户用小屏的浏览器如手机等，页面太窄无法显示分栏，就会按代码顺序显示，这违背我们原来的设计
41、设置浮动后，如果页面显示该元素和浮动上来的块元素中间的间距过小，可以将上移的元素的外边距（与浮动元素贴着的那边或左或右）设置为浮动元素的宽度
42、clear:right;右边不允许有浮动内容，当浮动元素与下面的元素重叠时，而又不需要重叠时，可以使用这个元素
	一般当上移上来的元素高度小于浮动元素高度时可能发生这种情况
43、流体布局和冻结布局
	流体布局：扩展浏览器窗口时，页面中的内容也会扩展以适应页面
	冻结布局：内容的宽度是固定的，不会随着浏览器窗口扩展或收缩
		在流体布局时，无论浏览器怎么调整，布局都会相应扩展或缩小，直到填满整个浏览器，但这可能会使布局设计变样
		所以需要冻结布局，冻结布局会锁定元素，让它们冻结在页面上，就算用户调整屏幕大小，设计仍能保持原样
		冻结操作：增加一个div，包围需要冻结的区域，再给这个div设置固定的宽度，最好再加一点内外边距
		效果：冻结成功，但是因为宽度固定，当窗口变大时，右边会有很大空白
44、针对冻结的缺陷，有一种凝胶布局（介于冻结和流体之间）：内容宽度固定，外边距会随着浏览器窗口扩展或收缩
	凝胶布局会锁定页面中内容区的宽度，不过会将它在浏览器中居中
	操作：在冻结的基础上，增加两个属性左右外边距并将值设为auto即 margin-left:auto;margin-right:auto;
	原因：外边距为auto时，浏览器会确定正确的外边距是多少，还会确保左右外边距相同，所以居中
45、绝对定位：创建两栏布局的常用技术，可以让内容保持正确的顺序，同时避免流体布局存在的问题
一般需要设置position属性值为absolute，还要设置与页面的距离，以及元素宽度（非必须，但是不指定的话，块元素会占浏览器的整个宽度）
例如：#sidebar{
	position:absolute; 		/*指定这个元素要绝对定位*/
	top:100px;				/*距页面上边100px*/
	right:200px;			/*距页面右边200px*/
	width:280px;
}
一个元素绝对定位时，浏览器会将它从流中完全删除，再把这个元素放再top和right属性指定的位置上（也可以用bottom和left指定）
流中的元素不会知道这个绝对定位的元素的存在，包括内联元素也不会围绕它，而是无视他
46、绝对定位的分层，一个元素可以放再另一个绝对定位元素的上面，如果页面上同一个位置有多喝绝对定位元素，就会分层
而每个定位元素都有一个名为z-index的属性，指定它在一个虚拟z轴行的位置，z-index的值越大，定位元素位置越上
47、可以对任何元素指定绝对定位，包括块元素和内联元素。例如指定<img>元素的位置
48、position属性有四个值：static、absolute、fixed、relative,
	其中static表示静态定位（也是默认值），元素会放在正常的文档流中，由浏览器来指定元素位置
	absolute表示绝对定位，将元素完全从页面流中取出，允许你为它指定一个绝对位置，这是相对于离他最近的父元素指定（一般是<html>)
	fixed表示固定定位，将元素放在相对于浏览器窗口的一个位置上（而不是相对于页面），固定元素永远也不会移动
	relative表示相对定位，相对于它外围包含元素来定位，它会让元素正常流入页面，不过在页面上显示之前要进行偏移，一般用于特殊效果
49、用了绝对定位，即使产生主内容区覆盖页脚的问题，也不能像流布局一样采用clear属性了，因为流元素完全不知道绝对定位元素的存在
50、css表格：每个单元格中放置一个块元素（注意，因为只放块元素，所以如果一个单元格里只有图像的话，要把图像包围在<div></div>)
	操作：
	先使用HTML增加结构，首先创建一个<div></div>表示整个表格，行和列要嵌套在这个div中，接下来，对于表格中的每一个行要创建一个div，包含行内容，
	然后对于每一列，只需要一个块元素作为该列内容
	用css指定元素属性：首先为表格增加的div设置id为"tableContainer",这个div包含行和列，
	样式如：div#tableContainer{display:table;}
	接着，行div的id可以设为tableRow,(多个行则需要多个div,考虑设置类，这样可以一个规则指定所有行的样式)，
	样式如下：div#tableRow{display:table-row;}
	最后，使用现有的div作为单元格，对应于行中的各列，
	样式：#main{display：table-cell;}
	注意1：在表格布局中，使用border-spacing作为表格中的单元格上的外边距，而不是使用原来的div的外边距
	注意2：需要增加一个属性vertical-align：top，确保表格两个单元格的所有内容相对于单元格上边对齐
	注意3：border-spacing和其他元素外边距创建的空间不会折叠
51、css表格与HTML表格
	联系：他们都是在HTML中创建一种结构，能够映射到表格的行和列
	区别：css表格显示知识使用一种类似表格的布局来表现这个结构中的内容，HTML表格面向的是表格数据，也就是说，css表格只是创建某种表现布局的方法，而HTML表格则是建立数据的结构
52、需要一个元素出现在页面中某个精确的位置上----选择绝对定位
53、z-index：元素在虚拟z轴上的顺序属性，只有使用css绝对定位、相对定位、固定定位的元素有z-index


54、HTML5新元素
<header></header>:放在页面顶部的内容，或者放在页面某个区块的顶部
<footer></footer> ：放在页面底部的内容，或者放在页面某个区块的底部
<aside></aside>：包含的内容是对页面内容的补充，如插图或边栏
<article></article> ：表示页面中一个独立的组成部分，如一个博客帖子、新闻报道等
<section></section> ：一个主题性内容分组，把相关的内容分组在一起
<nav></nav>：所包含的内容将作为页面的导航链接
<time></time>：包含一个日期或时间，也可能同时包含日期和时间
<video></video>:用来为页面增加视频媒体
<progress></progress>显示任务完成的进度
<mark></mark>用来突出显示某些文本
<canvas></canvas>用来在页面中显示用JavaScript绘制的图像和动画
55、section、article、div的区别
通用性：div>section>artcile
div：只是要增加一个元素以便为页面指定样式
section：要增加一个元素来标记一些内容，指示这是由相关内容构成的一个结构明显的区块
article：有些内容可以独立于页面上的其他内容进行重用和分发
56、一般section和article会有一个header或者有个标题
57、即使只放一个标题时也可以使用header，因为header元素能提供额外的语义含义，可以将页面、区块、或文章的首部和其余的内容区分开
58、导航：HTML里需要用到列表和一些锚标记，用<nav></nav>包围
css里要注意在列表的属性里删除列表符号：list-style-type：none；在列表项的属性里设置display：inline；这样这些列表项前后不会有回撤，而是像常规内联元素一样在页面上流入一行
59、<video controls autoplay width="512" height="288" src="video/myvide.mp4"></video> 
上例中autoplay控制视频自动播放，如果没有，用户需点击才能播放；controls属性会提供一组控件，一般包括播放、暂停、调节音量按钮，这两个属性是布尔属性，没有值，
src属性类似于<img>的src，告诉video元素在哪里查找源文件，
preload属性用于细粒度控制视频如何加载，值为none时在用户播放视频之前不下载视频，值为metadata时下载视频元数据，但是不下载视频内容设置为auto时，浏览器决定
width属性和height属性设置视频显示区（视窗）的宽度和高度，如果有海报，海报也会按这个宽高
poster属性会把视频的一帧显示为海报图像来表示这个视频，默认显示视频的第一帧，想显示特定图像，需指定
loop属性也是布尔属性，有loop属性，视频结束播放之后会自动重新开始播放视频
60、因为视频编码格式多样，浏览器不是全都支持，当需要提供多种视频格式时，<video></video>元素里原来的src属性删除，在里面对应每种格式使用一个<source>元素
例如
<video controls autoplay width="512" height="288" >
	<source src="video/1.mp4" >
	<source src="video/2.webm" >
	<source src="video/3.ogv" >
</video> 

61、HTML表格,格式如下
<table>  /*使用table标记开始这个表格*/
	<tr>   /*表行标记*/
		<th>表头内容</th>  /*表头标记，标记表头的一个单元格，必须放在表行里*/
		<th>表头内容</th>
		<th>表头内容</th>
	</tr>
	<tr>
		<td>表格内容</td>  /*单元格标记，必须放在表行里*/
		<td>表格内容</td>
		<td>表格内容</td>
	</tr>
	<tr>
		<td>表格内容</td>
		<td>表格内容</td>
		<td>表格内容</td>
	</tr>
</table>
表格由行中的数据单元格组成，表格中的列数就是行中数据单元格的个数，
<caption>表格标题</caption>：显示表格标题，默认在表格上方显示。
表格类似盒子模型，有内边距，边框，单元格内容区，但是没有外边距，相应的有边框间距border-spacing
border-spacing这个属性是针对整个表格定义的，不能单独设置各个表格单元格的边框间距，而是为所有单元格设置一个共同的间距
border-collapse：collapse：折叠边框，使单元格之间没有边框间距
注意1：即使单元格内容为空，也要列出所有数据单元格也就是<td></td>,如果省略，表格就不能正确的排列对齐
注意2：数据单元格需要跨多行或多列，可以使用<td></td>元素的rowspan或colspan属性
62、nth-child伪类，状态是一个元素相对于它的兄弟元素的数字顺序，
使用：元素名：nth-child(值){想设定的属性：属性值；}
 nth-child的值可以是even（偶数），odd（奇数），也可以是2n,2n+1等n的表达式
63、为列表ul ol li增加样式,使用list-style-type属性，
该属性的值有disc默认的圆点，值是circle显示简单的圆形标志，值为square显示方块标志，值为none显示没有标志
定制标志可以使用list-style-image属性，值为URL，例如list-style-image：url(img/1.gif);
64、表单：一个包含输入域的web页面，允许用户输入信息，提交表单时，这些信息会打包发送到服务器，由服务器脚本处理，处理完成后返回一个web页面
<form action="http://baidu.com/hfhtmlcss/contest.php" method="post"></form>
在上例中，action属性包含web服务器的URL/脚本所在文件夹/处理表单数据的服务器脚本文件名
method属性确定表单数据如何发送到服务器
65、常见表单元素
input元素的一个void元素，它后面没有内容
大多数表单元素都需要name，服务器脚本将使用它
<input type="text" name="" />type=text的input元素会在浏览器页面中创建一个单行控件
<input type="submit" name="" />type=submit的input元素默认效果是提交按钮
<input type="radio" name="yorn" value="y"/>
<input type="radio" name="yorn" value="n"/>type=radio的input元素会创建包含多个按钮的控件，但是一次只能选一个按钮，也就是单选按钮，每一组单选按钮必须有相同的name值，value不同
<input type="checkbox" name="laugh" value="hehe"/>
<input type="checkbox" name="laugh" value="heihei"/>
<input type="checkbox" name="laugh" value="haha"/>type=checkbox的input元素创建一个复选框按钮，可以选中也可以不选中，相关的复选框也共用一个name，value不同
<input type="button" name="" value="" />按钮
<input type="file" name="" value="" />文件，使用这个元素的前提是必须使用post方法
<input type="hidden" name="" value="" />隐藏
<input type="password" name="" value="" />密码
<input type="reset" name="" value="" />重置
<textarea name="comments" rows="10" cols="48"></textarea>创建一个多行的文本区，输入的文本放不下，右边还会有滚动条，rows告诉浏览器文本区高度为多少字符，cols告诉浏览器文本区宽度为多少字符，
也可以用css指定文本区的宽度和高度，开始和结束标记之间的所有文本会成为浏览器文本区控件的初始文本
<select name="">
	<option value="">11</option>
	<option value="">22</option>
	<option value="">33</option>
	<option value="">44</option>
</select>
select创建一个可下拉的菜单，要与option结合使用，option表示菜单项，每个菜单选项还可以包含一个表示这个菜单项的值
select元素增加布尔属性multiple，会将下拉的单选菜单变成一个多选菜单，选择时同时按Ctrl键可以选择多个选项
66、HTML5表单元素
<input type="number" min="0" max="10" /> 限制只能输入数字，甚至可以用可选的属性min/max指定这个元素的最大最大值
<input type="range" min="0" max="10" step="2" />类似number，只是它会显示一个滑动条，而不是一个输入框，step属性指定值的间隔数（number也可以用）
<input type="color" /> 指定颜色，点这个按钮会弹出颜色选择器
<input type="date" /> 指定日期，点这个按钮会弹出颜色选择器
<input type="email" /> 方便输入email的文本输入框
<input type="tel" /> 方便输入电话的文本输入框
<input type="url" /> 方便输入url的文本输入框
注意1：name属性，表单中的每个输入控件都有一个name属性，浏览器会将name属性值作为数据的标签，发送到服务器
注意2：输入只有一行的文本，如姓名或邮政编码，用<input type="text"  />；更多行的用<textarea></textarea>
注意3：input使用maxlength属性可以限制用户输入的字符数，但是textarea没有限制
注意4：如果为单选按钮输入元素增加一个布尔属性checked，浏览器显示表单时就会默认选中这个元素，
注意5：使用表单的组件不一定要定义form标签，需要将数据提交到服务器端才需要
注意6：单选框或复选框的每个控件的id必须唯一
67、get和post区别与联系，
联系：post和get都是讲表单数据从浏览器发送到服务器端
区别：get提交的数据会显示在地址栏，post不会；
get提交的数据受地址栏的限制，post不会
get对于敏感信息不安全，post不会
get会将提交信息封装在请求行，post封装在数据体
对服务器端而言，表单提交尽量用post，因为涉及到编码问题，
68、label元素：可以提供页面结构更多信息，更容易使用css对标签设置样式，对于有视力障碍的人，也有助于屏幕阅读器更准确的标识表单元素
使用：先为表单元素增加一个id属性，然后增加一个<label for="id值"></label>，设置它的for属性值为相应的id
注意：label可以放再与他关联的控件的前面或后面，只要for属性值与id匹配，label位置随意
69、input元素中的placeholder属性：为用户提供提示，使其了解这一部分需要什么内容
这个属性的值会显示在控件中，但是颜色要浅一点，一旦点击这个文本域，占位文本会消失，即使这个域为空就提交表单，占位内容也不会作为控件值提交
70、任何表单控件中都可以使用required属性，它显示这个域是必要的，如果这个控件没有值就无法正常提交表单
required属性是布尔属性，它没有值，也就是说如果有这个属性，说明设置了这个属性，反之
71、伪元素可以用来选择元素的某些部分，这些部分可能不便于包围在div或者span里，也不方便用其他方法来选择
例如first-letter伪元素用来选择一个块元素中文本的第一个字母，这样就可以做首字母大写/首字母下沉效果
first-line伪元素是用来选择段落的第一行
示例：p:first-letter{color:red;}  /*第一个字是红色*/  
示例：p:first-line{color:red;}  /*第一行是红色*/  
72、属性选择器，根据属性值来选择元素
		示例：img[width]{border:black thin;}/*这个选择会选择HTML中所有包含一个width属性的图像*/
		示例：img[height="300"]{border:black thin;}/*这个选择会选择HTML中所有包含一个height属性值为300的图像*/
		示例：img[alt~="flowers"]{border:black thin;}/*这个选择会选择alt属性包含单词flowers的图像*/
73、兄弟选择器：根据兄弟元素来选择元素，例如希望选择前面有一个<h1>元素的段落
		h1+p{color:red;}  /*格式先写前面的元素+兄弟元素*/
74、构造复杂选择器：先为要选择的元素定义上下文,如:div#green > blockquote /*这里id为green的div必须是blockquote的父元素*/
然后给出想选择的元素。如：div#green > blockquote p  /* 选择p元素，它必须是blockquote的子孙，而blockquote是id为green的一个div的子孙*/
然后指定伪类或伪元素，如：div#green > blockquote p:first-line/*接上，只选择这个段落的第一行*/
75、开发商特定css，格式：-开发商标识-属性
例如：div{
		transform:rotate(45deg);           /*首先列出通用属性，保证属性得到支持*/
		-webkit-transform:rotate(45deg);  /*谷歌开发商特定属性*/
		-moz-transform:rotate(45deg);      /*Mozilla开发商特定属性*/
		-o-transform:rotate(45deg);       /*Opera开发商特定属性*/
		-ms-transform:rotate(45deg);       /*IE开发商特定属性*/
	}
上例的效果是变换，旋转45度,还有个transition属性和transform属性配合使用，
				transition:transform 2s;
				-weblit-tansition:-webkit-transform 2s;
				-moz-tansition:-moz-transform 2s;
				-o-tansition:-o-transform 2s;
上面是说如果transform属性的值改变，要在指定的2s内从当前transform值过渡到新的transform值
