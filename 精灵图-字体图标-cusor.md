## 精灵图 CSS Sprite

精灵图，也叫雪碧图，是一种CSS图像合成技术,将各种**小图片合并到一张图片**上,然后利用CSS的背景定位只显示图片的很小一部分

使用精灵图的方法是通过CSS的background-image属性设置背景图片，然后通过`background-position`属性调整图片的位置，显示出需要的部分。

步骤：

- 设置对应元素的宽度和高度
- 设置精灵图作为背景图片
- 调整背景图片的位置来显示

优点：

- 减少网页加载时的HTTP请求次数，提高网页的性能和速度。

- 减小图片总大小

- 解决了图片命名的困扰,只需要针对一张集合的图片命名


制作：https://www.toptal.com/developers/css/sprite-generator

如何获取精灵图的位置：http://www.spritecow.com/

## cusor

可以设置鼠标指针（光标）在元素上面的显示样式

- `auto`：浏览器根据上下文自己决定指针的样式，比如根据文本和非文本切换指针样式
- `default`：由操作系统决定，一般就是一个小箭头
- `pointer`：一只小手，鼠标指针挪动到链接上的默认样式
- `text`：竖线。在文本上的默认样式
- `none`：没有任何指针显示在元素上面



## web fonts

在部署静态资源时, Font和HTML/CSS/JavaScript一起部署在静态服务器中

**用户的角度**:

- 浏览器一个网页时, 因为代码中有引入字体文件, 字体文件会被一起下载下来;

- 浏览器会根据使用的字体在下载的字体文件中查找、解析、使用对应的字体;

- 在浏览器中使用对应的字体显示内容;

**使用步骤**：

1. 将字体放到对应的目录中

2. 通过`@font-face`来引入字体, 并且设置格式

3. 使用字体

   注意: @font-face 用于加载一个自定义的字体;

```css
  @font-face{
    font-family: "qwerty";
    src: url(./fonts/xxxx.ttf);
  }
  body{
    font-family:"xxxx.ttf";
  }
```

**web fonts的兼容性**

有些浏览器可能不支持.ttf，为了浏览器的兼容问题，需要有对应其他格式的字体

- OpenType/TureType字体：`.otf` `.ttf`,建立在TrueType字体之上
- Embedded OpenType字体：`.eot` OpenType字体的压缩版
- SVG字体：`.svg` `.svgz`
- WOFF表示Web Open Font Format web开放字体： `.woff`，建立在TrueType字体之上



如果我们具备很强的兼容性，可以用下面的格式编写

```css
@font-face {
    font-family:-"hyfont03";
    src: url("./fonts2/AaJianHaoTi.eot");
    src: url("./fonts2/AaJianHaoTi.eot?#iefix") format("embedded-opentype"),
    url("./fonts2/AaJianHaoTi.woff") format("woff"),
    url("./fonts2/AaJianHaoTi.ttf") format("truetype"),
    url("./fonts2/AaJianHaoTi.svg#uxfonteditor") format("svg");
}
```

 这被称为"bulletproof @font-face syntax(刀枪不入的@font-face语法)"

src用于指定字体资源

- url指定资源的路径

- format用于帮助浏览器快速识别字体的格式;



## 字体图标

- 字体图标的好处:

	- 放大不会失真

	- 可以任意切换颜色

	- 用到很多个图标时,文件相对图片较小


- 字体图标的使用:
  - 登录阿里icons(https://www.iconfont.cn/)
  - 下载代码,并且拷贝到项目中

- 将字体文件和默认的css文件导入到项目中



使用步骤：

1.  通过link引入iconfont.css文件
2. 使用字体图标

使用字体图标常见的有两种方式：

1.  通过对应字体图标的Unicode来显示代码
2.  利用已经编写好的class, 直接使用即可

```css
<i class="iconfont">&#xe6f6;</i>
<i class="iconfont icon-music">;</i>
```

