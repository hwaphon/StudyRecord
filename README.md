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
