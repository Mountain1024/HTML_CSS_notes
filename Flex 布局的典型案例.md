## Flex 布局的典型案例

### 1. 水平垂直居中
**场景**：元素在容器中实现水平和垂直居中  
**实现**：利用 `justify-content` 和 `align-items` 属性  

```css
.container {
  display: flex;
  justify-content: center; /* 主轴居中 */
  align-items: center;     /* 交叉轴居中 */
  height: 300px;
}
```

### 2. 等宽导航栏
**场景**：多个导航按钮在容器中等宽分布  
**实现**：通过 `flex: 1` 让子项自动平分剩余空间  
```css
.nav {
  display: flex;
}
.nav-item {
  flex: 1; /* 等价于 flex: 1 1 0 */
  text-align: center;
}
```

### 3. 自适应双栏布局
**场景**：左侧固定宽度，右侧自适应填充  
**实现**：通过 `flex-grow` 控制扩展比例  
```html
<div class="container">
  <aside class="sidebar">200px</aside>
  <main class="content">Auto</main>
</div>
```
```css
.container {
  display: flex;
}
.sidebar {
  flex: 0 0 200px; /* 禁止伸缩 */
}
.content {
  flex: 1; /* 占据剩余空间 */
}
```

### 4. 响应式表单布局
**场景**：标签与输入框垂直对齐  
**实现**：通过 `align-items: baseline` 实现基线对齐  
```css
.form-row {
  display: flex;
  align-items: baseline;
  margin-bottom: 1rem;
}
.label {
  flex: 0 0 120px;
}
.input {
  flex: 1;
}
```

### 5. 圣杯布局（页脚置底）
**场景**：页面内容不足时页脚自动置底  
**实现**：通过 `flex-direction: column` 结合 `flex-grow`  
```css
body {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
.main-content {
  flex: 1; /* 填充剩余空间 */
}
.footer {
  margin-top: auto;
}
```

### 6. 卡片等高等分布局
**场景**：多列卡片等高且等宽分布  
**实现**：`flex-wrap` 结合 `align-items: stretch`  
```css
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
.card {
  flex: 1 1 300px; /* 最小300px，自动换行 */
  display: flex;
  flex-direction: column;
}
```

### 7. 瀑布流布局
**场景**：多列不等高元素自动排列  
**实现**：`flex-direction: column` 结合 `flex-wrap`  
```css
.waterfall {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  max-height: 1200px;
}
.item {
  width: 33.33%;
  padding: 10px;
}
```

### 8. 动态排序布局
**场景**：通过 `order` 属性调整元素顺序  
```css
.item:nth-child(1) { order: 3; }
.item:nth-child(2) { order: 1; }
.item:nth-child(3) { order: 2; }
```

### 9. 间距控制布局
**场景**：元素间自动分配间距  
**实现**：使用 `justify-content: space-between`  
```css
.toolbar {
  display: flex;
  justify-content: space-between;
  padding: 10px;
}
```

### 10. 图文混排布局
**场景**：图片与文字自适应排列  
```css
.media {
  display: flex;
  align-items: flex-start;
  gap: 15px;
}
.media-image {
  flex: 0 0 200px;
}
.media-content {
  flex: 1;
}
```

**关键特性应用总结表**：
| 案例         | 核心属性                         | 布局特点         |
| ------------ | -------------------------------- | ---------------- |
| 水平垂直居中 | justify-content + align-items    | 完美居中         |
| 等宽导航栏   | flex: 1                          | 空间均分         |
| 自适应双栏   | flex-grow + flex-basis           | 固定+弹性        |
| 表单基线对齐 | align-items: baseline            | 文字基线对齐     |
| 页脚置底     | flex-direction: column + flex:1  | 高度自适应       |
| 卡片等高等分 | flex-wrap + align-items: stretch | 响应式等高等宽   |
| 瀑布流       | flex-wrap + max-height           | 多列动态排列     |
| 动态排序     | order                            | 可视化顺序控制   |
| 间距控制     | justify-content: space-between   | 智能间距分配     |
| 图文混排     | gap + align-items                | 媒体对象经典布局 |