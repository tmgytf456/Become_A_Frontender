#小白新手前端升级日记

小白我是一名测试工程师，由于一直在做浏览器的测试，所以对前端工程师特别向往，但苦于自己一个人闭门造车，一直很难进步。我们部门有一个前端大牛，我经常和他交流，感觉受益匪浅，但每次都是他说完我就很难继续深入的去学习，所以我打算把整个学习过程都搬到github上，起到督促和分享的作用。

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
