# BootstrapPage

页面效果如下：

![home](https://github.com/FanXuanyi/BootstrapPage/blob/master/preview/home.png)

![information](https://github.com/FanXuanyi/BootstrapPage/blob/master/preview/information.png)

![product](https://github.com/FanXuanyi/BootstrapPage/blob/master/preview/product.png)

![article](https://github.com/FanXuanyi/BootstrapPage/blob/master/preview/article1.png)

![article](https://github.com/FanXuanyi/BootstrapPage/blob/master/preview/article2.png)

![about](https://github.com/FanXuanyi/BootstrapPage/blob/master/preview/about.png)

![connect](https://github.com/FanXuanyi/BootstrapPage/blob/master/preview/connect.png)

整个网页被我分成了九个部分（行）。下面来简单说明一下。

#### 1、导航栏（navbar）

整个放在`<nav>`标签中。
一行中分为两部分，一部分是标题或是logo图片（.navbar-header），另一部分是菜单选项栏（.navbar-nav）。

随着页面滚动，导航栏固定不动（.navbar-fixed-top），并且其背景颜色与首页背景一致（.navbar-dark）。

这里是一个响应式导航栏，当窗口小于768px时，会出现一个汉堡按钮。
因为我这里背景色很浅，所以需要设置这个汉堡按钮的颜色来更好的显示它。
在这里使用的是一个类名为sr-only的`<span>`和3个类名为icon-bar的`<span>`的标签实现的，也可以考虑使用fontawesome图标加文字的方式来实现。

存在的问题：窗口缩小，点击按钮后，选项的内容出现在最右端而不是最左侧。

解决办法：出现上面的问题是因为设置了一个右浮动，这里，我使用@media分屏幕大小设置样式，当窗口宽度小于768px时，清除浮动。

待实现的效果：从首页滚动到其他页面时，导航栏会有一个高度缩小的动画。

#### 2、头部（首页）（masthead）

整个放在`<header>`标签中。
该部分包含有两句欢迎语和一个按钮。
其中，两句欢迎语我分别放在了两个`<p>`标签中，也可以考虑使用`<hx>`标签。
按钮使用`<a>`标签加上btn类名来实现。

因为按钮点击后跳转到第一个内容块，所以将按钮`<a>`中的href指向第一个内容块的id。

添加背景图片，设置background-image、background-repeat、background-size属性。

存在的问题：背景图片随窗口大小自适应的问题。窗口缩小后，并没有显示完整的背景图。第五个内容块的背景也存在该问题。

解决办法：将background-size由cover设置为100% 100%，这样做虽然解决了自适应的问题，但是图片不是等比例拉伸，有可能会使图片失真。

接下来，有5个内容块，分别对应导航菜单栏中的5个选项。每个内容块都放在一个`<section>`标签中，并且每个内容块的第一行都包含一个标题和一个副标题，这一行的样式也一致的。每个内容块的背景色交替设置。

#### 3、信息（information）

这是第一个内容块。
分为了两行。
在第二行中，分为了三列，并且每一列都一样，都是由图标、小标题和文字内容组成。

关于图标使用的是font awesome，在这里是组合使用。
需要使用fa-stack类作为父类。关于图标大小和颜色说明一下，fa-stack-1x是正常比例，fa-inverse类可以切换图标颜色，或者自己使用CSS设置成想要的颜色。

#### 4、项目（project）

这是第二个内容块。
分为了两行。
在第二行中，分为了六块相同的内容。每一块都是由图片、小标题和一个简短信息组成。

关于图片，考虑到响应式，添加一个img-responsive类。
同时，这里存在着动画效果。当鼠标滑到图片上时会出现一个遮罩，移开时就消失；当鼠标点击后进入一个模态框。

1）关于遮罩的实现

- 遮罩使用绝对定位。
- 遮罩的长、宽要与图片的大小一致，考虑到窗口大小会变化，最好使用百分数来表示。
- 首先，我将width和height都设为100%后，出现了一个问题，就是缩小窗口后，遮罩的宽度多宽。但是我给`<img>`的父元素`<a>`设置了一个max-width属性便解决了这个问题。
- 鼠标未滑到图片上时，遮罩透明度opacity为0；当滑到（悬停）时，opacity为1。
- 遮罩出现的效果动画通过设置transition属性。

2）鼠标点击后出现的弹框——模态框

模态框中包含有标题、副标题、图片、文字、列表信息和关闭按钮这些内容。

出现的问题：模态框的大小设置。通过设置`width: 100%; display:inline-block;`解决了宽度没有覆盖整个窗口的问题，但是高度没有解决。

解决办法：上下没有覆盖整个屏幕是因为存在外边距，只要给上下外边距设为0即可。
但存在一个新的问题，将窗口缩小后，右上角的关闭按钮点击没有反应。

#### 5、文章（article）

这是第三个内容块。
分为了两行。
在第二行中，显示的是一个按时间轴形式的文章列表。

每一个图片加文字的布局如下代码所示：

```
<div>
    <div><!-- 图片 -->
        <img src="#">
    </div>
    <div><!-- 文字 -->
        <div><!-- 时间+标题 -->
            <h3>Time</h3>
            <h3>TiTle</h3>
        </div>
        <div><!-- 概述 -->
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Sunt ut voluptatum eius sapiente, totam reiciendis temporibus qui quibusdam, recusandae sit vero unde, sed, incidunt et ea quo dolore laudantium consectetur!</p>
        </div>
    </div>
</div>
```

图片之间的连线用伪元素before/after实现。

当窗口大于768px时，图片居中，文字内容左右交替显示；当窗口小于768px时，图片全部排在左侧，文字在右侧显示。所以使用了@media分屏幕大小来设置样式。

存在的问题：当窗口缩到更小时，文字和图片会重叠。

#### 6、关于（about）

这是第四个内容块。
分为了三行。
第二行，分为了三个相同的列。每一列由图片、名字、职位和三个小图标组成。
第三行是一段文字，并且居中显示。在这里添加了类col-lg-8，说明占了8列，为了让其居中显示，可以添加类col-lg-offset-2右移两列来实现。

#### 7、图标（logo）

整个放在一个`<section>`标签中。
只有一行，由四张图片组成。
在这里，因为放置的图片大小不一致，但是为了不显得突兀，我将整个div的背景色设置为与logo图片背景色一样的颜色。

#### 8、联系（contact）

这是第五个内容块。
分为了两行。
在第二行中是一个form表单。
左侧是三个`<input>`标签，用于填写name、email、phone的内容；
右侧是一个`<textarea>`文本标签，用于填写一些message。
在底部还有一个提交按钮。

#### 9、底部（footer）

整个放在`<footer>`标签中。
只有一行，分为了三列。包含的内容分别是版权、图标和其他链接。

最后，使用JS和jQuery来添加一些动画效果。

#### 1、点击导航栏菜单选项后滚动到相应页面

首先，将菜单选项的`<a>`标签中的href指向需要跳转的相应页面，这样点击之后就实现了跳转。
接下来实现滚动的效果。
使用offset()获取匹配元素在当前视口的相对偏移，这个方法会返回top和left两个值，在这里，我们只需要top值。
我们将对应的5内容块的偏移距离保存在一个数组中，然后获取点击选项的索引值找到对应的偏移地址。
使用delegate()方法为指定的元素添加一个或多个事件处理程序（在此处是点击事件），并规定这些事件发生时运行的函数（在此处是滚动到相应页面）。

在添加/移除样式时，使用lis[n].children()来获取子元素时，会报错。这是因为lis表示的是获取的`<li>`标签的一个数组，此时的它已经没有子元素了。但是可以直接使用$(this)来获取当前点击的元素。

#### 2、点击首页的more按钮滚动到第一个内容块页面

为了方便，给第一个选项的`<a>`标签添加一个first类。获取该元素并为该元素添加一个on类（高亮显示），然后为其父元素的同辈元素的所有子元素移除on类（移除高亮显示）。

#### 3、滚动条改变导航栏元素效果

将滚动条滚动的距离和内容块页面偏移顶部的距离进行比较，来判断当前显示页面，从而为相应选项进行高亮显示。


博客地址：http://blog.csdn.net/lollipop94/article/details/78312857
