# 表单

表单（Form）是网页中用于收集用户输入的交互控件集合，通过 HTTP 请求将数据发送至 Web 服务器进行处理。它广泛应用于注册、登录、搜索等场景。

## 常见元素

- `<form>`：表单容器，通常包含所有表单相关元素作为其后代。
- `<input>`：多功能输入控件，支持多种类型，如单行文本、密码、单选框、复选框、按钮等。
- `<textarea>`：多行文本输入框，适用于长文本输入。
- `<select>` 和 `<option>`：下拉选择框，提供选项列表。
- `<button>`：按钮，用于触发提交、重置等操作。
- `<label>`：表单元素的标签，提升用户体验和可访问性。

## input 元素详解

### 常见属性

- `type`：定义输入类型：
  - `text`：单行文本输入（明文，如用户名）。
  - `password`：密码输入（密文，隐藏字符）。
  - `radio`：单选框（互斥选择，如性别）。
  - `checkbox`：复选框（多选，如兴趣）。
  - `button`：普通按钮（无默认行为）。
  - `reset`：重置按钮，清空表单内控件的值。
  - `submit`：提交按钮，将数据发送至服务器。
  - `file`：文件上传控件。
  - `date`：日期选择器。
  - `time`：时间选择器。
- `readonly`：只读，允许选中但不可编辑。
- `disabled`：禁用，控件不可交互且不提交数据。
- `checked`：默认选中，仅适用于 `radio` 或 `checkbox`。
- `autofocus`：页面加载时自动聚焦。
- `name`：控件名称，用于服务器端识别数据。
- `value`：默认值或用户输入值。
- `required`：必填，提交前需验证。
- `placeholder`：占位提示文本，输入前显示。

> HTML 表单是用于收集用户输入的一种网页元素，它可以包含文本框、单选按钮、复选框、下拉列表等不同类型的控件。HTML 表单的基本结构如下：
>
> ```html
> <form action="action_page.php" method="post">
>   <!-- 表单控件 -->
> </form>
> ```
>
> - `<form>` 元素定义了一个表单，它的 `action` 属性指定了 **表单数据提交的目标地址**，`method` 属性指定了 **提交数据的 HTTP 方法**（`get` 或 `post`）。
> - `<input>` 元素是最常用的表单控件之一，它可以创建不同类型的输入框，如文本框、密码框、单选按钮、复选框等。`type` 属性定义了输入框的类型，`name` 属性定义了输入框的名称，`value` 属性定义了输入框的默认值。
> - `<label>` 元素用于为表单控件添加标签，它的 `for` 属性指定了要关联的控件的 `id` 属性。
> - `<select>` 元素用于创建下拉列表，它包含了多个 `<option>` 元素，每个 `<option>` 元素定义了一个可选项。
> - `<textarea>` 元素用于创建多行文本输入框，它的 `rows` 和 `cols` 属性定义了文本框的大小。
> - `<button>` 元素用于创建按钮，它的 `type` 属性定义了按钮的功能，如提交表单、重置表单等。
>
> 下面是一个简单的 HTML 表单的例子，它包含了文本框、密码框、单选按钮、复选框、下拉列表和按钮：
>
> ```html
> <form action="/" method="post">
>   <!-- 文本输入框 -->
>   <label for="name">用户名:</label>
>   <input type="text" id="name" name="name" required />
>   <br />
>   <!-- 密码输入框 -->
>   <label for="password">密码:</label>
>   <input type="password" id="password" name="password" required />
>   <br />
>   <!-- 单选按钮 -->
>   <label>性别:</label>
>   <input type="radio" id="male" name="gender" value="male" checked />
>   <label for="male">男</label>
>   <input type="radio" id="female" name="gender" value="female" />
>   <label for="female">女</label>
>   <br />
>   <!-- 复选框 -->
>   <input type="checkbox" id="subscribe" name="subscribe" checked />
>   <label for="subscribe">订阅推送信息</label>
>   <br />
>   <!-- 下拉列表 -->
>   <label for="country">国家:</label>
>   <select id="country" name="country">
>     <option value="cn">CN</option>
>     <option value="usa">USA</option>
>     <option value="uk">UK</option>
>   </select>
>   <br />
>   <!-- 提交按钮 -->
>   <button type="submit">提交</button>
> </form>
> ```
>

### 表单验证与交互

HTML5 提供了内置验证属性，增强表单功能：

- `pattern`：正则表达式验证，例如 `<input type="text" pattern="[A-Za-z]{3,}" />`（仅字母，3+字符）。
- `min` / `max`：限制范围，例如 `<input type="number" min="1" max="100" />`。
- 事件支持：通过 `onchange` 或 `onsubmit` 添加交互逻辑。

## 布尔类型

布尔属性是只需要出现属性名即可生效的特殊属性，常见的包括：

- `disabled`：禁用控件。
- `checked`：默认选中。
- `readonly`：只读模式。
- `multiple`：允许多选（适用于 `<select>`）。
- `autofocus`：自动聚焦。
- `selected`：默认选中（适用于 `<option>`）。

**特性**：

- 无需显式赋值，写上属性名即表示启用。
- 若赋值，则值须与属性名相同，例如 `<input disabled="disabled" />`。

```html
<input type="checkbox" checked /> <!-- 默认选中 -->
<input type="text" disabled="disabled" /> <!-- 禁用，等效于 disabled -->
```

## 表单按钮

按钮可以通过 `<button>` 或 `<input>` 实现，具体类型由 `type` 属性定义：

- `type="button"`：普通按钮，无默认行为，通常与 JavaScript 事件绑定使用。
- `type="reset"`：重置按钮，清空表单所有控件的值。
- `type="submit"`：提交按钮，将表单数据发送至服务器。

![image-20231218212736961](./assets/image-20231218212736961.png)

也可以通过按钮来实现：

![image-20231218212804988](./assets/image-20231218212804988.png)

`type="button"` 是没有默认行为的按钮，通常脚本指定 `click` 事件的监听函数来使用。

```html
<input type="button" value="点击">
```

**推荐使用 `<button>`**：

- `<button> `支持嵌套内容（如图标或多行文本），语义更清晰。
- `<input type="button">` 仅支持 `value` 属性显示文本。

```html
<button type="button"><img src="icon.png" alt="图标" /> 点击</button>
<input type="button" value="点击" />
```

## `<input>` 与 `<label>` 协作

`<label>` 为控件提供描述，并通过 `for` 属性绑定 `<input>` 的 `id`，点击标签可激活对应控件：

![image-20231218212939411](./assets/image-20231218212939411.png)

## 单选框 (radio)

通过将 `<input>` 的 `type` 设置为 `radio` 创建单选框：

- 同一组单选框需共享相同的 `name` 属性以实现互斥选择。

```html
<fieldset>
  <legend>年级选择</legend>
  <input type="radio" id="grade1" name="grade" value="1" checked />
  <label for="grade1">一年级</label>
  <input type="radio" id="grade2" name="grade" value="2" />
  <label for="grade2">二年级</label>
</fieldset>
```

> **提示**：`<fieldset>` 和 `<legend>` 可为单选组添加语义化分组。

## 复选框 (checkbox)

- 将 `<input>` 的 `type` 设置为 `checkbox` 创建复选框：
  - 同类复选框建议使用相同的 `name` 属性，便于数据分组处理。

```html
<div>
  爱好：
  <label for="basketball">
    篮球 <input id="basketball" type="checkbox" name="hobby" value="basketball">
  </label>
  <label for="football">
    足球 <input id="football" type="checkbox" name="hobby" value="football">
  </label>
  <label for="run">
    跑步 <input id="run" type="checkbox" name="hobby" value="run">
  </label>
</div>
```

## `<textarea>`的使用

`<textarea>` 用于多行文本输入，常用属性包括：

- `cols`：可见列数。
- `rows`：可见行数。

**缩放控制（CSS）**：

- `resize: none`：禁止缩放。
- `resize: horizontal`：仅水平缩放。
- `resize: vertical`：仅垂直缩放。
- `resize: both`：水平垂直均可缩放。

```html
<textarea name="comment" rows="4" cols="50" style="resize: vertical;">默认文本</textarea>
```

## select 和 option 的使用

`<select>` 创建下拉列表，`<option>` 定义每个选项：

- `<select>` 属性：
  - `multiple`：支持多选（需配合 Ctrl 或 Shift）。
  - `size`：可见选项数量。
- `<option>` 属性：
  - `selected`：默认选中。

```html
<select name="fruits" multiple size="3">
  <option value="apple">苹果</option>
  <option value="banana" selected>香蕉</option>
  <option value="orange">橙子</option>
</select>
```

## form 常见的属性

form 常见的属性如下:

- `action`：用于 **提交表单数据的请求 URL**
- `method`：HTTP 请求方法（`get` 或 `post`）
  - get：数据附加在 URL 中，适合简单查询。
  - post：数据以请求体发送，适合复杂或敏感数据。
- `target`：提交后页面打开方式（如 `_blank`、`_self`）。

## 请求方式的对比

| 特性         | GET                             | POST                          |
| ------------ | ------------------------------- | ----------------------------- |
| 数据位置     | URL 查询字符串                  | HTTP 请求体                   |
| 数据大小限制 | 受 URL 长度限制(2048 字符)      | 无限制                        |
| 安全性       | 不安全（敏感数据暴露在 URL 中） | 更安全（数据不在 URL 中显示） |
| 缓存支持     | 支持                            | 不支持                        |

![image-20231218213341832](./assets/image-20231218213341832-1702906632679-1.png)
