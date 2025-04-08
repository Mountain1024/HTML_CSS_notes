# Grid 布局

## Grid 基础

### 什么是 Grid 布局？

CSS Grid 布局（简称 Grid）是 CSS 提供的一种强大的**二维布局系统**。它允许开发者将页面或组件划分为基于**行 (Row)** 与**列 (Column)** 的网格结构，通过 Grid，可以精确、灵活地将**网格项 (Grid Item)** 放置到预定义的**单元格 (Cell)** 或**区域 (Area)** 中。

> **对比 Flexbox**：Flexbox 主要用于**一维**布局（沿单条轴线排列项目），非常适合组件内部或简单的线性布局。Grid 则专注于**二维**布局，更适合整体页面结构或复杂的模块布局。两者可以而且经常结合使用。

## 基础概念

### Grid 核心术语

- **网格容器 (Grid Container)**：

  - 应用了 `display: grid` 或 `display: inline-grid` 的父元素。
  - 负责定义网格的结构（多少行、多少列、尺寸、间距）并控制其子项的默认排列方式。
  - **如何创建**：
    - `display: grid;`：创建块级网格容器（默认占据整行）。
    - `display: inline-grid;`：创建行内级网格容器（表现类似行内块元素，可与文本等同行排列）。

- **网格项 (Grid Item)**：

  - 网格容器的**直接子元素**。
  - 自动成为网格项，其布局受容器属性和自身属性共同控制。
  - **特性**:
    - 布局位置由 Grid 容器规则决定。
    - 即使是行内元素（如 `<span>`），也会表现得类似块级元素（可以设置尺寸、边距等）。
    - `float`, `clear`, `vertical-align`, `display: inline-block/table-cell`, 以及 `column-*` 属性对其 **无效**。

- **网格线 (Grid Line)**：

  - 构成网格结构的水平和垂直分隔线，是定义网格轨道和区域的基础。
  - 一个 `n` 行 `m` 列的网格，包含 `(n + 1)` 条水平网格线和 `(m + 1)` 条垂直网格线。
  - 网格线可以通过数字索引（从 1 开始）引用，也可以赋予自定义名称。

  ![CSS grid](E:\@Ing\HTML_CSS_notes\assets\1_bg2019032503.png)

- **网格轨道 (Grid Track)**：

  - 两条相邻网格线之间的空间，即**一行**或**一列**。

- **网格单元格 (Grid Cell)**：

  - 由四条相邻的水平和垂直网格线围成的**最小单位**，是放置网格项的基本空间。

- **网格区域 (Grid Area)**：

  - 由任意**四条指定的网格线**（不必相邻）包围的**矩形区域**。一个区域可跨越多个单元格，用于放置单个网格项。

## Grid 属性概览

Grid 属性分为两类：

1. **应用于网格容器 (Grid Container)**：定义网格整体结构、隐式规则、间距和对齐。
2. **应用于网格项 (Grid Item)**：控制单个子项在网格中的位置、跨度、对齐和顺序。

### 应用于 Grid Container 的属性

- **定义网格结构**:
  - `grid-template-columns`：定义列轨道的数量和尺寸。
  - `grid-template-rows`：定义行轨道的数量和尺寸。
  - `grid-template-areas`：通过命名区域可视化地定义网格布局。
  - `grid-template`：以上三者的简写形式。
- **定义隐式网格**: (当项目数量超出显式定义的网格时)
  - `grid-auto-columns`：定义自动生成的列（隐式列）的尺寸。
  - `grid-auto-rows`：定义自动生成的行（隐式行）的尺寸。
  - `grid-auto-flow`：控制自动放置项的排列方式（`row`, `column`, `dense`）。
- **定义间距 (Gutters)**:
  - `gap`：同时设置行和列的间距 (`row-gap column-gap`)。
  - `row-gap`：设置行与行之间的间距。
  - `column-gap`：设置列与列之间的间距。
  - *注：`grid-gap`, `grid-row-gap`, `grid-column-gap` 是旧语法，建议使用无 `grid-` 前缀的新语法。*
- **对齐网格内容 (Tracks)**: (当网格总尺寸小于容器时)
  - `justify-content`：整个网格在容器内的**水平**对齐方式。
  - `align-content`：整个网格在容器内的**垂直**对齐方式。
  - `place-content`：`align-content` 和 `justify-content` 的简写。
- **对齐网格项 (Items)**: (在它们所在的 Grid Area 内)
  - `justify-items`：设置所有网格项在其单元格/区域内的**水平**默认对齐。
  - `align-items`：设置所有网格项在其单元格/区域内的**垂直**默认对齐。
  - `place-items`：`align-items` 和 `justify-items` 的简写。

### 应用于 Grid Item 的属性

- **定位与跨度**:
  - `grid-column-start` / `grid-column-end`：定义项目占据的起始/结束**列**网格线。
  - `grid-row-start` / `grid-row-end`：定义项目占据的起始/结束**行**网格线。
  - `grid-column`：`grid-column-start` / `grid-column-end` 的简写。
  - `grid-row`：`grid-row-start` / `grid-row-end` 的简写。
  - `grid-area`：通过名称引用 `grid-template-areas` 中定义的区域，或作为以上四个属性的简写。
- **自身对齐**:(覆盖容器的 `*-items` 设置)
  - `justify-self`：单独设置该项在其单元格/区域内的**水平**对齐。
  - `align-self`：单独设置该项在其单元格/区域内的**垂直**对齐。
  - `place-self`：`align-self` 和 `justify-self` 的简写。
- **顺序**:
  - `order`：(与 Flexbox 类似) 控制自动布局项目的排列顺序，但不推荐在 Grid 中过多依赖它来改变二维位置，优先使用显式放置。

## Grid Container 属性详解

### 定义显式网格轨道

#### `grid-template-columns` 和 `grid-template-rows`

- **作用**：定义网格的列和行的大小（轨道尺寸）。

- **语法**：使用空格分隔的值列表，每个值定义一个轨道的尺寸。

- **常用值**:

  - **长度单位**: `px`, `em`, `rem` 等。
  - **百分比**: `%` (相对于网格容器的**内容区域**尺寸)。
  - **`auto`**: 由内容或可用空间决定尺寸。
  - **`fr` 单位 (fraction)**：表示网格容器中**可用空间**的一份。极其灵活，用于创建按比例分配空间的弹性布局 (例如 `1fr 2fr` 表示第一列占可用空间的 1/3，第二列占 2/3)。
  - **`minmax(min, max)`**: 定义一个尺寸范围，轨道尺寸不会小于 `min`，也不会大于 `max`。例如 `minmax(100px, 1fr)` 表示最小 100px，最大可扩展到占据一份可用空间。
  - **`repeat(count, tracks)`**: 重复定义轨道。
    - `repeat(3, 100px)` 等同于 `100px 100px 100px`。
    - `repeat(auto-fill, minmax(150px, 1fr))`：**响应式神器**。自动填充尽可能多的列，每列最小 150px，并弹性分配剩余空间。`auto-fill` 即使空间不足以放下新列也会创建空的轨道，而 `auto-fit` 会将空轨道折叠为 0，使现有列扩展填充空间。
  - **`fit-content(limit)`**: 将轨道尺寸限制在 `limit` 值以内，但允许其根据内容收缩。

- **示例**:

  ```css
  .container {
    display: grid;
    /* 3 列: 固定 150px | 最小 100px, 最大 1fr | 占 2份 剩余空间 */
    grid-template-columns: 150px minmax(100px, 1fr) 2fr;
    /* 2 行: 内容决定高度 | 固定 50px */
    grid-template-rows: auto 50px;
    /* 使用 repeat 创建自适应列 */
    /* grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); */
  }
  ```

#### 命名网格区域：`grid-template-areas`

- **作用**：提供一种极其直观、可视化的方式来定义网格布局，并将网格项放置到指定区域。

- **工作流程**:

  1. **命名项**: 在每个需要放置的 Grid Item 上使用 `grid-area: <自定义名称>;` 指定一个名字。
  2. **定义区域**: 在 Grid Container 上使用 `grid-template-areas`，值为用**引号**包裹的字符串列表。
      - 每个字符串代表**一行**。
      - 字符串内用**空格分隔**的名称定义了该行的列如何分配给各个区域。
      - 使用 **`.`** (英文句点) 表示该单元格为空，不属于任何区域。

- **规则**：

  - 同一名称定义的所有单元格必须形成一个**连续的矩形**区域。
  - 每个字符串（行）中的名称/`.`数量必须与 `grid-template-columns` 定义的**列数**完全一致。

- **示例**:

  ```css
  .container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
      "header header header"
      "sidebar main main"
      "footer footer footer";
  }
  
  .header { grid-area: header; }
  .sidebar { grid-area: sidebar; }
  .main { grid-area: main; }
  .footer { grid-area: footer; }
  ```

  这个例子定义了一个经典的三列布局：顶部是横跨三列的 header，中间是占一列的 sidebar 和占两列的 main content，底部是横跨三列的 footer。

#### 网格模板简写：`grid-template`

- **作用**：`grid-template-rows`, `grid-template-columns`, 和 `grid-template-areas` 的简写。
- **语法**：其语法较为复杂，可以组合定义行、列和区域。
  - `grid-template: <'grid-template-rows'> / <'grid-template-columns'>`
  - `grid-template: [ <line-names>? <string> <track-size>? <line-names>? ]+ [ / <explicit-track-list> ]?` (结合区域定义)
- **建议**：虽然功能强大，但为了代码的可读性和维护性，**通常推荐分开写** `grid-template-rows`, `grid-template-columns`, 和 `grid-template-areas`。

### 定义隐式网格和自动放置`grid-auto-*`

- **何时产生隐式网格？**

  - 当 Grid Item 的数量超过了 `grid-template-columns` 和 `grid-template-rows` 定义的显式单元格数量时。

  - 当某个 Grid Item 通过 `grid-column/row` 属性被放置到了显式网格范围之外时。

#### `grid-auto-columns` 和 `grid-auto-rows`

- **作用**：定义这些自动创建的（隐式）列和行的尺寸。

- **默认值**：`auto` (尺寸由内容决定)。

- **示例**:

  ```css
  .container {
    display: grid;
    grid-template-columns: 1fr 1fr; /* 显式定义 2 列 */
    /* 未显式定义行，所有行（包括第一行）都是隐式行 */
    grid-auto-rows: 100px; /* 所有自动创建的行高都为 100px */
    gap: 10px;
  }
  /* 如果有 4 个子项，它们会排成 2x2 网格，每行高 100px */
  ```

#### `grid-auto-flow`

- **作用**：控制没有明确指定位置的 Grid 项目（自动放置的项目）如何排列。
- **取值**:
  - `row` (默认): 按行依次填充，填满一行后换到下一行。
  - `column`: 按列依次填充，填满一列后换到下一列。
  - `dense`: 尝试填补网格中较早出现的空白单元格（可能导致项目顺序打乱）。

#### 设置网格间距：`gap`, `row-gap`, `column-gap`

- **作用**：设置网格线之间的间距（沟槽）。`grid-gap` 是旧的写法。
- **语法**:
  - `gap: <row-gap> <column-gap>;` (如果提供两个值)
  - `gap: <value>;` (如果行、列间距相同)
  - `row-gap: <value>;` (单独设置行间距)
  - `column-gap: <value>;` (单独设置列间距)
- **值**: 长度值 (`px`, `em`, `%`)。
- **关键特性**:
  - 间距**只存在于轨道之间**，不会在网格容器的边缘添加。
  - 使用 `gap` 比传统 `margin` 布局更简洁，避免了外边距合并和处理首尾元素边距的问题。

### 对齐 Grid Tracks (`justify-content`, `align-content`)

- **作用**：当网格的总尺寸（所有轨道尺寸 + 所有间距）**小于**其 Grid 容器的尺寸时，控制整个网格**作为一个整体**在容器内的对齐方式。
- **`justify-content`** (水平对齐，沿行轴):
  - `start`: 网格靠容器左侧对齐。
  - `end`: 网格靠容器右侧对齐。
  - `center`: 网格在容器中水平居中。
  - `stretch`: (如果轨道尺寸是 auto) 拉伸轨道以填满容器宽度 (需要轨道尺寸允许)。
  - `space-between`: 网格轨道两端对齐，轨道间距相等。
  - `space-around`: 每个网格轨道两侧的间距相等，导致轨道之间间距是边缘间距的两倍。
  - `space-evenly`: 所有轨道间距（包括与容器边缘的间距）完全相等。
- **`align-content`** (垂直对齐，沿列轴):
  - 值与 `justify-content` 类似 (`start`, `end`, `center`, `stretch`, `space-between`, `space-around`, `space-evenly`)，但作用于垂直方向。
- **`place-content`**: 简写属性，`place-content: <align-content> <justify-content>;`。如果只提供一个值，则两方向相同。

### 对齐 Grid Items (`justify-items`, `align-items`)

- **作用**：设置网格**内部所有项目**（内容）在其分配到的 Grid Area（通常是单元格）内的默认对齐方式。
- **`justify-items`** (水平对齐，沿行轴):
  - `start`: 项目靠其单元格左侧对齐。
  - `end`: 项目靠其单元格右侧对齐。
  - `center`: 项目在其单元格内水平居中。
  - `stretch` (默认): 项目拉伸以填满其单元格的宽度（如果未设置固定宽度）。
- **`align-items`** (垂直对齐，沿列轴):
  - `start`: 项目靠其单元格顶部对齐。
  - `end`: 项目靠其单元格底部对齐。
  - `center`: 项目在其单元格内垂直居中。
  - `stretch` (默认): 项目拉伸以填满其单元格的高度（如果未设置固定高度）。
  - `baseline`: 项目按其内容的基线对齐。
- **`place-items`**: 简写属性，`place-items: <align-items> <justify-items>;`。如果只提供一个值，则两方向相同。例如 `place-items: center;` 等同于 `align-items: center; justify-items: center;`。

## Grid Item 属性详解

这些属性设置在 Grid 项目（子元素）上，用于控制单个项目的位置、跨度和对齐。

### 定位与跨度

#### `grid-column-start`, `grid-column-end`, `grid-row-start`, `grid-row-end`

- **作用**：通过指定网格线的编号或名称，来定义一个 Grid Item 从哪条线开始，到哪条线结束，从而确定其在网格中的位置和跨度。

- **值**:

  - **数字**: 网格线的编号（从 1 开始，负数表示从末尾开始，-1 是最后一条线）。
  - **名称**: 如果在 `grid-template-columns/rows` 中定义了网格线名称。
  - **`span <number>`**: 表示项目跨越指定数量的轨道。
  - **`span <name>`**: 表示项目跨越到指定名称的网格线。
  - **`auto`**: 自动放置。

- **示例**:

  ```css
  .item-1 {
    /* 从第 2 条列线开始，到第 4 条列线结束 (覆盖第 2、3 列) */
    grid-column-start: 2;
    grid-column-end: 4;
    /* 从第 1 条行线开始，到第 3 条行线结束 (覆盖第 1、2 行) */
    grid-row-start: 1;
    grid-row-end: 3;
  }
  ```

#### `grid-column` 和 `grid-row`

- **作用**：分别是 `grid-column-start / grid-column-end` 和 `grid-row-start / grid-row-end` 的简写。

- **语法**: `<start-line> / <end-line>`。如果只提供一个值，则表示 `start-line`，`end-line` 默认为 `auto` (通常只占一个轨道)。

- **示例**:

  ```css
  .item-c {
    grid-column: 2 / 4; /* 等同于 grid-column-start: 2; grid-column-end: 4; */
    grid-row: 1 / 3;    /* 等同于 grid-row-start: 1; grid-row-end: 3; */
  }
  .item-d {
    grid-column: 1;     /* 只占第 1 列 */
    grid-row: span 2; /* 从自动放置的行开始，跨越 2 行 */
  }
  ```

#### `grid-area`

*   **用法 1: 引用命名区域**
    *   `grid-area: <name>;` - 将此项放置到 `grid-template-areas` 中定义的同名区域。这是最直观的用法。
*   **用法 2: 定位简写**
    *   `grid-area: <row-start> / <column-start> / <row-end> / <column-end>;` - 同时指定四条网格线。

- **示例**:

  ```css
  /* 用法 1 (接 4.2 示例) */
  header { grid-area: header; }
  
  /* 用法 2 */
  .item-special {
    /* 占据从第 2 行第 1 列 到 第 4 行第 3 列的区域 */
    grid-area: 2 / 1 / 4 / 3;
  }
  ```

### 单项对齐（覆盖）

#### `justify-self` 和 `align-self`

- **作用**：允许单个 Grid Item 覆盖其容器 `justify-items` 和 `align-items` 定义的默认对齐方式。
- **默认值**：`auto` (继承容器的 `justify-items`/`align-items` 值，通常是 `stretch`)。
- **值**: 与 `justify-items`/`align-items` 相同 (`start`, `end`, `center`, `stretch`, `baseline` (仅 align-self))，外加 `auto`。
- **示例**: 容器设置 `align-items: stretch;`，但某个项目设置 `align-self: center;`，则该项目会在其单元格内垂直居中，而不是拉伸。
- **`place-self`**: 简写属性，`place-self: <align-self> <justify-self>;`。

### 关键技巧与特性总结

1. **二维布局**: Grid 的核心是同时控制行和列，非常适合页面整体布局和复杂模块。
2. **`fr`** 单位: 实现弹性和比例布局的利器，自动分配可用空间。
3. **`minmax()`**: 创建尺寸灵活但有边界的轨道，对响应式设计很有用。
4. **`repeat()`**: 简化重复轨道的定义，`auto-fill` / `auto-fit` 结合 `minmax()` 可创建强大的响应式列布局。
5. **`grid-template-areas`**: 提供一种直观、可视化的方式来定义布局，特别适合复杂的、有明确区域划分的结构。
6. **显式放置 vs 自动放置**: 可以精确控制关键项目的位置 (`grid-column`/`row`/`area`)，让其他项目自动填充剩余空间 (`grid-auto-flow`)。
7. **`gap`** 属性: 简洁地处理项目间距，无需担心外边距合并或首尾元素问题。
8. **对齐控制**: Grid 提供了容器级别 (`justify/align-content`) 和项目级别 (`justify/align-items`, `justify/align-self`) 的全面对齐控制。
9. **内容与布局分离**: HTML 结构更干净，布局逻辑主要在 CSS 中。
10. **`subgrid`**: 允许嵌套的 Grid 容器继承其父 Grid 的轨道定义，使得内部元素可以与外部网格对齐（需要浏览器支持）。

### Grid 与 Flexbox 的选择

- **使用 Flexbox**:
  - 当你需要沿着**单条轴线**（行或列）排列元素时。
  - 用于组件内部元素的布局（如按钮组、导航项、卡片内的内容）。
  - 当内容优先，让项目根据内容自动伸缩和换行时。
  - 简单的等高列。
- **使用 Grid**:
  - 当你需要同时控制**行和列**的二维布局时。
  - 用于页面整体布局结构（页眉、页脚、侧边栏、主内容区）。
  - 需要精确控制项目的位置和跨度时。
  - 创建复杂的、非线性的网格结构。
  - 需要 `grid-template-areas` 提供的可视化布局方式时。
- **结合使用**: 两者并非互斥，常常结合使用。例如，使用 Grid 进行页面整体布局，然后在某个 Grid Area 内部使用 Flexbox 来排列该区域内的元素。

