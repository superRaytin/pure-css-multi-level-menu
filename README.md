> 代码也疯狂，一段代码，一段人生。

# Navigation
* [css-multi-level-menu & 纯CSS无限制级联菜单](#css-multi-level-menu)
* [QQMail-style-tips-floating-layer & QQ邮箱风格的浮层提示](#QQMail-style-tips-floating-layer)

# css-multi-level-menu
纯CSS无限制级联菜单，特点是代码量小 —— CSS不足100行，扩展性强。

引入css文件
```html
<link href="../../libs/css-multi-level-menu/multi-menu.css" rel="stylesheet">
```

HTML部分
```html
<div class="multi-menu">
    <ul>
        <li class="multi-menu-parent">
            <span class="name">Put the mouse above me</span>
            <ul>
                <li>
                    <span class="name">I'm a normal item</span>
                </li>
                ...
            </ul>
        </li>
        <li>
            <span class="name">I'm a normal item3</span>
        </li>
        ...
    </ul>
</div>
```

上面的例子展示了一个简单的二级菜单，更多级按照同样的格式增加即可

通过给 `li` 增加class来增强功能：

* `multi-menu-parent` 表示该菜单项下面有子级菜单
* `disabled` 表示该菜单项为不可点击状态
* `separate` 表示分隔线

给 `ul` 增加class `check-list` 模仿复选框的效果，同时给子级菜单项增加class `checked` 可以选中该项，选中的项前面会有一个 `√` 标识

下面是一个结构更复杂功能更多的示例：
```html
<div class="multi-menu">
    <ul>
        <li class="multi-menu-parent">
            <span class="name">Put the mouse above me</span>
            <ul>
                <li>
                    <span class="name">I'm a normal item</span>
                </li>
                <li class="separate"></li>
                <li>
                    <span class="name">I'm a normal item2</span>
                </li>
                ...
            </ul>
        </li>
        <li class="disabled">
            <span class="name">I'm a disabled item</span>
        </li>
        <li class="multi-menu-parent">
            <span class="name">I'm a normal item4</span>
            <ul class="check-list">
                <li>
                    <span class="name">I'm a normal item</span>
                </li>
                <li class="checked">
                    <span class="name">I'm checked!</span>
                </li>
                ...
            </ul>
        </li>
        <li class="separate"></li>
        <li>
            <span class="name">I'm a normal item5</span>
        </li>
        ...
    </ul>
</div>
```

另外，如果你更喜欢less的方式，同样也提供了 [less文件](/libs/css-multi-level-menu/multi-menu.less)

以上示例只需要 `CSS` 和 `HTML`，没有脚本，也没有图片引用，低碳环保

运行效果如下图：

![css-multi-level-menu](examples/src/images/css-multi-level-menu.png)

[猛击我查看Demo](http://codepen.io/superRaytin/details/xjtgD)

### 扩展

如果想要类似操作系统，前面带有图标的菜单，那么，HTML结构只需要稍微的改一改：

```html
<li>
    <span class="glyphicon glyphicon-heart"></span>
    <span class="name">I'm a normal item3</span>
</li>
```

图标库推荐采用 `bootstrap3` 提供的字体图形库 `Glyphicons`

如果想要 `悬停` 的效果，那必须要借助JS来实现，比如用jQuery库可以这么写

```javascript
$('.multi-menu li').on('mouseover', function(){
    var that = $(this);
    if(that.hasClass('disabled')) return;
    if(that.hasClass('multi-menu-parent')){
        that.find('> ul').show();
    }
    that.siblings('li').find('ul').hide();
});
// 点击空白处隐藏
$('html').on('click', function(){
    var menu = $('.multi-menu');
    if(menu.length){
        menu.find('li.multi-menu-parent > ul').hide();
    }
});
```

同时还需要对 `multi-menu.css` 作一个小小的改动，去掉下面这一句

```css
.multi-menu ul li.multi-menu-parent:not(.disabled):hover > ul {
  display: block;
}
```

或者直接使用改好的 [multi-menu-with-js.css](/libs/css-multi-level-menu/multi-menu-with-js.css)

[猛击我查看Demo（扩展）](http://codepen.io/superRaytin/pen/GIxyt)

# QQMail-style-tips-floating-layer
QQ邮箱风格的浮层提示，觉得很是美观，遂提取出来，仅供学习参考，设计版权归QQ邮箱所有。

引入css文件
```html
<link href="../../libs/QQMail-style-tips-floating-layer/floating-tips.css" rel="stylesheet">
```

推荐使用 [less文件](/libs/QQMail-style-tips-floating-layer/floating-tips.less)

HTML部分
```html
<span class="qtips_wrap">
	<div class="qtips">
		<div class="tipcontainer">
			<span class="arrowup"></span>
				<div class="container">
					<div class="contentcontainer">
						<div class="content">
							<div class="tipsicon">
								<span class="tipsico tipsico_normal"></span>
							</div>
							<a class="btnClose" href="javascript:;"></a>
							<div class="tipstxt">
								<div class="desc">生活不是眼前的苟且，<br>生活有诗和远方。</div>
							</div>
							<div class="tipsrightpanel">
								<div class="opertbar">
									<a href="http://3g.mail.qq.com/cgi-bin/loginpage" target="_blank">了解更多</a>
									&nbsp;&nbsp;<a class="" title="" href="javascript:;">我知道了</a>
								</div>
							</div>
							<div class="clr"></div>
						</div>
					</div>
				</div>
			<span class="arrowdown hide"></span>
		</div>
		<div class="tipbackground"></div>
	</div>
</span>
```

运行效果如下图：

![css-multi-level-menu](examples/src/images/QQMail-style-tips-floating-layer.png)

[猛击我查看Demo](http://codepen.io/superRaytin/details/vwmEt)