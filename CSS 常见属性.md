### **一、文本相关属性**

1. **`color`**  
   设置文本的颜色。可以通过颜色名称（如 `red`）、十六进制值（如 `#ff0000`）、RGB 值（如 `rgb(255, 0, 0)`）或 HSL 值（如 `hsl(0, 100%, 50%)`）来定义颜色。

2. **`font-family`**  
   定义字体族。可以指定多个字体作为备选方案，例如：`font-family: Arial, sans-serif;`。浏览器会按照顺序尝试加载字体，如果第一个字体不可用，则使用下一个。

3. **`font-size`**  
   设置字体大小。常见的单位包括像素（`px`）、百分比（`%`）、相对单位（`em` 或 `rem`）。例如，`16px` 表示字体高度为 16 像素，而 `1.2em` 表示相对于父元素字体大小的 1.2 倍。

4. **`font-weight`**  
   设置字体的粗细。常见值有 `normal`（默认值，通常为 400）、`bold`（加粗，通常为 700），也可以直接使用数值（如 `100` 到 `900` 的整数倍）。

5. **`text-align`**  
   控制文本的对齐方式。可选值包括：
   - `left`：左对齐（默认值）。
   - `right`：右对齐。
   - `center`：居中对齐。
   - `justify`：两端对齐，使每行的宽度相同。

6. **`text-decoration`**  
   添加或移除文本装饰效果。常用值包括：
   - `underline`：添加下划线。
   - `line-through`：添加删除线。
   - `overline`：添加上划线。
   - `none`：移除所有装饰效果。

7. **`text-transform`**  
   转换文本的大小写。常用值包括：
   - `uppercase`：将文本转换为大写。
   - `lowercase`：将文本转换为小写。
   - `capitalize`：将每个单词的首字母大写。

8. **`line-height`**  
   设置行间距。可以使用无单位数字（如 `1.5`，表示相对于字体大小的比例）、固定单位（如 `20px`）或百分比（如 `150%`）。

9. **`letter-spacing`**  
   调整字符之间的间距。正值增加间距，负值减少间距。例如，`letter-spacing: 2px;` 表示每个字符之间增加 2 像素的间距。

10. **`word-spacing`**  
    调整单词之间的间距。与 `letter-spacing` 类似，但作用于单词间。例如，`word-spacing: 5px;` 表示每个单词之间增加 5 像素的间距。

---

### **二、盒模型相关属性**

11. **`width` 和 `height`**  
    设置元素的宽度和高度。可以使用固定单位（如 `px`）、百分比（如 `50%`）或自动计算（如 `auto`）。需要注意的是，这些值仅适用于内容区域（`content-box`）。

12. **`margin`**  
    定义元素的外边距，用于控制元素与其他元素之间的距离。可以分别设置四个方向（`margin-top`、`margin-right` 等），或者使用简写形式（如 `margin: 10px 20px;` 表示上下 10px，左右 20px）。

13. **`padding`**  
    定义元素的内边距，用于控制内容与边框之间的距离。同样支持四个方向的单独设置或简写形式。

14. **`border`**  
    设置边框样式。完整语法为 `border: [宽度] [样式] [颜色]`，例如 `border: 1px solid black;`。还可以单独设置某一边的边框，如 `border-top`。

15. **`border-radius`**  
    设置边框的圆角半径。可以使用像素值（如 `10px`）或百分比（如 `50%`，形成圆形）。例如，`border-radius: 50%;` 可以将正方形变成圆形。

16. **`box-sizing`**  
    控制盒模型的计算方式：

- `content-box`（默认值）：宽度和高度仅包括内容区域。
- `border-box`：宽度和高度包括内容、内边距和边框。

17. **`display`**  
    定义元素的显示模式。常见值包括：

- `block`：块级元素，独占一行。
- `inline`：行内元素，与其他元素共存于同一行。
- `flex`：弹性布局容器。
- `grid`：网格布局容器。

18. **`visibility`**  
    控制元素是否可见。值为 `visible` 时元素正常显示，值为 `hidden` 时元素隐藏但仍占据空间。

19. **`overflow`**  
    处理内容溢出的情况。常见值包括：

- `hidden`：隐藏溢出的内容。
- `scroll`：始终显示滚动条。
- `auto`：仅在内容溢出时显示滚动条。

---

### **三、背景与图像相关属性**

21. **`background-color`**  
    设置背景颜色，类似于 `color` 属性，但作用于元素的背景。

22. **`background-image`**  
    设置背景图片。例如，`background-image: url('image.jpg');`。

23. **`background-repeat`**  
    控制背景图片的重复方式。常用值包括：

- `repeat`：水平和垂直方向重复。
- `no-repeat`：不重复。
- `repeat-x`：仅水平方向重复。
- `repeat-y`：仅垂直方向重复。

24. **`background-position`**  
    定义背景图片的位置。可以使用关键字（如 `top left`）、百分比（如 `50% 50%`）或像素值（如 `10px 20px`）。

25. **`background-size`**  
    设置背景图片的尺寸。常用值包括：

- `cover`：按比例缩放图片以完全覆盖背景区域。
- `contain`：按比例缩放图片以完全适应背景区域。

26. **`opacity`**  
    设置元素的透明度，取值范围为 `0`（完全透明）到 `1`（完全不透明）。例如，`opacity: 0.5;` 表示半透明。

27. **`object-fit`**  
    控制图片或视频在容器中的适应方式。常用值包括：

- `cover`：按比例缩放以填满容器。
- `contain`：按比例缩放以适应容器。

28. **`clip-path`**  
    定义剪裁路径，用于创建复杂的形状。例如，`clip-path: circle(50%);` 可以将元素剪裁为圆形。

29. **`filter`**  
    应用滤镜效果。常见值包括：

- `blur(5px)`：模糊效果。
- `grayscale(50%)`：灰度效果。
- `brightness(150%)`：亮度调整。

30. **`mask`**  
    使用遮罩效果定义元素的可见区域。例如，`mask-image: linear-gradient(black, transparent);` 可以创建渐变透明效果。

---

### **四、布局相关属性**

31. **`position`**  
    定义元素的定位方式：

- `static`：默认值，元素按照文档流排列。
- `relative`：相对于自身位置进行偏移。
- `absolute`：相对于最近的已定位祖先元素进行定位。
- `fixed`：相对于视口进行定位。

32. **`top`, `right`, `bottom`, `left`**  
    设置定位偏移量。仅在 `position` 不为 `static` 时生效。

33. **`z-index`**  
    控制堆叠顺序。数值越大，元素越靠前。

34. **`float`**  
    设置浮动效果。常见值包括 `left` 和 `right`，用于实现文字环绕图片等效果。

35. **`clear`**  
    清除浮动的影响。常用值包括 `left`、`right` 和 `both`。

36. **`flex`**  
    定义弹性盒子子项的属性。例如，`flex: 1;` 表示子项占据剩余空间。

37. **`flex-direction`**  
    设置主轴方向。常见值包括 `row`（水平方向）和 `column`（垂直方向）。

38. **`justify-content`**  
    定义主轴上的对齐方式。常见值包括 `center`（居中对齐）、`space-between`（均匀分布）。

39. **`align-items`**  
    定义交叉轴上的对齐方式。常见值包括 `center`（居中对齐）、`stretch`（拉伸填充）。

40. **`grid-template-columns`**  
    定义网格布局的列结构。例如，`grid-template-columns: 1fr 2fr 1fr;` 表示三列，宽度比例为 1:2:1。

---

### **五、动画与过渡相关属性**

41. **`transition`**  
    定义过渡效果。完整语法为 `transition: [属性名] [持续时间] [时间函数] [延迟时间]`。例如，`transition: all 0.3s ease-in-out;`。

42. **`animation`**  
    定义动画效果。完整语法为 `animation: [名称] [持续时间] [时间函数] [延迟时间] [迭代次数] [方向] [填充模式]`。

43. **`transform`**  
    应用变换效果。常见值包括：

- `rotate(45deg)`：旋转 45 度。
- `scale(2)`：放大两倍。
- `translateX(10px)`：沿 X 轴平移 10 像素。

44. **`transform-origin`**  
    设置变换的原点位置。例如，`transform-origin: top left;` 表示以左上角为原点。

45. **`backface-visibility`**  
    控制元素背面是否可见。常见值包括 `visible` 和 `hidden`。

---

### **六、其他常用属性**

46. **`cursor`**  
    设置鼠标指针的样式。常见值包括 `pointer`（手型）、`default`（默认箭头）。

47. **`outline`**  
    定义轮廓线，通常用于表单控件的聚焦状态。例如，`outline: 1px solid red;`。

48. **`list-style`**  
    定义列表的样式。常见值包括 `disc`（实心圆点）、`circle`（空心圆点）、`none`（无样式）。

49. **`white-space`**  
    控制空白符的处理方式。常见值包括：

- `nowrap`：禁止换行。
- `pre`：保留空白符和换行符。

50. **`user-select`**  
    控制用户是否可以选择文本。常见值包括 `none`（禁止选择）和 `text`（允许选择）。

