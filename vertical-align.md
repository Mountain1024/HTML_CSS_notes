## vertical-align

`vertical-align` 属性影响 **行内级元素（inline-level elements）** 或 **行内块级元素（inline-block elements）** 在一个 **行盒（line box）** 中的垂直对齐方式。

### 基础思考：`div` 的高度从何而来？
- **问题**：一个 `div` 未设置高度时，会有高度吗？  
  - **无内容**：高度为 0。  
  - **有内容**：内容会撑起 `div` 的高度。  
- **本质**：  
  - 内容具有 **行高（line-height）**，撑起了 `div` 的高度。  
- **行高撑起高度的原因**：  
  - CSS 中存在 **行盒（line boxes）**，用于包裹一行中的所有 **行内级元素（inline-level elements）**。  
  - 文字等内容有行高，**line boxes** 必须完整包裹行高，才能正确包含这些元素。

### 进一步思考：
如果 `div` 中包含 **文字**、**图片**、**inline-block 元素**，甚至这些元素设置了 `margin` 等属性，会如何影响布局？

---

## 深入理解 vertical-align – 不同情况分析

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

---

## vertical-align 的基线（baseline）

- **核心结论**：  
  **line boxes** 会确保包裹当前行的所有内容。  
- **对齐看似复杂的原因**：  
  - 默认对齐方式是 `baseline`，不同元素的基线定义不同。  
- **什么是 baseline？**  
  - **文本**：字母 **x** 的底部。  
  - **inline-block（无文本）**：元素的 `margin-bottom` 底部（若无 `margin`，则是盒子底部）。  
  - **inline-block（有文本）**：最后一行文本的 **x** 的底部。

---

## vertical-align 的取值

以下为 `vertical-align` 的常见值及其含义（参考 MDN）：

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

---

## 解决图片下边缘间隙的方法

图片作为行内级元素时，常因基线对齐在底部产生间隙，可通过以下方法解决：  
1. 设置 `vertical-align: top`、`middle` 或 `bottom`。  
2. 将图片转为块级元素：`display: block`。

---

## 补充说明

- **行内级元素（inline-level elements）**：包括 `inline`、`inline-block`、`inline-table` 等。  
- **行盒（line box）**：CSS 布局中包裹一行内容的矩形区域。  
- **x-height**：小写字母 **x** 的高度，影响 `middle` 对齐计算。  

