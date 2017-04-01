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
