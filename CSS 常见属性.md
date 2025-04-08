**核心布局 (Layout)**

1. **`display`**: 定义元素的显示类型。
    * `block`: 块级元素，占据整行。
    * `inline`: 行内元素，只占据内容所需宽度。
    * `inline-block`: 结合了 `inline` 和 `block` 的特性。
    * `flex`: **极其重要**，启用 Flexbox 弹性布局模型，用于一维布局（行或列）。
    * `grid`: **极其重要**，启用 Grid 布局模型，用于二维布局（行和列）。
    * `none`: 隐藏元素，并且不占据空间。
    * `contents`: 元素自身不产生盒子，但其子元素正常渲染（用于改变DOM结构而不影响布局）。

2. **Flexbox 相关属性 (当 `display: flex` 时)**
    * `flex-direction`: 主轴方向 (`row`, `column`, `row-reverse`, `column-reverse`)。
    * `justify-content`: 主轴对齐方式 (`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`)。
    * `align-items`: 交叉轴（单行/列）对齐方式 (`stretch`, `flex-start`, `flex-end`, `center`, `baseline`)。
    * `align-content`: 交叉轴（多行/列）对齐方式 (`stretch`, `flex-start`, `flex-end`, `center`, `space-between`, `space-around`)。
    * `flex-wrap`: 是否换行 (`nowrap`, `wrap`, `wrap-reverse`)。
    * `flex-grow`: 放大比例（数字）。
    * `flex-shrink`: 缩小比例（数字）。
    * `flex-basis`: 元素在主轴上的初始大小 (`auto`, 长度值, 百分比)。
    * `flex`: `flex-grow`, `flex-shrink`, `flex-basis` 的简写。
    * `gap` (或 `row-gap`, `column-gap`): Flex 项目之间的间距。
    * `order`: Flex 项目的排列顺序（数字）。
    * `align-self`: 单个 Flex 项目在交叉轴上的对齐方式（覆盖 `align-items`）。

3. **Grid 布局相关属性 (当 `display: grid` 时)**
    * `grid-template-columns`: 定义网格列的轨道（大小、数量）。
    * `grid-template-rows`: 定义网格行的轨道。
    * `grid-template-areas`: 使用命名区域定义网格布局。
    * `gap` (或 `row-gap`, `column-gap`): 网格轨道之间的间距。
    * `justify-items`: 网格项沿行轴（内联轴）的对齐方式。
    * `align-items`: 网格项沿块轴（列轴）的对齐方式。
    * `place-items`: `align-items` 和 `justify-items` 的简写。
    * `justify-content`: 网格容器内网格沿行轴的对齐方式（当网格总尺寸小于容器时）。
    * `align-content`: 网格容器内网格沿块轴的对齐方式（当网格总尺寸小于容器时）。
    * `place-content`: `align-content` 和 `justify-content` 的简写。
    * `grid-column-start`, `grid-column-end`, `grid-row-start`, `grid-row-end`: 定义网格项放置的起始/结束线。
    * `grid-column`, `grid-row`: 上面四个属性的简写。
    * `grid-area`: 定义网格项放置的区域（可以是名称或行列线）。

**盒子模型 (Box Model)**

4. **`width`, `height`**: 设置元素内容的宽度和高度。
5. **`min-width`, `max-width`, `min-height`, `max-height`**: 设置元素的最小/最大宽度和高度。
6. **`padding`**: 内边距（元素内容与边框之间）。可分拆为 `padding-top`, `padding-right`, `padding-bottom`, `padding-left`。
7. **`margin`**: 外边距（元素边框与相邻元素之间）。可分拆为 `margin-top`, `margin-right`, `margin-bottom`, `margin-left`。
8. **`border`**: 边框。可拆分为 `border-width`, `border-style`, `border-color`，也可按方向拆分 (`border-top`, etc.)。
9. **`box-sizing`**: **极其重要**，定义 `width` 和 `height` 如何计算。
    * `content-box` (默认): `width`/`height` 只包含内容区。
    * `border-box`: `width`/`height` 包含内容区、`padding` 和 `border`。现代开发通常全局设为 `border-box`。

**定位 (Positioning)**

10. **`position`**: 元素的定位方案。
    * `static` (默认): 正常文档流。
    * `relative`: 相对自身原始位置进行偏移，仍占据原始空间。
    * `absolute`: 相对于最近的 *已定位* (非 `static`) 祖先元素进行定位，脱离文档流。
    * `fixed`: 相对于视口（Viewport）进行定位，脱离文档流。
    * `sticky`: 结合了 `relative` 和 `fixed`，在滚动到特定阈值前表现为 `relative`，之后表现为 `fixed`。
11. **`top`, `right`, `bottom`, `left`**: 当 `position` 不是 `static` 时，用来指定元素的偏移量。
12. **`z-index`**: 控制已定位元素的堆叠顺序（数值越大越靠上）。

**排版与文本 (Typography & Text)**

13. **`color`**: 文本颜色。
14. **`font-family`**: 字体族（如 "Arial", sans-serif）。
15. **`font-size`**: 字体大小（常用 `px`, `em`, `rem`）。
16. **`font-weight`**: 字体粗细 (`normal`, `bold`, 数值 100-900）。
17. **`line-height`**: 行高（影响垂直间距）。
18. **`text-align`**: 文本水平对齐方式 (`left`, `right`, `center`, `justify`)。
19. **`text-decoration`**: 文本装饰 (`none`, `underline`, `overline`, `line-through`)。
20. **`text-transform`**: 文本大小写转换 (`none`, `uppercase`, `lowercase`, `capitalize`)。
21. **`letter-spacing`**: 字符间距。
22. **`word-spacing`**: 单词间距。
23. **`white-space`**: 处理元素内的空白符 (`normal`, `nowrap`, `pre`, `pre-wrap`, `pre-line`)。
24. **`text-overflow`**: 处理溢出的文本 (`clip`, `ellipsis`)，通常配合 `overflow: hidden` 和 `white-space: nowrap` 使用。

**视觉效果 (Visual Effects)**

25. **`background`**: 背景（简写属性）。
    * `background-color`: 背景颜色。
    * `background-image`: 背景图片 (`url(...)`)。
    * `background-repeat`: 背景重复方式 (`no-repeat`, `repeat`, `repeat-x`, `repeat-y`)。
    * `background-position`: 背景图片位置。
    * `background-size`: 背景图片尺寸 (`auto`, `cover`, `contain`, 长度/百分比)。
26. **`border-radius`**: 圆角。
27. **`box-shadow`**: 盒子阴影。
28. **`opacity`**: 元素的不透明度 (0.0 - 1.0)。
29. **`visibility`**: 控制元素可见性 (`visible`, `hidden`)。`hidden` 会隐藏元素，但仍占据空间（与 `display: none` 不同）。
30. **`cursor`**: 鼠标悬停时的光标样式 (`pointer`, `default`, `text`, etc.)。
31. **`overflow`**: 处理内容溢出元素盒子的情况 (`visible`, `hidden`, `scroll`, `auto`)。可分拆为 `overflow-x`, `overflow-y`。
32. **`filter`**: 应用图形效果（如 `blur()`, `grayscale()`, `brightness()`, `contrast()` 等）。
33. **`backdrop-filter`**: 对元素*后面*的区域应用图形效果（常用于毛玻璃效果）。
34. **`object-fit`**: 规定 `<img>` 或 `<video>` 等替换元素的内容如何适应其容器 (`fill`, `contain`, `cover`, `none`, `scale-down`)。
35. **`aspect-ratio`**: 设置元素的宽高比，让浏览器自动计算高度或宽度。

**过渡与动画 (Transitions & Animations)**

36. **`transition`**: 定义属性值平滑过渡的效果（简写）。
    * `transition-property`: 指定应用过渡的 CSS 属性名称。
    * `transition-duration`: 过渡持续时间。
    * `transition-timing-function`: 过渡速度曲线 (`linear`, `ease`, `ease-in`, `ease-out`, `ease-in-out`, `cubic-bezier(...)`)。
    * `transition-delay`: 过渡开始前的延迟时间。
37. **`animation`**: 应用动画（简写）。
    * `animation-name`: 绑定到 `@keyframes` 规则的名称。
    * `animation-duration`: 动画持续时间。
    * `animation-timing-function`: 动画速度曲线。
    * `animation-delay`: 动画开始前的延迟。
    * `animation-iteration-count`: 动画播放次数 (`infinite` 表示无限次)。
    * `animation-direction`: 动画播放方向 (`normal`, `reverse`, `alternate`, `alternate-reverse`)。
    * `animation-fill-mode`: 动画结束后元素的状态 (`none`, `forwards`, `backwards`, `both`)。
    * `animation-play-state`: 控制动画播放/暂停 (`running`, `paused`)。
38. **`@keyframes`**: 定义动画的关键帧。

**其他重要特性**

39. **CSS 变量 (Custom Properties)**:
    * `--*`: 定义自定义属性 (e.g., `--main-color: #3498db;`)。
    * `var()`: 使用自定义属性 (e.g., `color: var(--main-color);`)。极大提高了 CSS 的可维护性和主题化能力。
40. **`outline`**: 绘制于元素周围的轮廓线，不影响布局（常用于焦点状态）。
41. **`list-style`**: 设置列表项标记（`list-style-type`, `list-style-position`, `list-style-image` 的简写）。
42. **`pointer-events`**: 控制元素是否能成为鼠标事件的目标 (`auto`, `none`)。

**重要概念（非属性，但与属性应用密切相关）**

* **选择器 (Selectors)**: 如类选择器 (`.class`), ID 选择器 (`#id`), 属性选择器 (`[attr]`), 伪类 (`:hover`, `:focus`, `:nth-child()`), 伪元素 (`::before`, `::after`) 等，决定了样式应用到哪些元素。
* **层叠与继承 (Cascade & Inheritance)**: 理解样式如何覆盖以及子元素如何继承父元素样式。
* **特殊性/优先级 (Specificity)**: 决定当多个规则应用到同一元素时哪个规则生效。
* **响应式设计 (Responsive Design)**: 使用 `@media` 查询根据设备特性（如视口宽度）应用不同样式。
* **单位 (Units)**: 理解不同单位的适用场景，如 `px`, `%`, `em`, `rem`, `vw`, `vh`, `fr` (Grid布局)。`rem` 和 `vw/vh` 在现代响应式开发中尤其重要。
