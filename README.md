#小白新手前端升级日记

小白我是一名测试工程师，由于一直在做浏览器的测试，所以对前端工程师特别向往，但苦于自己一个人闭门造车，一直很难进步。我们部门有一个前端大牛，我经常和他交流，感觉受益匪浅，但每次都是他说完我就很难继续深入的去学习，所以我打算把整个学习过程都搬到github上，起到督促和分享的作用。

##2014年10月10日 星期五-雾霾
#a标签里不能包含a标签
今天写页面发现的一个问题，在写一个模块的时候忘记了这个大模块需要被点击，然后将div改为a标签，像这样：

    <a class="bd">
		<div class="bd-ct">
			<a class="bd-ct-a">
				<div class="bd-ct-a-div">
					<a class="bd-ct-a-div-a"></a>
				</div>
			</a>
		</div>
	</a>
	
	
奇怪的事情发生了，因为a标签里包含a标签，所以最外面的a标签就漏掉了，然后就会有2个bd\2个ba-ct-a,简化下，直接a标签包含a标签看看会如何：

    <a class="one" href="">
		<a class="two" href="">
			<a class="three" href=""></a>
		</a>
	</a>
	
在浏览器里是在这样的：

    <a class="one" href=""></a>
    <a class="two" href=""></a>
    <a class="three" href=""></a>

一开始我还以为这是匿名行级元素，后来我就将a标签用i来代替，发现浏览器解析的时候就有正常的层级关系，这应该和a标签有关系，浏览器在解析a标签的时候如果没有发现闭包就遇到了下一个a标签就会自动补充一个闭包，但是问题又来了，如果在2个a标签之间有一个块级元素会怎么样，像这样：

    <a class="bd">
		<div class="bd-ct">
			<a class="bd-ct-a">
			</a>
		</div>
	</a>

浏览器会这样解析：

    <a class="bd"></a>
    <div class="bd-ct">
        <a class="bd"></a>
        <a class="bd-ct-a"></a>
    </div>

为什么会这样解析呢？为什么会多一个bd呢？第一个bd可以用上面的方式解释，第二个是那来的？我开始猜测是匿名行级元素问题，但有点不是很明白，等fish回来了问问他

##2014年10月9日 星期四-雾霾天气巨差
#margin为负值

这个国庆偷懒了，好多天都没写东西了。
昨天fish问我，怎么把3个div放到一个div里，3字子元素还是重叠状态，父元素的高度为最高的最元素，说实话，当时我大脑一片空白，对于这个我的理解是使用相对定位都顶在上面好了，但这样做有个问题是父类元素无法使用BFC，所以不设定高度的话只能为零，达不到高度的要求。

后来fish让我看看线上的一个项目，让我自己找，我看了半天，在fish的指点下找到了，其实这个技巧在很多地方都有应用到，核心技术就是margin为负值。

一个完整的margin属性是这么写的margin: top right bottom left;(eg: margin:10px 20px 30px 40px)。在margin属性中一共有两类参考线，top和left的参考线属于一类，right和bottom的参考线属于另一类。top和left是以外元素为参考，right和bottom是以元素本身为参考。margin的位移方向是指margin数值为正值时候的情形，如果是负值则位移方向相反。
用我自己的理解就是margin-top\left会影响自身的位置，而margin-right\bottom会影响相邻元素的位置，正值的反方向就是负值的方向。



##2014年9月23日 星期二-下了一整天的雨
#inline，block and inline-block
inline不换行
block换行
inline-block不换行

##2014年9月22日 星期一-小雨
###Doctype: standerd mode & quirks mode
quirks mode 怪异模式，为了浏览器能兼容早期的网页设计而保留的一种页面渲染模式
触发：当没有定义DOCTYPY时会触发怪异模式 ，<meta http-equiv=”X-UA-Compatible” content=”IE=EmulateIE10″ >
不同：

    1.盒子模型：
    quirks :box width = content width+padding left&right+borderleft&right
    standards: box width = content width
    2.对齐不同 ：
    quirks:在inline元素中的对齐线是bottom line
    standards:对其是baseline
    3.table字体
    quirks：table 单元格中字体的 font-size，font-style，font-weight 属性不会继承 body，只有 family 属性会被继承
    standards:字体属性都是可以继承的
    4.可替换内联元素的大小：
    quirks：no-replaced inline元素的大小是可以设置的
    standards：是不可以设置的
    5.元素百分比高度
    quirks：高度有内容的变化而变化
    standards：百分比高度被正确应用
    用margin:0 auto设置水平居中在IE下会失效
    6.溢出处理
    quirks:已出被当做扩展box来对待，对撑大父级元素
    standards:溢出后不会被裁剪，也不会被撑大
    7.quirk模式下设置图片的padding会失效
    8.quirk模式下Table中的字体属性不能继承上层的设置
    9.quirk模式下white-space:pre会失效


##2014年9月19日 星期五-晴
终于搞定了github的配置（这小白也太白了），开始我的前端记录历程，根据之前clyfish给我的建议，我决定还是踏踏实实一点，先搞定前端的最基本的技能：CSS ，计划再看一遍[CSS2.1标准](http://www.w3.org/TR/CSS21/cover.html)，然后再依照clyfish之前给的功能点过一遍，争取将css吃透。
###css：

    +doctype(standards mode and quirks mode)
    +inline, block and inline-block
    +box-sizing: border-box
    +clearfix: content: "", display: table, clear: both
    +png8, png24, png32, gif, jpg, webp
    +containing block
    +block formatting context
    +media queries
    +css preprocessors(sass, compass, less, stylus)
    +transition, animation, transform
    +css class naming(BEM)

今天学习的BEM命名法，block－element-modifiers及模块、元素、修饰符。
b可以包含b,m组成最小的b,修饰符来区别模块和元素。元素全部使用class。
