# CSS 属性详解

## CSS 文本的属性

### `text-decoration` - 文本装饰线

- `text-decoration` 用于为文本添加**装饰线**。
  
  - `decoration` 是装饰/装饰品的意思;
  
- 常见取值：

  - `none`: 无装饰线（可去除 `<a>` 元素的默认下划线）。
  - `underline`: 下划线。
  - `overline`: 上划线。
  - `line-through`: 中划线（删除线）。
  


> **注意**：`<a>` 标签默认带有 `text-decoration: underline`，可用 `text-decoration: none` 取消。

### `text-transform` - 文本大小写转换

`text-transform` 用于设置文字的 **大小写转换**

- "Transform" 意为变形或变换。

常见取值：

- `capitalize`：每个单词的首字母大写（如 "hello world" → "Hello World"）。
- `uppercase`：所有字符转换为大写（如 "hello" → "HELLO"）。
- `lowercase`：所有字符转换为小写（如 "HELLO" → "hello"）。
- `none`：不转换。

### `text-indent` - 首行缩进

**`text-indent`** 用于设置段落**首行缩进**。

- `text-indent: 2em;` 表示缩进 2 个字符宽度（`em` 相对于当前字体大小）。
- 支持 `rem` 单位（相对于根元素字体大小）。
- 支持负值，例如 `text-indent: -2em;` 可实现悬挂缩进。

### `text-align` - 文本水平对齐

- 定义**行内内容**（如文本、行内元素、图片）相对于其**块级父元素**的对齐方式。

- 常用的值
  - `left`：左对齐（默认值）。
  - `right`：右对齐。
  - `center`：居中对齐。
  - `justify`：两端对齐，常用于报纸排版，浏览器会调整单词间距。

  > **注意事项**：
  >
  > - 仅对行内元素（`inline`）或行内块元素（`inline-block`）生效。
  > - 对块级元素本身（如 `div`）无效，仅影响其内容。
  > - 若需要将整个块级元素居中，可以结合 `display: inline-block` 与父元素的 `text-align: center` 来实现：
  > - 直接对块级元素（如 `<div>`）设置 `text-align: center`只会影响内部行内内容，并不会让 `<div>` 本身水平居中。
  
- 也可以让 **图片以及其他东西** 居中(**仅针对行元素, 不针对块元素**)

```css
/*让div在.block盒子里居中*/
<style>
    .block{
      background-color:#f00;
      height:300px;
      text-align:center;
        /*在这里需要注意如果仅有align的话,是居中不了的,因为text-align只针对于行元素,所以需要把块元素转换为行内块元素*/
    }
    .block>div{
      background-color: rgb(0,255,0);
      height:200px;
      width:200px;
      display:inline-block;/*转换为行内块元素*/
    }
  </style>

  <div class="block">
    <div></div>
  </div>

```

### `text-shadow` - 文本阴影

`text-shadow` 用于为文本添加阴影效果，其语法类似于 `box-shadow`（但不包含扩展半径）。

- 语法

```css
text-shadow: horizontal-offset vertical-offset blur-radius color;
```

- `horizontal-offset`：水平偏移（正值向右，负值向左）。

- `vertical-offset`：垂直偏移（正值向下，负值向上）。

- `blur-radius`：模糊半径，值越大越模糊（可选）。

- `color`：阴影颜色，可用 rgba 定义透明度。

**特点**：与 `box-shadow` 不同，无 `spread-radius`（扩展半径）参数。

```css
p {
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
}
```

[通过该网站测试文字阴影](https://html-css-js.com/css/generator/box-shadow/)

### `letter-spacing` & `word-spacing` - 字符与单词间距

- **`letter-spacing`**：设置字符间的间距。
- **`word-spacing`**：设置单词间的间距。
- 默认值均为 `0`，支持设置负值以缩小间距。

### `white-space` - 空白处理

定义如何处理元素内的空白符 (空格、制表符、换行符)。

- `normal`：合并空白字符，允许自动换行。
- `nowrap`：合并空白字符，不允许自动换行。
- `pre`：保留所有空白 (包括空格和换行)，不自动换行（类似 `<pre>` 标签）。
- `pre-wrap`: 保留所有空白，但**允许**自动换行。
- `pre-line`：合并空白字符，但保留换行符，允许自动换行。

### `text-overflow` - 文本溢出处理

指定当文本溢出其**包含元素**时如何显示。**通常用于单行文本**。

- `clip`：直接裁剪溢出部分。
- `ellipsis`：显示省略号（...）。

- **使用条件** (对于 `ellipsis`):

  1.  元素必须是块级或行内块级。
  2.  设置 `overflow: hidden;` (隐藏溢出内容)。
  3.  设置 `white-space: nowrap;` (强制文本不换行)。

- **示例**：单行文本溢出显示省略号：

  ```css
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  ```
  
  **多行省略号**: 通常需要使用 `-webkit-line-clamp` (非标准但广泛支持) 或结合 JavaScript 实现。


## CSS 字体的属性

### `font-size` 

- **`font-size`** 设置字体大小，默认值为 `16px`。

- 设置方式
  
  - 具体值：如 `20px`。
  
  - `em`：相对于父元素字体大小。
  - `rem`：相对于根元素（`<html>`）字体大小。
  - 百分比：如 `50%`，基于父元素字体大小。
  - 视口单位: `vw`, `vh` 等 (相对于视口尺寸)。
  

### `font-family` - 字体族

**`font-family`** 指定文字的字体。

- 支持多个字体，按顺序尝试，例如 `"Arial", "Helvetica", sans-serif`。
- 浏览器使用第一个用户设备支持的字体。
- 建议在字体列表末尾加上通用字体族（如 `serif` 或 `sans-serif`），以确保回退效果。

### `font-weight` - 字体粗细

设置文字的粗细程度。

- 常见取值：
  - 数值：`100` 至 `900`（`400` 为正常，`700` 为粗体）。
  - 关键字：`normal`（`400`）、`bold`（`700`）。

- `strong`、`b`、`h1~h6` 等标签的 font-weight 默认就是 bold

### line-height

- **`line-height`** 设置行高（行间距）。
- **定义**：
  - 行高是两行文字基线（`baseline`，小写字母 `x` 底部对齐的线）间的距离。
  - 行距 = `line-height` - `font-size`

![image-20231212010032299](./assets/image-20231212010032299.png)

**取值**：

- `normal`: 浏览器默认值 (通常约为 `1.2`)。

- 无单位值：如 `1.5`，表示当前字体大小的倍数。
- 具体值：如 `20px`。

**行距是上下等分** 的, 可以利用这个特性, 使 **文本** 在容器内 **垂直居中**

![image-20231212010235354](./assets/image-20231212010235354.png)

**单行文本垂直居中**: 将 `line-height` 设置为与容器 `height` 相等的值 (仅适用于单行文本)。

### `font-style`

- `font-style` 控制文本的倾斜样式。
  - `normal`：正常字体。
  - `italic`：斜体（依赖于字体是否提供内置斜体样式）。
  - `oblique`：倾斜，通常为浏览器模拟效果（即使字体不含斜体）。

注意：em、i、cite、address、var、dfn 等元素的 font-style 默认就是 `italic`

### `font-variant` - 字体变体

- **`font-variant`** 影响小写字母的显示形式。
  - `variant` 是变形的意思；
- 可以设置的值如下
  - `normal`: 常规显示
  - `small-caps`: 将小写字母替换为缩小的大写字母

### `font` - 字体缩写属性

- 用于一次性设置多个字体相关属性。**使用时需谨慎**。

  - **语法 (严格顺序)**:
    `[font-style || font-variant || font-weight]? font-size [/line-height]? font-family`

- **规则**：

  - `font-size` 和 `font-family` 必填且顺序固定。
  - 其他属性可选且顺序可调。
  - `/line-height` 可以省略, 如果不省略, 必须跟在 `font-size` **后面**

  - **示例**：

  ```css
  p {
    font: italic 700 16px/1.5 "Arial", sans-serif;
  }
  ```

  > **小技巧**：在网页中，为了视觉效果通常不会使用纯黑色 `#000`，而使用稍柔和的颜色如 `#333`。

## CSS 背景的属性

###  `background-color` - 背景颜色

设置元素的背景颜色。填充 `content` 和 `padding` 区域，位于 `border` 下方。

-   **值**: 颜色值 (`#RGB`, `#RRGGBB`, `rgb()`, `rgba()`, `hsl()`, `hsla()`, 颜色关键字, `transparent`)。
-   **默认**: `transparent` (透明)。

### `background-image` - 背景图片

`background-image` 用于设置元素的背景图片，显示在背景色之上。

-   **值**:
    -   `none`: 无背景图 (默认)。
    -   `url('path/to/image.jpg')`: 指定图像路径。
    -   渐变函数: `linear-gradient()`, `radial-gradient()`, `conic-gradient()` 等。
-   **多背景**: `background-image: url('fg.png'), url('bg.jpg');` (第一个图像在最上层)。
-   **注意**: 元素需要有尺寸 (width/height) 才能显示背景图。背景图默认显示在背景色之上。

```css
div {
  background-image: url('background.jpg');
  width: 200px;
  height: 200px;
}
```

### `background-repeat` - 背景重复

`background-repeat` 用于定义背景图片是否重复平铺。

**取值**：

- `repeat`：水平和垂直方向平铺（默认）。
- `no-repeat`：不平铺。
- `repeat-x`：仅水平平铺。
- `repeat-y`：仅垂直平铺。

![image-20231218192943566](./assets/image-20231218192943566.png)

### `background-size` - 背景尺寸

设置背景图片大小。

- `auto`：默认，保持图片原始尺寸。
- `cover`：缩放覆盖元素，可能裁剪。
- `contain`：缩放适应元素，可能留白。
- **具体尺寸**：如 `100px 200px`（分别指定宽和高）。
- **百分比**：如 `50% 50%`，相对于元素尺寸。

### `background-position` - 背景位置

设置背景图像的初始位置。原点默认为 padding box 的左上角。

- **取值**：

  - 具体值：如 `20px 50px` (距左 距上)。


  - 关键字: `top`, `bottom`, `left`, `right`, `center`。可组合使用 (如 `center top`)。


  - 百分比：如 `50% 50%`（图片中心对齐元素中心）。


- **计算**: 百分比值 `X% Y%` 指的是将图像上 `(X%, Y%)` 的点与容器内 `(X%, Y%)` 的点对齐。

- **单值**: 若只提供一个值，第二个值默认为 `center`。

**示例**：

```css
div {
  background-position: center center;
}
```

![image-20231218193336079](./assets/image-20231218193336079.png)

### `background-attachment` - 背景关联

决定背景图像是随元素滚动，还是固定在视口中。

- **值**:
  -   `scroll`: 背景相对于**元素**固定，随页面滚动 (默认)。
  -   `fixed`: 背景相对于**视口 (viewport)** 固定，不随页面滚动 (创建视差效果)。
  -   `local`: 背景相对于**元素的内容**固定，如果元素有滚动条，背景会随内容一起滚动。

### `background` - 背景缩写属性

`background` 是多个背景属性的简写。

**语法**：

```css
background: [color] [image] [repeat] [attachment] [position] / [size];
```

**示例**：

```css
div {
  background: #fff url('bg.jpg') no-repeat fixed center / cover;
}
```

- 注意若使用 `background-size`，则需要在 `background-position` 后用斜杠（/）分隔。
- 属性顺序较为灵活，但必须确保 `background-color`、`background-image`、`background-repeat`、`background-attachment` 与 `background-position`（及其后可选的 `/background-size`）能正确解析。
- **重置**: 与 `font` 类似，使用此缩写会重置未指定的背景属性为其初始值。

### `background-image` vs `<img>` 对比

| **性质**        | **img**           | **background-image** |
| --------------- | ----------------- | -------------------- |
| 占用空间        | 是                | 否                   |
| 右键查看地址    | 是                | 否                   |
| 支持 CSS Sprite | 否                | 是                   |
| 搜索引擎收录    | 是（需 alt 属性） | 否                   |

总结

- 装饰性背景通常采用 `background-image`。
- 内容相关图片建议使用 `<img>` 标签以利于 SEO（同时可使用 `alt` 属性）。

## 光标样式 (`cursor`)

设置鼠标指针悬停在元素上时显示的图标样式。

**常见取值**：

- `auto`：浏览器根据上下文决定。
- `default`：默认箭头。
- `pointer`：小手（可点击）。
- `text`：文本光标（竖线）。
- `none`：隐藏光标。
- `url('path/to/cursor.cur'), auto`: 使用自定义光标图像，提供后备。

## 垂直对齐 (`vertical-align`)

`vertical-align` 属性定义 **行内级元素 **或 **行内块级元素** 在一个 **行盒（line box）** 中的垂直对齐方式。

基础思考：`div` 的高度从何而来？

- **问题**：一个 `div` 未设置高度时，会有高度吗？  
  - **无内容**：高度为 0。  
  - **有内容**：内容会撑起 `div` 的高度。  
- **本质**：  
  - 内容具有 **行高（line-height）**，撑起了 `div` 的高度。  
- **行高撑起高度的原因**：  
  - CSS 中存在 **行盒（line boxes）**，用于包裹一行中的所有 **行内级元素（inline-level elements）**。  
  - 文字等内容有行高，**line boxes** 必须完整包裹行高，才能正确包含这些元素。

进一步思考：

如果 `div` 中包含 **文字**、**图片**、**inline-block 元素**，甚至这些元素设置了 `margin` 等属性，会如何影响布局？

### 深入理解 vertical-align – 不同情况分析

以下分析假设 `div` 为容器，内部元素的对齐受 `vertical-align` 控制：

1. **情况一：只有文字**  
   - **line boxes** 包裹文字的 **行高（line-height）**。  
   - 文字以默认的 `baseline`（基线）对齐。

2. **情况二：图片 + 文字**  
   - **line boxes** 包裹图片和文字的行高。  
   - 图片和文字根据各自的 `vertical-align` 值对齐（默认 `baseline`）。

3. **情况三：图片 + 文字 + inline-block（比图片大）**  
   - **line boxes** 包裹所有元素的行高。  
   - 各元素按 `vertical-align` 值对齐，默认以基线为准。

4. **情况四：图片 + 文字 + inline-block（比图片大且设置 margin-bottom）**  
   - **line boxes** 包裹所有元素的行高。  
   - `inline-block` 的 `margin-bottom` 会影响其在 **line boxes** 中的位置，但不改变行高计算。

5. **情况五：图片 + 文字 + inline-block（比图片大且设置 margin-bottom）+ 更多文字**  
   - **line boxes** 仍包裹所有元素的行高。  
   - 各元素按 `vertical-align` 对齐，`margin-bottom` 影响 `inline-block` 的最终位置。

### vertical-align 的基线（baseline）

- **核心结论**：  
  **line boxes** 会确保包裹当前行的所有内容。  
- **对齐看似复杂的原因**：  
  - 默认对齐方式是 `baseline`，不同元素的基线定义不同。  
- **什么是 baseline？**  
  - **文本**：字母 **x** 的底部。  
  - **inline-block（无文本）**：元素的 `margin-bottom` 底部（若无 `margin`，则是盒子底部）。  
  - **inline-block（有文本）**：最后一行文本的 **x** 的底部。

### vertical-align 的取值

- **`baseline`（默认值）**：  
  将元素的基线与父元素的基线对齐。  
- **`top`**：  
  将元素的顶部与 **line boxes** 的顶部对齐。  
- **`middle`**：  
  将元素的垂直中心点与父元素基线加上 **x-height**（小写字母 x 高度）一半的位置对齐。  
- **`bottom`**：  
  将元素的底部与 **line boxes** 的底部对齐。  
- **`<percentage>`**：  
  相对于 `line-height` 的百分比偏移，正值向上，负值向下，`0%` 等同于 `baseline`。  
- **`<length>`**：  
  指定具体的偏移距离（如 `10px` 或 `-5em`），`0cm` 等同于 `baseline`。

### 解决图片下边缘间隙的方法

图片作为行内级元素时，常因基线对齐在底部产生间隙，可通过以下方法解决：  

1. 设置 `vertical-align: top`、`middle` 或 `bottom`。  
2. 将图片转为块级元素：`display: block`。

补充说明

- **行内级元素（inline-level elements）**：包括 `inline`、`inline-block`、`inline-table` 等。  
- **行盒（line box）**：CSS 布局中包裹一行内容的矩形区域。  
- **x-height**：小写字母 **x** 的高度，影响 `middle` 对齐计算。  
