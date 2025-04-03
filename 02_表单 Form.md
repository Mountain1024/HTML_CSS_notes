# 表单 (Forms)

表单是网页中用于**收集用户输入**的交互控件集合，通过 HTTP 请求将数据发送至 Web 服务器进行处理。它广泛应用于注册、登录、搜索等场景。

##  **表单容器: `<form>` 元素**

`<form>` 元素是所有表单控件的容器，元素定义了表单的整体行为，特别是数据提交的目标地址和方式。

```html
<form action="表单提交地址" method="提交方法" enctype="编码类型" novalidate autocomplete="on">
    <!-- 表单控件放置于此 -->
</form>
```

**核心属性:**

-   **`action`**: (必需) 指定接收并处理表单数据的服务器端 **URL**。若省略或为空，则提交到当前页面 URL。
-   `method`: 指定提交数据使用的 **HTTP 方法** 。
    -   `get` (默认): 将表单数据作为 **URL 查询参数** 追加到 `action` URL 后面 (`?key=value&key2=value2...`)。
        *   数据在 URL 中可见。
        *   长度受 URL 限制 (通常约 2KB)。
        *   适合用于**获取/查询**数据（如搜索），因为请求是幂等的且可被缓存/收藏。
    -   `post`: 将表单数据包含在 HTTP 请求的**请求体 (Request Body)** 中发送。特点：
        *   数据不在 URL 中可见，更安全（尤其配合 HTTPS）。
        *   理论上没有数据长度限制。
        *   适合用于**创建/更新**资源或提交敏感信息（如密码、大量文本、文件上传）。
-   `enctype`: **当 `method="post"` 时**，指定数据的编码类型。
    -   `application/x-www-form-urlencoded` (默认): 标准编码，空格转 `+`，特殊字符 URL 编码。
    -   `multipart/form-data`: **文件上传时必需**。不进行字符编码，允许传输二进制数据。
    -   `text/plain`: (HTML5) 数据以纯文本发送，基本不编码（较少使用）。
-   `target`: 指定在何处显示响应 (`_self`, `_blank` 等)。
-   `novalidate`: **布尔属性**。禁用浏览器内置的 HTML5 表单验证功能，允许表单直接提交，即使存在格式错误或必填项未填。
-   **`autocomplete`**: 控制表单内控件是否默认启用浏览器自动填充 (`on` 或 `off`)。可在单个控件上覆盖。

```html
<form action="/submit-data" method="post" enctype="multipart/form-data" novalidate>
  <!-- 表单控件放置于此 -->
</form>
```

## **常用表单控件**

- `<form>`：表单容器，通常包含所有表单相关元素作为其后代。
- `<input>`：最通用的输入控件，通过 `type` 属性区分多种形态。
- `<textarea>`：多行文本输入框，适用于长文本输入。
- `<select>` 与 `<option>`: 创建下拉选择列表。`<optgroup>` 可对选项分组。
- `<button>`：按钮，用于触发提交、重置等操作。
- `<label>`：表单元素的标签，提升用户体验和可访问性。
- `<fieldset>` 与 `<legend>`: 将相关控件分组并提供分组标题。
- `<datalist>`: 提供预定义选项列表，与 `<input>` 结合实现输入建议。

## `<input>` 元素详解

`<input>` 元素是表单中最通用的元素，其行为主要由 `type` 属性决定。

### 常用 `type` 类型

**文本输入:**

- `text`：单行文本输入（明文，如用户名）。
- `password`：密码输入（密文，隐藏字符）。
- `email`, `url`: 特定格式输入的文本框 (提供基础格式验证)。
- `search`: 搜索框，样式可能略有不同（如带清除按钮），语义化。
- `tel`: 电话号码输入框（不强制格式，便于移动端调起数字键盘）

**选择类:**

- `radio`: **单选按钮**。同一组（name 相同）中只能选一个。
- `checkbox`: **复选框**。允许选择零个或多个。

**按钮类:**

- `button`: **普通按钮**。无默认行为，通常用于 JavaScript 交互。
- `submit`: **提交按钮**。点击触发表单提交。
- `reset`: **重置按钮**。将表单内所有控件恢复到初始值。
- `image`: **图像提交按钮**。使用 `src` 指定图片，点击图片提交表单，并附带点击坐标 (`x`, `y`)。



- `file`: 文件选择控件，用于上传文件（需配合 `<form>` 的 `enctype="multipart/form-data"`）。
- `date`, `time`, `datetime-local`, `month`, `week`: 日期/时间选择器。
- `number`: 数值输入框，可限制范围 (`min`, `max`) 和步长 (`step`)。
- `hidden`  隐藏输入域。用户不可见，但其 `name` 和 `value` 会随表单提交。常用于传递 ID、Token、状态值等无需用户交互的数据。
- `range`: 滑块控件，用于在指定范围 (`min`, `max`) 内选择一个值。
- `color`: 颜色选择器。

### 常用属性

- `name`: (对需提交数据的控件 **必需**) 定义控件的名称，作为提交数据时的键 (`key`)，供服务器端识别。
- `value`: 控件的初始值或提交时的值。
  -   文本类：输入框的初始内容。
  -   `radio`/`checkbox`：选中时提交给服务器的那个选项的值。
  -   按钮类 (`<input>`)：按钮上显示的文本。
  -   `hidden`：要提交的隐藏数据值。
- `id`: 元素的唯一标识符，主要用于 `<label>` 的 `for` 属性关联、CSS 样式和 JavaScript 操作。。
-   `required`: (布尔属性) 标记为必填项，提交前浏览器会进行非空验证。
-   `readonly`: (布尔属性) 控件值**只读**，用户不能修改，但其值会随表单提交。
- `disabled`: (布尔属性) **禁用**控件。控件变灰、不可交互，其 `name` 和 `value` **不会**随表单提交。
-   `checked`: (布尔属性, 仅 `radio`/`checkbox`) 设置为默认选中状态。
- `autofocus`: (布尔属性) 页面加载时该控件自动获得焦点。
- `placeholder`: 输入框为空时的**占位提示文本**。
- `min`, `max`, `step`: (用于 `number`, `range`, 日期/时间类型) 定义允许的最小值、最大值和步长。
- `maxlength`: (用于文本类输入) 限制最大输入字符数。
- `accept`: (仅 `<input type="file">`) 指定允许上传的文件类型 (MIME 类型、文件扩展名、`audio/*`, `video/*`, `image/*`)。
- `pattern`: (用于文本相关 `type`) 提供一个正则表达式，输入值需匹配该模式才有效。配合 `title` 属性可提供格式提示。
- `multiple`: (布尔属性, 用于 `email`, `file`, `<select>`) 允许用户选择/输入多个值。
- `list`: (用于文本类 `<input>`) 关联一个 `<datalist>` 元素的 `id`，为输入框提供预定义选项建议。

## 布尔属性

布尔属性是只需要出现属性名即可生效的特殊属性，常见的包括：

- `checked` (用于 `radio`, `checkbox`)
- `selected` (用于 `<option>`)
- `disabled` (用于多数表单控件)
- `readonly` (用于 `input`, `textarea`)
- `required` (用于多数表单控件)
- `multiple` (用于 `<select>`, `input type="file"`, `input type="email"`)
- `autofocus` (用于可聚焦元素)
- `novalidate` (用于 `<form>`)
- `formnovalidate` (用于 `submit` 按钮)

**特性**：

- 无需显式赋值，写上属性名即表示启用。
- 若赋值，则值须与属性名相同，例如 `<input disabled="disabled" />`。

```html
<input type="checkbox" checked /> <!-- 默认选中 -->
<input type="text" disabled="disabled" /> <!-- 禁用，等效于 disabled -->
```

## `<textarea>` 多行文本框

**常用属性:**

*   `rows`: 指定可见行数（控制初始高度）。
*   `cols`: 指定可见列数（控制初始宽度）。
*   `maxlength`: 限制最大输入字符数。
*   `placeholder`, `required`, `readonly`, `disabled`, `autofocus` 等通用属性也适用。
*   `wrap`: (HTML5) 控制文本换行方式 (`soft` 默认，提交时不带换行符；`hard` 提交时带换行符，需配合 `cols`)。
*   **缩放控制 (CSS):** 通过 CSS 的 `resize` 属性控制其是否及如何允许用户调整尺寸 (`none`, `vertical`, `horizontal`, `both`)。

```html
<label for="bio">个人简介:</label><br>
<textarea id="bio" name="biography" rows="5" cols="50" placeholder="介绍一下你自己..." style="resize: vertical;"></textarea>
```



## 表单按钮：`<button>` vs `<input>`

创建按钮可以使用 `<button>` 元素或 `<input>` 元素（设置 `type` 为 `button`, `submit`, 或 `reset`）。

- `type="button"`：普通按钮，无默认行为，通常与 JavaScript 事件绑定使用。
- `type="reset"`：重置按钮，清空表单所有控件的值。
- `type="submit"`：提交按钮，将表单数据发送至服务器。

也可以通过按钮来实现：

```html
<!-- 推荐使用 <button> 元素 -->
<button type="submit">确认提交</button>
<button type="reset">重置表单</button>
<button type="button" onclick="doSomething()">自定义脚本按钮</button>

<!-- 使用 <input> 创建按钮 (旧式) -->
<input type="submit" value="提交">
<input type="reset" value="重置">
<input type="button" value="自定义操作" onclick="doSomething()">
```

`type="button"` 是没有默认行为的按钮，通常脚本指定 `click` 事件的监听函数来使用。

两者都能创建按钮，但 **强烈推荐使用 `<button>` 元素**:

*   **内容更灵活:** `<button>` 内部可以包含 HTML 内容（如 `<img>`, `<span>`），而 `<input>` 只能通过 `value` 显示纯文本。
*   **语义更清晰:** `<button>` 更明确地表示一个按钮。
*   **默认行为:** `<button>` 在 `<form>` 内若未指定 `type`，默认为 `type="submit"`。

## `<label>` 元素 - 控件标签

`<label>` 为表单控件提供描述性标签。它有两种主要关联方式：

* **显式关联 (推荐):** 使用 `for` 属性指向对应控件的 `id`。点击标签时，关联的控件会获得焦点。

  ```html
  <label for="username">用户名:</label>
  <input type="text" id="username" name="username">
  ```

* **隐式关联:** 将表单控件直接嵌套在 `<label>` 元素内部。此时无需 `for` 和 `id` 属性。

  ```html
  <label>用户名: <input type="text" name="username"></label>
  ```

**优点:** 增大点击区域，方便用户操作；屏幕阅读器能正确读出关联，提升可访问性。

![image-20231218212939411](./assets/image-20231218212939411.png)

## **单选 (`radio`) 与 复选 (`checkbox`)**

- **单选按钮 (`radio`):**
  *   同一组单选按钮必须拥有相同的 `name` 属性，以实现互斥选择。
  *   每个选项应有不同的 `value`。
  *   使用 `checked` 属性设置默认选中项。
  *   通常与 `<fieldset>` 和 `<legend>` 结合使用，语义化分组。

```html
<fieldset>
  <legend>选择性别:</legend>
  <input type="radio" id="male" name="gender" value="M" checked> <label for="male">男</label>
  <input type="radio" id="female" name="gender" value="F"> <label for="female">女</label>
</fieldset>
```

- **复选框 (`checkbox`):**
  *   允许用户选择零个或多个选项。
  *   同一类别的复选框建议使用相同的 `name` (服务器端可能收到同名参数的多个值)。
  *   使用 `checked` 设置默认勾选项。
  *   每个复选框必须设置 `value` 属性。

```html
<p>兴趣爱好:</p>
<input type="checkbox" id="coding" name="hobby" value="code"> <label for="coding">编程</label>
<input type="checkbox" id="music" name="hobby" value="music"> <label for="music">音乐</label>
```

## `<select>`, `<option>`, `<optgroup>` - 下拉选择列表

- 创建下拉菜单供用户选择。

  *   **`<select>`**: 列表容器。
      *   `name`: 必需，提交时的键。
      *   `id`: 用于 `<label>` 关联。
      *   `multiple`: (布尔属性) 允许选择多个选项。
      *   `size`: 设置可见选项的数量（大于 1 时通常呈现为列表框）。
  *   **`<option>`**: 定义列表中的一个选项。
      *   `value`: 提交到服务器的值。若省略，则提交 `<option>` 标签内的文本。
      *   `selected`: (布尔属性) 设置为默认选中项。
      *   标签内的文本：用户在下拉列表中看到的文本。
  *   **`<optgroup>`**: 对 `<option>` 进行分组。
      *   `label`: 分组的标题。

```html
<label for="country">选择国家:</label>
<select id="country" name="country_code">
  <option value="">--请选择--</option>
  <optgroup label="亚洲">
    <option value="CN">中国</option>
    <option value="JP">日本</option>
  </optgroup>
  <optgroup label="欧洲">
    <option value="GB" selected>英国</option>
    <option value="FR">法国</option>
  </optgroup>
</select>
```

### **`<datalist>` 与 `<input list="...">`: 输入建议**

`<datalist>` 元素包含一组 `<option>` 元素，这些选项作为与它关联的 `<input>` 元素的建议列表。用户输入时，浏览器会显示匹配的建议。

*   `<datalist>` 需要一个 `id`。
*   `<input>` 的 `list` 属性值必须等于 `<datalist>` 的 `id`。
*   `<option>` 在 `<datalist>` 中只需要 `value` 属性 (用户看到和提交的值)。也可以包含标签文本。

```html
<label for="browser">喜欢的浏览器:</label>
<input type="text" id="browser" name="browser" list="browser-list">
<datalist id="browser-list">
  <option value="Chrome"></option>
  <option value="Firefox"></option>
  <option value="Edge"></option>
  <option value="Safari"></option>
</datalist>
```

### **`<fieldset>` 与 `<legend>`: 表单分组**

将逻辑相关的控件组织在一起，视觉上通常表现为一个带标题的边框。

*   `<fieldset>`: 创建分组容器。
*   `<legend>`: (必须是 `<fieldset>` 的第一个子元素) 提供分组的标题。

```html
<fieldset>
  <legend>联系信息</legend>
  <p>
    <label for="email">邮箱:</label>
    <input type="email" id="email" name="email">
  </p>
  <p>
    <label for="tel">电话:</label>
    <input type="tel" id="tel" name="phone">
  </p>
</fieldset>
```



## **HTML5 表单验证**

浏览器内置的客户端验证机制，在提交前检查用户输入。

**验证触发时机：** 当用户尝试提交表单时（例如点击 `type="submit"` 按钮）。

*   **属性验证:**
    *   `required`: 确保字段不为空。
    *   `type` (如 `email`, `url`, `number`): 提供基础的类型和格式验证。
    *   `min`, `max`, `step`: 数值范围和步长验证。
    *   `minlength`, `maxlength`: 文本长度验证。
    *   `pattern`: 使用正则表达式进行复杂的格式验证。
*   **禁用验证：**
    *   在 `<form>` 上加 `novalidate` 属性：禁用整个表单的验证。
    *   在提交按钮 (`<button type="submit">` 或 `<input type="submit">`) 上加 `formnovalidate` 属性：通过此按钮提交时不进行验证。
*   **CSS 伪类:** `:valid`, `:invalid`, `:required`, `:optional` 等伪类可用于根据验证状态设置控件样式。

### HTML5 `form*` 属性

允许提交按钮等元素覆盖其所属 `<form>` 的某些属性，实现更灵活的提交行为，尤其适用于一个表单内有多个不同目的的提交按钮。

*   `formaction`: 覆盖 `<form>` 的 `action`。
*   `formenctype`: 覆盖 `<form>` 的 `enctype`。
*   `formmethod`: 覆盖 `<form>` 的 `method`。
*   `formnovalidate`: 覆盖 `<form>` 的 `novalidate` (使本次提交不验证)。
*   `formtarget`: 覆盖 `<form>` 的 `target`。

## GET vs POST 请求方法对比

| 特性           | GET                                                        | POST                                                         |
| :------------- | :--------------------------------------------------------- | :----------------------------------------------------------- |
| **数据位置**   | URL 查询字符串 (`?key=value&...`)                          | HTTP 请求体 (Request Body)                                   |
| **数据长度**   | **有限制** (受 URL 最大长度限制，约 2KB+)                  | 理论上**无限制** (主要受服务器配置限制)                      |
| **安全性**     | **较低** (数据在 URL 中可见，易被日志记录、缓存、历史记录) | **相对较高** (数据不在 URL 中，支持 HTTPS 加密传输)          |
| **缓存**       | 请求**可被缓存**                                           | 请求默认**不被缓存**                                         |
| **浏览器历史** | 请求参数保留在历史记录中                                   | 请求参数**不**保留在历史记录中                               |
| **书签收藏**   | 可以收藏为书签                                             | **不能**收藏为书签                                           |
| **幂等性**     | 通常**是** (多次相同请求，服务器状态和响应不变)            | 通常**否** (多次请求可能导致不同结果或副作用，如重复创建资源) |
| **主要用途**   | 获取/查询数据 (Read operations)                            | 创建/更新/删除数据 (Create/Update/Delete)，提交敏感或大量数据 |

![image-20231218213341832](./assets/image-20231218213341832-1702906632679-1.png)
