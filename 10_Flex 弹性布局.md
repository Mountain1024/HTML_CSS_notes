# 	Flex 布局

## 什么是 Flexbox？

**Flexbox**（弹性盒子布局）是一种强大的 CSS3 一维布局模型，专为解决现代 Web 应用的布局需求而设计。

- **核心特性**：
  - **动态调整**：子元素可根据容器可用空间自动**膨胀**（填充多余空间）或**收缩**（适应有限空间），实现自适应效果。
  - **一维布局**：专注于行或列的单向排列，与二维的 Grid 布局互补。
  - **术语：** 通常简称为 **Flex 布局**或 **弹性布局**。
- **普及性**：
  - **移动端**：已成为事实标准，几乎所有现代移动页面依赖 Flexbox。
  - **PC 端**：占据主流，仅少数老旧网站仍依赖传统浮动（`float`）或定位（`positioning`）。

## 为什么需要 Flex 布局？

### 传统布局的局限性

在 Flexbox 出现之前，Web 开发者主要依赖 **浮动 (float)**、**定位 (positioning)** 和 **表格布局 (table layout)** 来实现页面布局。但这些工具存在明显缺陷：

- **浮动（`float`）**：
  - **设计初衷**：用于文字环绕图片，而非布局。
  - **问题**：需借助清除浮动（`clear`）或伪元素（如 `::after`），实现复杂且易出错；多列布局时，高度无法自然对齐。
- **定位（`positioning`）**：
  - **特点**：通过绝对（`absolute`）或相对（`relative`）定位实现灵活布局。
  - **不足**：难以适配动态变化的屏幕尺寸，复杂响应式设计维护成本高。
  - **例子**：绝对定位元素无法随容器大小自动调整位置。
- **表格布局 (table layout)**
  *   **设计目的：** 使用 HTML 表格 (`<table>`) 元素进行布局。
  *   **主要问题：**
      *   结构复杂，语义化差，不利于 SEO 优化。
      *   渲染性能较差，影响页面加载速度。

传统方法难以优雅实现以下常见需求：

1. **垂直居中**：需计算偏移量（如 `top: 50%; margin-top: -高度/2`）或借助表格布局（`display: table`），代码复杂。
2. **等分空间**：子元素平分容器宽度需手动设置百分比（如 `width: 33.33%`），无法灵活适应内容变化。
3. **多列对齐**：浮动布局中，各列高度因内容不同而参差不齐，需额外处理。
4. **动态适配**：容器尺寸或内容变化时，调整困难，常需 hack（如添加冗余标记）。

**结论**：传统布局效率低、适配性差，已无法满足现代 Web 开发对灵活性和响应式的需求。

## Flex 布局的重要概念

![image-20250227151411642](./assets/image-20250227151411642.png)

### 核心概念

- **两个角色**：
  - **Flex Container（弹性容器）**：通过 `display: flex` 或 `inline-flex` 定义的父元素，负责管理子元素的布局。
  - **Flex Item（弹性子项）**：容器内的直接子元素，自动成为 Flex 项目，受容器属性控制。
- **Flex Item 特性**：
  - **受控性 (Controlled)：** Flex 项目的排列、对齐和尺寸由 Flex 容器的属性统一管理，无需单独设置。
  - **灵活性 (Flexible)：** Flex 项目的行为超越了传统的块级元素和行内元素，可以根据容器的可用空间进行伸缩。
  - **自适应性 (Adaptive)：** 默认情况下，Flex 项目会根据自身内容调整大小，也可以通过 `flex` 属性精确控制其伸缩行为。
- **轴线系统**：Flexbox 基于两个轴线进行布局
  - **主轴（Main Axis）**：由 `flex-direction` 定义的排列方向，默认为水平（从左到右）。
  - **交叉轴（Cross Axis）**：垂直于主轴的方向，默认为垂直。
  - **起止点**：
    - 主轴：`main-start`（主轴起点） -> `main-end`（主轴终点）
    - 交叉轴：`cross-start`（交叉轴起点） -> `cross-end`（交叉轴终点）
  - **尺寸术语**：
    - `main size`：子项在主轴上的占用空间（如宽度或高度）。
    - `cross size`：子项在交叉轴上的占用空间。
- **特性**：
  - 子项的 `float`、`clear` 和 `vertical-align` 属性在 Flex 布局中失效。
  - 提供更高的自由度，超越传统块级（`block`）与行内（`inline`）限制。

### 如何创建 Flex Container？

通过 CSS 的 `display` 属性启用：

- **`display: flex;`**：创建块级 Flex 容器。该容器会占据一行，类似于块级元素。
- **`display: inline-flex;`**：创建行内 Flex 容器。该容器可以与其他行内元素并排显示，类似于行内元素。

## Flex 布局模型

Flex 布局基于**主轴（Main Axis）**和**交叉轴（Cross Axis）**的二维坐标系：

- **主轴**：由 `flex-direction` 定义，默认排列方向（如水平或垂直）。
- **交叉轴**：垂直于主轴，受 `align-items` 和 `align-content` 控制对齐方式。
- **起止点**：
  - 主轴：`main-start` → `main-end`。
  - 交叉轴：`cross-start` → `cross-end`。

![flex_terms](./assets/flex_terms.png)

![image-20250227145635206](./assets/image-20250227145635206.png)

## Flex 相关属性

Flexbox 属性可以分为两类：应用于 **Flex 容器** 的属性和应用于 **Flex 项目** 的属性。

### 应用于 Flex Container 的属性

- **`flex-direction`**：定义主轴方向。
- **`flex-wrap`**：控制子项是否换行。
- **`flex-flow`**：`flex-direction` 和 `flex-wrap` 的简写。
- **`justify-content`**：调整主轴上的对齐和间距。
- **`align-items`**：调整交叉轴上单行子项的对齐。
- **`align-content`**：调整交叉轴上多行子项的对齐（需配合 `flex-wrap`）。

### 应用于 Flex Item 的属性

- **`flex-grow`**：剩余空间的分配比例。
- **`flex-shrink`**：空间不足时的收缩比例。
- **`flex-basis`**：定义了 Flex 项目在主轴方向上的初始大小，作为伸缩的基准。
- **`flex`**：上述三者的简写。
- **`order`**：定义了 Flex 项目的排列顺序。
- **`align-self`**：覆盖单个子项的交叉轴对齐。

## 核心属性详解

### **`flex-direction`**

- **作用**：定义主轴方向，决定 Flex Item 的排列顺序。
- **取值**：
  - `row`（默认）：水平从左到右，适合横向导航栏。
  - `row-reverse`：水平从右到左，反向排列。
  - `column`：垂直从上到下，常用于垂直堆叠布局。
  - `column-reverse`：垂直从下到上，适用于倒序列表。

![image-20250227151553004](./assets/image-20250227151553004.png)

### **`flex-wrap`**

- **作用**：控制 Flex 项目是否换行，以及如何换行。解决在 Flex 容器空间不足时，Flex 项目的布局问题。
- **取值**：
  - `nowrap`（默认）：强制单行，子项可能溢出或压缩。
  - `wrap`：多行排列，从上到下，适合图片网格。
  - `wrap-reverse`：多行排列，从下到上，反向堆叠。
- **示例**：`flex-wrap: wrap;` 让过多子项自然换行，避免挤压。

![image-20250227151612883](./assets/image-20250227151612883.png)

### **`flex-flow`**

- **作用**：`flex-direction` 和 `flex-wrap` 的简写。
- **语法**：`flex-flow: <direction> <wrap>;`（顺序随意，可省略任一值）。
- **默认值**：`row nowrap`。
- **示例：** `flex-flow: row wrap;` 将主轴方向设置为水平，并允许 Flex 项目换行。

##  **`justify-content`**

- **作用**：控制主轴上 Flex Item 的对齐与间距分配。
- **取值**：
  - `flex-start`（默认）：靠主轴起点对齐（如左对齐）。
  - `flex-end`：靠主轴终点对齐（如右对齐）。
  - `center`：居中对齐。
  - `space-between`：首尾贴边，中间均分。
  - `space-around`：每项两侧间距相等（首尾间距为中间一半）。
  - `space-evenly`：所有间距完全相等（含首尾）。

![image-20250227151644732](./assets/image-20250227151644732.png)

### **`align-items`**

- **作用**：控制交叉轴上单行 Flex Item 的对齐方式。
- **取值**：
  - `stretch`（默认）：拉伸填满交叉轴（需无固定高度）。
  - `flex-start`：靠交叉轴起点对齐。
  - `flex-end`：靠交叉轴终点对齐。
  - `center`：居中对齐。
  - `baseline`：按首行文字基线对齐。
- **示例**：`align-items: center;` 实现单行子项垂直居中。

![image-20250227151702237](./assets/image-20250227151702237.png)

### **`align-content`**

- **作用**：控制交叉轴上多行 Flex Item 的对齐与间距（需配合 `flex-wrap: wrap`）。
- **取值**：
  - `stretch`（默认）：拉伸填满交叉轴。
  - `flex-start`：靠交叉轴起点对齐。
  - `flex-end`：靠交叉轴终点对齐。
  - `center`：居中对齐。
  - `space-between`：首尾贴边，中间均分。
  - `space-around`：每行周围间距相等。
- **示例**：`align-content: space-around;` 多行网格均匀分布。
- **注意**：若只有一行，该属性无效。

![image-20250227151716874](./assets/image-20250227151716874.png)

## Flex Item 属性详解

### **`order`**

- **作用**：调整 Flex Item 的排列顺序，默认值为 `0`，值越小越靠前。
- **示例**：`order: 1;` 将元素移至后面。

![image-20250227151734570](./assets/image-20250227151734570.png)

## `flex items`

![image-20250227151913195](./assets/image-20250227151913195.png)

### **`flex-grow`**

- **作用**：定义剩余空间分配比例，默认值为 `0`（不分配）。
- **示例**：：** 如果 Flex 容器有 300px 的剩余空间，`flex-grow: 2` 的 Flex 项目将分配到 200px 的空间，而 `flex-grow: 1` 的 Flex 项目将分配到 100px 的空间。

![image-20250227151928440](./assets/image-20250227151928440.png)

##  `flex-shrink`

- **作用：**  定义了 flex 元素如何在空间不足时收缩
  * 接受任意非负数值（正整数、正小数或 0），默认值为 `1`。
  * 仅当 flex 元素在主轴（main axis）方向的总尺寸超出 flex 容器大小时生效。

- **收缩计算公式**
  * 若所有 flex 元素的 `flex-shrink` 值之和大于 1，则每个元素的收缩尺寸为：**超出容器尺寸 × 该元素的收缩比例 ÷ 所有元素的收缩比例之和**。
  * 例如：容器溢出 100px，元素 A 的 `flex-shrink` 为 2，元素 B 为 1，总和为 3，则 A 收缩 66.67px，B 收缩 33.33px。
  
- **约束条件**
  * 收缩后的最终尺寸不会小于元素的 `min-width` 或 `min-height`。

---

##  `flex-basis`

- **作用**：指定子项在主轴上的基准尺寸，作为伸缩计算起点。
  
- **取值**：
  - `auto`（默认）：根据内容或 `width`/`height` 确定。
  - 具体值（如 `100px`、`20%`）：显式设置。
- **优先级**（从高到低）：
  1. `max-width` / `max-height` 或 `min-width` / `min-height`（约束边界）；  
  2. `flex-basis`（显式设置的基准值）；  
  3. `width` / `height`（传统尺寸属性）；  
  4. 内容本身的固有尺寸（无显式设置时）。  
- **作用**  
  - 在分配剩余空间或计算收缩前，`flex-basis` 作为元素的初始大小参考。

---

## `flex`（简写）

- **`flex` 是 `flex-grow`、`flex-shrink` 和 `flex-basis` 的简写**  
  - 可指定 1 个、2 个或 3 个值，语法灵活但有严格规则。  

- **单值语法**  
  - `<number>`（无单位数，如 `2`）：视为 `flex-grow`，`flex-shrink` 默认为 1，`flex-basis` 默认为 0。  
  - 有效宽度值（如 `100px`）：视为 `flex-basis`，`flex-grow` 和 `flex-shrink` 默认为 1。  
  - 关键字：  
    - `none`：等同于 `0 0 auto`（不伸缩）；  
    - `auto`：等同于 `1 1 auto`（默认伸缩）；  
    - `initial`：等同于 `1 0 0`（初始值）。  

- **双值语法**  
  - 第一个值：`<number>`（如 `2`），视为 `flex-grow`。  
  - 第二个值：  
    - `<number>`（如 `3`）：视为 `flex-shrink`，`flex-basis` 默认为 0；  
    - 有效宽度值（如 `50%`）：视为 `flex-basis`，`flex-shrink` 默认为 1。  

- **三值语法**  
  - 第一个值：`<number>`（如 `1`），视为 `flex-grow`。  
  - 第二个值：`<number>`（如 `2`），视为 `flex-shrink`。  
  - 第三个值：有效宽度值（如 `200px`），视为 `flex-basis`。  

- **示例**  
  - `flex: 1` → `flex: 1 1 0`  
  - `flex: 2 50px` → `flex: 2 1 50px`  
  - `flex: 0 0 100px` → 固定尺寸，不伸缩。

### **`align-self`**

- **作用**：覆盖单个子项在交叉轴上的对齐方式，优先级高于 `align-items`。

- **取值**：与 `align-items` 一致，另加 `auto`（默认，继承容器 `align-items`）。

- **示例**：

  ```css
  .item {
    align-self: flex-end; /* 靠交叉轴底端对齐 */
  }
  ```
