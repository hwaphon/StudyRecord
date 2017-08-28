### 20170331


 [小tip: CSS3如何实现圆角的outline效果？](http://www.zhangxinxu.com/wordpress/2015/04/css3-radius-outline/)

 [css outline实践研究](http://www.cnblogs.com/pssp/p/5906676.html)

 [秋月何时了，CSS3 border-radius知多少？](http://www.zhangxinxu.com/wordpress/2015/11/css3-border-radius-tips/)


 教学视频- [CSS 之深入 border](http://www.imooc.com/learn/755)

 教学视频- [重拾CSS的乐趣](http://www.imooc.com/learn/588)

 利用 `outline` 可以给一个元素设置 `hover` 样式，这样和使用 `border` 有什么不同之处呢? `outline` 不占据布局空间，也就是说它不影响元素的大小，如果是这样的话，那可是可以解决很多问题啊，比如一个图片默认没有边框，hover的时候有一个1px的边框，那么如果不做处理盒子会抖动一下。

 不过 `outline` 没有圆角的效果，`Firefox` 是个例外，它有一个 `-moz-outline-radius` 属性，其实 `outline` 和 `border` 用法是很像的。为了在不影响元素大小的情况下，给一个元素添加一个外边框，而且这个元素还拥有圆角，就不能再使用 `outline` 了，可以使用 `box-shadow`。`box-shadow` 经常使用的参数是前五个，水平偏移，垂直偏移，模糊半径，扩展大小，颜色。其实这个拓展大小就好像是给 `box-shadow` 加了一个 `padding`，利用 `box-shadow: 0 0 0 5px red` 就可以在不改变元素大小的情况下添加一个宽度为 `5px`，颜色为红色的边框。

 还可以使用 `outline` 画出一个一个 `+` 的符号，用以下代码即可：

     div {

		margin: 0 auto;
		width: 48px;
		height: 48px;
		background-image: linear-gradient(120deg, #84fab0 0%, #8fd3f4 100%);
		outline: 16px dotted #fff;
		outline-offset: -16px;
	 }

  只需要将 `outline-width` 设置为元素宽高的 `1/3`，`outline-offset` 设置为宽高的 `-1/3` ，`outline-style` 设置为 `dotted` 就可以完成这个效果。

### 20170401

视屏 - [CSS 深入理解之 float 浮动](http://www.imooc.com/learn/121)


    <div id="hwa-container">

            <img src="2.jpg" id="hwa-img">

            <div id="hwa-content">
                <p>content...</p>
                <img src="2.jpg">
            </div>

    </div>

浮动两侧自适应布局：只需要给 `#hwa-img` 设置 `float`，给 `#hwa-content` 设置 `display: table-cell`（主要是为了触发 BFC，清楚浮动影响）。

右侧固定左侧自适应布局： 给 `#hwa-content` 设置 `width: 100%` 和 `float: left` ，然后给 `#hwa-container` 设置 `padding-right: 48px` 这个 `48px` 的值就是 `#hwa-img` 的宽度，因为我们要用这个位置放置 `#hwa-img`，最后一步就是给 `#hwa-img` 设置 `margin-right: -48px`,让其能够填充到 `#hwa-container` 的右侧。

浮动与单侧尺寸固定的流体布局：为 `#hwa-img` 设置 `float:left`, 然后将 `#hwa-content` 的 `margin-left` 设置一个大于 `#hwa-img` 宽度的值即可。

！！重点推荐 ：

[CSS布局奇淫巧计之-强大的负边距](http://www.cnblogs.com/2050/archive/2012/08/13/2636467.html#2457812)

[负值之美：负margin在页面布局中的应用](http://www.cnblogs.com/jscode/archive/2012/08/28/2660078.html)

[理解 CSS 中的 BFC](https://www.w3cplus.com/css/understanding-block-formatting-contexts-in-css.html)


### 20170402

慕课网 - [CSS 3D特效](http://www.imooc.com/learn/77)

慕课网- [图片阴影](http://www.imooc.com/learn/240)

父级设置了 `relative`，子元素设置了 `absolute`，且均设置了 `z-index` 属性值的时候，父级对子元素的层级有限制（即不论子元素 `z-index` 值大小，层级不“正常”显示）。如果将父级的层级设置为：`z-index：auto` ，或者父级不设置 `z-index` 属性，则子元素的 `z-index` 不受父级限制，即正常显示。）

曲线阴影的原理如下：将元素的 `after` 和 `before` 设置为带圆角的矩形（宽度略小一点），将其 `z-index` 设置为处于元素之下，让其阴影露出来即可。

翘边阴影的原理如下： 将元素的 `after` 和 `before` 设置为对称的平行四边形（可以通过 `skew` 和 `rotate` 获得），为它们设置好阴影并处于元素之下即可。

### 20170403

慕课网 - [CSS3实现网页平滑过渡效果](http://www.imooc.com/learn/252)

虽然语义性较差，但是可以利用 `input[type="radio"]` 模仿点击切换功能。

博客园- [RGBA与Opacity区别小解](http://www.cnblogs.com/myvin/p/4621417.html)

概括的来说，`rgba` 和 `opacity` 的区别如下： `opacity` 会继承父元素的 `opacity` 属性，而 `RGBA` 设置的元素的后代元素不会继承不透明属性。

文章 - [css清除浮动float的三种方法总结，为什么清浮动？浮动会有那些影响？](https://my.oschina.net/leipeng/blog/221125)

文章 - [浅谈 CSS 清除浮动的 6 种方法](https://segmentfault.com/a/1190000003937063)

文章 - [float, relative, absoulte](http://www.cnblogs.com/fu277/archive/2012/03/13/2393519.html)

知乎 - [在 CSS 中，用 float 和 position 的区别是什么？](https://www.zhihu.com/question/19588854)

文章 - [标准W3C盒子模型和IE盒子模型](http://www.cnblogs.com/ljb161108/p/6044639.html)

### 20170404

文章 - [CSS3 动画属性 animation 的基本用法](https://www.tangbc.com/article/basic-usage-of-css3-animation)

文章 - [如何理解animation-fill-mode及其使用？](https://segmentfault.com/q/1010000003867335)

### 20170405

文章 - [CSS3 Filter的十种特效](http://www.w3cplus.com/css3/ten-effects-with-css3-filter)

文章 - [ubuntu12.04装配IE8（playOnLinux)](http://www.myexception.cn/linux-unix/1441983.html)

文章 - [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

文章 - [Quick Tip: Get to Know the CSS Object Fit and Position Properties](http://tutorialzine.com/2016/04/quick-tip-get-to-know-css-object-fit-position/)

文章 - [Finally! CSS Triangles Without Ugly Hacks](http://tutorialzine.com/2017/03/css-triangles-without-hacks/)

文章 - [CSS Grid VS Flexbox: A Practical Comparison](http://tutorialzine.com/2017/03/css-grid-vs-flexbox/)

文章 - [Which tool to use? Flexbox or Grid?](http://jeffbridgforth.com/which-tool-to-use-flexbox-or-grid/comment-page-1/#comment-13561)

文章 - [Quick Tip: The Easiest Way To Show Browser Notifications](http://tutorialzine.com/2017/01/the-easiest-way-to-show-browser-notifications/)

网站- [一键生成雪碧图](http://csssprites.com/)

### 20170406

文章 - [学习Javascript闭包（Closure)](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)

### 20170407

当文字颜色深于背景颜色时，可以为文字右下方添加亮色阴影，代码如下：

    text-shadow: 1px 1px 0 rgba(255, 255, 255, .7);

当文字颜色浅于背景颜色，则可为文字左上方添加深色阴影来形成内浮雕效果，代码如下：

    text-shadow: -1px -1px 0 rgba(0, 0, 0, .7);


### 20170408

`margin` 负值边距会影响文档流和浮动流的计算，不过这种计算是从左到右，从上到下的，也就是说对于一个元素而言，如果为其设置 `margin-right` 和 `margin-bottom` 为负值 x，则文档流和浮动流会将元素的大小视为 `width + x`，而如果将其设置为 `margin-left` 和 `margin-top` 则不会这样计算，它会将元素往上或者往左拉。

### 20170409

如果 `input` 标签没有被放在 `form` 标签中，那么你设置的 `required` 属性是无效的。

文章 - [如何动态修改 placeholder 的颜色？](https://segmentfault.com/q/1010000004216231)

### 20170411

文章 - [VueJs: The Basics](https://coligo.io/vuejs-the-basics/)

文章 - [VueJs: Components](https://coligo.io/vuejs-components/)

文章 - [Creating a Markdown Editor with VueJs and GitHub's API](https://coligo.io/markdown-editor-vuejs/)

### 20170412

文章 - [2017年要学习的3个CSS新特性](http://www.iwebxy.com/post/940)

### 20170414

文章 - [CSS——LESS](http://www.w3cplus.com/css/less)

### 20170415

文章 - [纯CSS实现瀑布流布局](https://www.w3cplus.com/css/pure-css-create-masonry-layout.html)

文章 - [《你不知道的 CSS》之等比例缩放的盒子](https://www.talkingcoder.com/article/6408123439394783254)

### 20170418

文章 - [requestAnimationFrame
The secret to silky smooth JavaScript animation!](http://creativejs.com/resources/requestanimationframe/)

文章 - [破解前端面试（80% 应聘者不及格系列）：从 DOM 说起](https://zhuanlan.zhihu.com/p/26420034)

### 20170419

文章 - [开始使用Web Workers](http://blog.jobbole.com/30445/)

文章 - [css3属性column知多少](http://www.cnblogs.com/xinjie-just/p/5953386.html)

文章 - [IndexedDB简介与入门](https://segmentfault.com/a/1190000006924681?utm_source=tuicool&utm_medium=referral)

文章 - [CSS3 filter:drop-shadow滤镜与box-shadow区别应用](http://www.zhangxinxu.com/wordpress/2016/05/css3-filter-drop-shadow-vs-box-shadow/)

---

### 20170427

[webpack: Cannot find module 'webpack/lib/node/NodeTemplatePlugin](http://www.cnblogs.com/meij/p/5208214.html)

---

### 20170502

[bodyParser中间件的研究](http://www.tuicool.com/articles/beEJ32a)

---

### 20170504

[node-http](http://i5ting.github.io/node-http/#1)

### 20170505

[NodeJS包教不包会](https://www.shiyanlou.com/courses/493)
[Git 教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/)

### 20170506

[HTML's New Template Tag](https://www.html5rocks.com/zh/tutorials/webcomponents/template/)

### 20170514

[Understand JavaScript Closures With Ease](http://javascriptissexy.com/understand-javascript-closures-with-ease/)

[JavaScript Variable Scope and Hoisting Explained](http://javascriptissexy.com/javascript-variable-scope-and-hoisting-explained/)

[JavaScript Objects in Detail](http://javascriptissexy.com/javascript-objects-in-detail/)

### 20170516

[【转载】CSS书写模式](https://www.w3cplus.com/css/css-writing-modes.html)

[理解Flexbox：你需要知道的一切](https://www.w3cplus.com/css3/understanding-flexbox-everything-you-need-to-know.html)

[text-stroke实现文本描边效果](https://www.w3cplus.com/css3/text-stroke.html)

### 20170517

[CSS进阶：提高你前端水平的 4 个技巧](http://mp.weixin.qq.com/s/UtQXVjJIJlwff6Y0B5hS2g)

[What Makes For a Semantic Class Name?](https://css-tricks.com/semantic-class-names/)

### 20170524

[Sass Guide](http://sass-lang.com/guide)

[Building a Horizontal Timeline With CSS and JavaScript](https://webdesign.tutsplus.com/tutorials/building-a-horizontal-timeline-with-css-and-javascript--cms-28378)

[Building a Vertical Timeline With CSS and a Touch of JavaScript](https://webdesign.tutsplus.com/tutorials/building-a-vertical-timeline-with-css-and-a-touch-of-javascript--cms-26528)

[获取元素CSS值之getComputedStyle方法熟悉](http://www.zhangxinxu.com/wordpress/2012/05/getcomputedstyle-js-getpropertyvalue-currentstyle/)

### 20170605
[精通 gulp 常用插件](https://juejin.im/entry/58a3c17ab123db00545e42de)

### 20170817
[JavaScript Promise 迷你书](http://liubin.org/promises-book/)

### 20170819
[Sass Basics](http://sass-lang.com/guide)

### 20170825
[你所不知道的 CSS 动画技巧与细节](http://www.cnblogs.com/coco1s/p/7443263.html)
