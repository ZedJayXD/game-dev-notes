---
title: "obsidian进阶の插件系列|Templater从小白到菜鸟 - 技术栈"
source: "https://jishuzhan.net/article/2013503186830147585"
author:
published:
created: 2026-06-24
description: "写在前面：本文目的是为了更好地理解及掌握官方档案说明书，从而整理而成的二创，因此引用了大量原文以及源代码，侵删！"
tags:
  - "clippings"
---
> 写在前面：本文目的是为了更好地理解及掌握官方档案说明书，从而整理而成的二创，因此引用了大量原文以及源代码，侵删！

📚 官方原文：

$$
https://gitcode.com/gh_mirrors/te/Templater.git
$$

([https://gitcode.com/gh\_mirrors/te/Templater.git](https://gitcode.com/gh_mirrors/te/Templater.git))

## 操作前摇：

### 1、点设置：

![](https://i-blog.csdnimg.cn/direct/b442550c221c44a28fbdae14855605ab.png)

### 2、关闭安全模式

![](https://i-blog.csdnimg.cn/direct/717a35f7581247b9ba534649b45b397f.png)

### 3、下载插件

![](https://i-blog.csdnimg.cn/direct/eebc282d59184e13bbf330add5a7849a.png)

### 4、搜索并安装

![](https://i-blog.csdnimg.cn/direct/77b1e88cbb0446caa7dd868caa0b9eab.png)  
![](https://i-blog.csdnimg.cn/direct/c24d732ee7a545fcb5f7e3d8db44625f.png)

### 5、点击设置面板

![](https://i-blog.csdnimg.cn/direct/c816180a7b9c44a080fef218df1aa81e.png)

## 01三步执行插件:

### ①简易版配置:初步只需要设置这两步

![](https://i-blog.csdnimg.cn/direct/6b883062a5c445c89bfbc8f71d899868.png)

### ② 认识快捷键

![](https://i-blog.csdnimg.cn/direct/5d6dfade94e64e65be17c5fefdee3d42.png)

### ③执行第一个命令函数（获取日期）

> <% tp.date.now() %>

**操作：**

alt+r>>函数执行结果会覆盖函数  
![](https://i-blog.csdnimg.cn/direct/1a289ac114e5459bb78c69ba40c93c1e.png)

## 02Templater 面板设置说明:

![](https://i-blog.csdnimg.cn/direct/6b18b387c63e4fd2b511050761ef8963.png)

### 以下面板设置以表格汇总：

### 001通用设置 (General Settings)

### 002模板快捷键 (Template Hotkeys)

### 003文件夹模板 (Folder Templates) (需先启用 Trigger on new file creation)

### 004文件正则模板 (File Regex Templates) (需先启用 Trigger on new file creation)

### 005启动模板 (Startup Templates)

### 006用户脚本函数 (User Script Functions)

### 007用户系统命令函数 (User System Command Functions)

| **设置类别** | **选项 / 功能名称** | **说明** |
| --- | --- | --- |
| **通用设置 (General Settings)** | `Template folder location` | 指定模板文件夹路径，该文件夹内的文件可作为模板使用。 |
|  | `Syntax Highlighting on Desktop` | 在桌面端编辑模式下为 Templater 命令启用语法高亮。 |
|  | `Syntax Highlighting on Mobile` | 在移动端编辑模式下启用 Templater 语法高亮（⚠️ 可能破坏实时预览，慎用）。 |
|  | `Automatic jump to cursor` | 插入模板后自动触发 `tp.file.cursor` ，跳转到光标占位符位置。也可手动设置快捷键触发。 |
|  | `Trigger Templater on new file creation` | 监听新文件创建事件，若匹配规则，则自动执行模板命令。 ✅ 兼容 Daily Notes、Calendar 等插件。 ⚠️ **警告** ：确保新文件内容安全，避免执行不可信代码。 |
| **模板快捷键 (Template Hotkeys)** | Template Hotkeys | 允许将特定模板绑定到键盘快捷键。 |
| **文件夹模板 (Folder Templates)** （需先启用 *Trigger on new file creation* ） | Folder Templates | 为指定文件夹（及其子文件夹）自动应用模板。 • 匹配深度优先（最深路径优先） • 顺序无关 • 可添加 `/` 作为全局兜底规则 ❌ 与 File Regex Templates 互斥 |
| **文件正则模板 (File Regex Templates)** （需先启用 *Trigger on new file creation* ） | File Regex Templates | 使用正则表达式匹配新文件路径，自动应用对应模板。 • 自上而下匹配， **首个匹配生效** • 可添加 `.*` 作为兜底规则 • 推荐用 [Regex101](https://regex101.com/) 测试正则 ❌ 与 Folder Templates 互斥 |
| **启动模板 (Startup Templates)** | Startup Templates | Templater 启动时 **仅执行一次** 的模板。 • **不输出任何内容** • 适用于注册 Obsidian 事件钩子等初始化操作 |
| **用户脚本函数 (User Script Functions)** | User Script Functions | 指定一个文件夹，其中所有 `.js` 文件将作为 **CommonJS 模块** 加载，用于定义 `tp.user.xxx()` 自定义函数。 • 文件夹必须在 Vault 内或可访问 • 参考文档：Script User Functions |
| **用户系统命令函数 (User System Command Functions)** | User System Command Functions | 允许创建调用 **系统命令** 的自定义用户函数。 ⚠️ **高危功能** ：仅执行你完全理解且来源可信的系统命令 • 参考文档：System User Functions |

---

### 💡 总结：

- 若需 **按文件夹自动套用模板** → 用 **Folder Templates**
- 若需 **按文件名/路径正则匹配** → 用 **File Regex Templates**
- 日常daily → 推荐配合 **Daily Notes + Startup Templates + User Script Functions**
- 安全第一：避免在 `Startup` 或 `New File` 中执行未知脚本

## 03plugin语法:

### 📌 Templater 语法核心规则总览

| **类别** | **规则 / 要点** | **说明与示例** |
| --- | --- | --- |
| **命令基本结构** | 必须包含开始和结束标签 | 所有命令必须写作： `<% ... %>` ✅ 正确： `<% tp.date.now() %>` ❌ 错误： `tp.date.now()` （缺少标签） |
| **函数调用前缀** | 所有函数均属于 `tp` 对象 | 函数路径使用点号 `.` 访问： `tp.<module>.<function>()` 例如： `tp.file.title`, `tp.user.myFunc()` |
| **函数调用语法** | 使用括号 `()` 调用 | 即使无参数也需加 `()` ： ✅ `tp.date.now()` ❌ `tp.date.now` |

---

### 📥 函数参数类型规范

| **参数类型** | **书写格式** | **示例** |
| --- | --- | --- |
| `string` | 用单引号 `'...'` 或双引号 `"..."` 包裹 | `"YYYY-MM-DD"`, `'Hello'` |
| `number` | 直接写数字（可带负号） | `7`, `-3`, `0` |
| `boolean` | 仅限小写 `true` 或 `false` | `true`, `false` |
| 多类型（union） | 按实际传入值的类型书写 | 若参数为 \`number |

> ⚠️ **必须严格匹配类型** ，否则函数会报错或行为异常。

---

### 📘 函数文档语法 vs 实际调用对比

| **项目** | **文档中显示的签名（仅用于说明）** | **实际调用时的正确写法** |
| --- | --- | --- |
| 示例函数 | \`tp.date.now(format?: string = "YYYY-MM-DD", offset?: number | string, reference?: string, reference\_format?: string)\` |
| 参数名 | `format`, `offset` 等（符号名） | **不写参数名！** 只按顺序传值 |
| 类型标注 | `: string`, `: number` | **不写类型！** |
| 默认值 | `= "YYYY-MM-DD"` | 若使用默认值，可省略该参数 |
| 可选参数 | 带 `?`（如 `offset?`） | 可省略，但若提供必须按顺序 |

---

### ✅ 有效调用示例（tp.date.now）

| **调用方式** | **输出效果（假设今天是 2026-01-18）** |
| --- | --- |
| `<% tp.date.now() %>` | `2026-01-18` |
| `<% tp.date.now("YYYY年MM月DD日") %>` | `2026年01月18日` |
| `<% tp.date.now("dddd", 1) %>` | `Monday` （明天） |
| `<% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>` | 若文件名为 `2025-12-25` ，则输出 `2025-12-25` |

---

### ❌ 常见错误调用（无效写法）

| **错误写法** | **问题原因** |
| --- | --- |
| `tp.date.now(format: string = "YYYY-MM-DD")` | 写了参数名、类型、默认值 ------ 这是文档语法，不是调用语法 |
| `tp.date.now(format="YYYY-MM-DD")` | JavaScript 不支持命名参数（除非对象解构，但 Templater 不支持） |
| `<% tp.date.now(YYYY-MM-DD) %>` | 字符串未加引号，会被当作变量或语法错误 |
| `<% tp.date.now(true) %>` | 第一个参数应为字符串，传了布尔值 |

---

### 💡 关键总结

- ✅ **命令必须包裹在 `<% %>` 中**
- ✅ **函数必须以 `tp.` 开头**
- ✅ **参数只写值，不写名称/类型/默认值**
- ✅ **参数顺序必须严格匹配文档定义**
- ✅ **字符串必须加引号，布尔值必须小写**

## 04Javascript执行命令

模板引擎使用所有命令结果生成替换字符串时，它将存储在名为tR。这是将包含已处理文件内容的字符串。可以从JS执行命令访问该变量。  
**命令类型**

**Templater** 定义了2种类型的开始标记，即定义了2种类型的 **命令**:

- `<%`: 插值命令。它将输出内部表达式的结果。
- `<%*`:**JavaScript执行命令** 它将执行里面的JavaScript代码。默认情况下，它不输出任何内容。  
	命令的结束标记始终是相同的:`%>`

### 001命令实用程序

除了不同类型的命令之外，您还可以使用命令实用程序。它们也在命令的开始标记中声明。所有命令实用程序都适用于所有命令类型。可用的命令实用程序有:

#### \- 空白控件

复制代码

```
<%* if (tp.file.title == "MyFile" ) { %>
This is my file!
<%* } else { %>
This isn't my file!
<%* } %>
Some content ...
```

如果条件为false，将产生以下输出 (当它为真时也会发生同样的情况)，请注意空行:

复制代码

```
This isn't my file!

Some content ...
```

您可能希望删除由 **执行命令**,不产生任何输出。

空白控件存在特定的语法:

- 下划线 `_` 在 **开始** 标签的 (`<%_`) 将修剪 **全部** 空白 **之前** 命令
- 下划线 `_` 在 **结束** 标签的 (`_%>`) 将修剪 **全部** 空白 **之后** 命令
- 破折号 `-` 在 **开始** 标签的 (`<%-`) 将修剪 **一个** 换行符 **之前** 命令
- 破折号 `-` 在 **结束** 标签的 (`-%>`) 将修剪 **一个** 换行符 **之后** 命令。

示例中，要修复模板以删除空白行，我们将使用以下模板 (注意破折号 `-` 在标签的末尾)，以删除空白换行符 **之后** 执行命令:

复制代码

```
<%* if (tp.file.title == "MyFile" ) { -%>
This is my file!
<%* } else { -%>
This isn't my file!
<%* } -%>
Some content ...
```

这将产生以下输出:

复制代码

```
This isn't my file!
Some content ...
```

#### \- 动态命令

使用此命令实用程序，意味着进入预览模式时将解析此命令。

要声明动态命令，添加plus+在命令开始标记后签名:<%+

您的命令现在将仅在预览模式下执行。

这对于内部函数很有用，例如tp.file.last\_modified\_date例如:

复制代码

```
Last modified date: <%+ tp.file.last_modified_date() %>
```

### 002Internal Functions

**现有的内部模块：**

#### App module: tp.app

#### Config module: tp.config

#### Date module: tp.date

#### File module: tp.file

#### Frontmatter module: tp.frontmatter

#### Hooks module:tp.hooks

#### Obsidian module: tp.obsidian

#### System module: tp.system

#### Web module: tp.web

典型的内部函数调用如下：

<% tp.<module\_name>.<internal\_function\_name> %>

### 003用户功能(User script)：

//您可以在Templater中定义自己的函数。

//您可以使用两种类型的用户函数:

- 编写用户函数脚本
- 系统命令用户功能

//调用用户函数

使用通常的函数调用语法调用用户函数:

tp.user.<user\_function\_name>(),

<user\_function\_name>是您定义的函数名称。

定义了一个名为echo,一个完整的命令调用将如下所示:

复制代码

```
<% tp.user.echo() %>
```

#### //步骤：

1. 指定了Scripts文件夹作为Templater设置中的脚本文件夹
2. Templater将加载所有JavaScript (.js文件) 中的脚本Scripts文件夹
3. 创建名为Scripts/my\_script.（在黑曜石之外创建文件，因为黑曜石只创建markdown文件。js文件）
4. 调用脚本作为用户函数。函数名对应于脚本文件名

#### exp.01:输出Message from my script: Hello World!

复制代码

```
module.exports = function (msg) {
    return \`Message from my script: ${msg}\`;
};
```

调用:

复制代码

```
<% tp.user.my_script("Hello World!") %>
```

这将输出Message from my script: Hello World!

运行结果：  
![](https://i-blog.csdnimg.cn/direct/733f574d51a74fd7845b485eea7d4df6.png)

#### exp.02：把普通文本转换成提示块

提供三种常用 Callout 类型的便捷调用方式：

note(text) → 生成普通提示块

tip(text) → 生成技巧提示块

warning(text) → 生成警告提示块

复制代码

```
function formatAsCallout(text, type = "note") {
  const blockQuoteLines = text.split("\n").map((line) => \`> ${line}\`);
  return \`> [!${type}]\n${blockQuoteLines.join("\n")}\`;
}

module.exports = {
  note: (text) => formatAsCallout(text, "note"),
  tip: (text) => formatAsCallout(text, "tip"),
  warning: (text) => formatAsCallout(text, "warning"),
};
```

调用:

复制代码

```
<% tp.user.my_script.note("Line 1\nLine2") %>
```

输出:

复制代码

```
> [!note]
> Line 1
> Line2
```

#### 带有文档的用户脚本示例

复制代码

```
/**
 * This does something cool
 */
function doSomething() {
    console.log('Something was done')
}

module.exports = doSomething;
```

### 004转换成系统脚本System scripts:

这种类型的用户函数允许您执行系统命令并检索其输出。

需要在Templater的设置中启用系统命令用户功能。

#### 定义:

> 需要定义一个函数名称,与一个系统命令 插件设置>>Add User Function
> 
> 一旦完成，Templater将创建一个以您定义的名称命名的用户函数，该函数将执行您的系统命令并返回其输出
> 
> 就像内部函数一样，用户函数在tpJavaScript对象，更具体地说，在tp.user对象。

#### 参数:

> 您可以将可选参数传递给用户函数。它们必须作为包含属性及其相应值的单个JavaScript对象传递:{arg1: value1, arg2:
> 
> value2,...}。 这些参数将以以下形式提供给您的程序/脚本环境变量 在前面的示例中，这将给出以下命令声明:<%
> 
> tp.user.echo({a: "value 1", b: "value 2"})。
> 
> 如果我们的系统命令调用bash脚本，我们将能够访问变量a和b使用 a 和 a和 a和b。

#### 系统命令中的内部参数:

> 您可以在系统命令中使用内部函数。在执行系统命令之前，内部函数将被替换。
> 
> 例如，如果您配置了系统命令cat <% tp.file.path() %>,它将在执行系统命令之前被替换为cat/path/to/file。

### 005title,frontmatter,tags和自定义函数：

#### <%\* tR += "test" %>

复制代码

```
---
type: template
---
This is a person template.

<%* tR = "" -%>
---
type: person
---
# <% tp.file.cursor() %>
```

将输出:

复制代码

```
---
type: person
---
#
```

**建议和提示：**

需要注意的是，tp.system.prompt()和tp.system.suggester()两者都需要一个await将值保存到变量的语句

#### Templater 模板示例

| 功能 | 技术点 |
| --- | --- |
| **条件渲染** | 基于文件名、frontmatter、标签动态生成内容 |
| **调试输出** | 使用 `console.log()` 打印信息到控制台 |
| **内容处理** | 读取并替换当前文件内容，插入结果 |
| **模板语法** | 使用 `<%* ... %>` 执行逻辑， `tR +=` 控制输出 |

---

Templater 使用 `<% ... %>` 和 `<%* ... %>` 两种标签：

- `<% ... %>` ：执行 JavaScript 表达式，并将 **返回值输出到文档中** 。
- `<%* ... %>` ：执行 JavaScript 代码块（语句）， **不自动输出结果** ，但可通过 `tR += ...` 手动追加内容。

> ⚠️ 注意： `<%*` 块中的代码是 **异步执行的** （底层基于 `async/await` ），适合处理条件判断、函数定义、文件操作等。

---

##### 1\. 根据文件标题判断

javascript 复制代码

```javascript
<%* if (tp.file.title.startsWith("Hello")) { %>
This is a hello file !
<%* } else { %>
This is a normal file !
<%* } %>
```
- **作用** ：检查当前笔记的\*\*文件名（不含路径和扩展名）\*\*是否以 `"Hello"` 开头。
- **输出** ：
	- 如果是 → 插入 `This is a hello file !`
		- 否则 → 插入 `This is a normal file !`

✅ 示例：

文件名为 `Hello World.md` → 触发"hello file"。

---

##### 2\. 根据 Frontmatter 字段判断

javascript 复制代码

```javascript
<%* if (tp.frontmatter.type === "seedling") { %>
This is a seedling file !
<%* } else { %>
This is a normal file !
<%* } %>
```
- **作用** ：读取当前文件的 **YAML frontmatter** 中的 `type` 字段。
- **前提** ：文件必须包含类似以下内容：
	yaml 复制代码
	```yaml
	---
	type: seedling
	---
	```
- **输出** ：
	- 若 `type == "seedling"` → 显示"seedling file"
		- 否则 → 显示"normal file"

📌 `tp.frontmatter` 是一个对象，可直接访问任意 frontmatter 键。

---

##### 3\. 根据标签（Tags）判断

javascript 复制代码

```javascript
<%* if (tp.file.tags.contains("#todo")) { %>
This is a todo file !
<%* } else { %>
This is a finished file !
<%* } %>
```
- **作用** ：检查当前文件是否包含标签 `#todo` 。
- **注意** ： `tp.file.tags` 返回的是 **带 `#` 的完整标签数组** ，如 `["#todo", "#work"]` 。
- **方法** ：使用了 `.contains()` ------ 这是 Templater 对数组的 **扩展方法** （等价于原生 `.includes()` ）。

✅ 文件含 `#todo` 标签 → 显示"todo file"。

> 💡 实际上，更标准的写法应为 `tp.file.tags.includes("#todo")` ，但 Templater 确实提供了 `.contains()` 别名（兼容性考虑）。

---

##### 4\. 定义并调用自定义函数（仅控制台输出）

javascript 复制代码

```javascript
<%*
function log(msg) {
    console.log(msg);
}
%>
<%* log("Title: " + tp.file.title) %>
```
- **作用** ：定义一个 `log` 函数，并打印当前文件标题到 **开发者控制台（DevTools Console）** 。
- **注意** ： `console.log()` **不会输出到笔记中** ，仅用于调试。
- 要打开控制台：Obsidian → `Ctrl+Shift+I` （Windows/Linux）或 `Cmd+Option+I` （Mac）。

🔧 这是典型的 **调试技巧** ，用于查看变量值。

---

##### 5\. 替换文件内容中的文本并输出

javascript 复制代码

```javascript
<%* tR += tp.file.content.replace(/stuff/, "things"); %>
```
- **作用** ：
	1. 获取当前文件 **执行模板前的全部内容** （ `tp.file.content` ）；
		2. 将其中第一个匹配 `"stuff"` 的子串替换为 `"things"` ；
		3. 通过 `tR += ...` **将结果追加到最终输出中** 。
- **注意** ：
	- `tR` 是 Templater 的 **输出缓冲区变量** （template Result）；
		- 此操作 **不会修改原文件** ，只是把处理后的内容插入到模板位置；
		- 正则 `/stuff/` 只替换 **第一次出现** ，若要全局替换需用 `/stuff/g` 。

✅ 示例：

原文件内容含 `I have stuff to do` → 输出变为 `I have things to do` 。

---

#### ⚠️ 注意事项

1. **`tp.file.content` 是只读快照** ：它反映的是 **模板执行前** 的文件内容，修改它不会影响原文件。
2. **异步上下文** ：所有 `<%* ... %>` 代码运行在 `async` 函数中，可使用 `await` （如 `await tp.system.prompt(...)` ）。
3. **标签格式** ： `tp.file.tags` 包含 `#` ，查询时需带上（如 `"#todo"` ）。
4. **Frontmatter 依赖** ：若文件无 frontmatter， `tp.frontmatter.type` 会是 `undefined` ，可能导致错误（建议加判空）。

## 05函数速查表

#### 📚 Templater 内置函数速查表（整理）

| 模块（Module） | 函数（Function） | 签名（Signature） | 描述（Description） | 参数（Arguments） | 示例（Examples） |
| --- | --- | --- | --- | --- | --- |
| **`tp.app`** | \--- | `tp.app` | 提供对 Obsidian 应用实例的访问。建议优先使用此而非全局 `app` 。 | \--- | \--- |
| **`tp.user`** | \--- | `tp.user` | 用于调用用户自定义脚本（位于"用户脚本函数"文件夹中）。 | \--- | \--- |
| **`tp.config`** | `template_file` | `tp.config.template_file` | 当前模板文件的 `TFile` 对象。 | \--- | \--- |
|  | `target_file` | `tp.config.target_file` | 模板将被插入的目标文件的 `TFile` 对象。 | \--- | \--- |
|  | `run_mode` | `tp.config.run_mode` | Templater 的启动方式（如"新建文件"、"追加到当前文件"等）。 | \--- | \--- |
|  | `active_file` | `tp.config.active_file?` | 启动 Templater 时的活动文件（若存在）。 | \--- | \--- |
| **`tp.date`** | `now` | `tp.date.now(format="YYYY-MM-DD", offset?, reference?, reference_format?)` | 获取当前日期（可偏移、可基于参考日期）。 | \- `format`: 输出格式（默认 `"YYYY-MM-DD"` ） - `offset`: 偏移量（数字=天数，字符串=ISO 8601 如 `"P1W"` ） - `reference`: 参考日期（如 `tp.file.title` ） - `reference_format`: 参考日期格式 | \- `<% tp.date.now() %>` → `2026-01-18` - `<% tp.date.now("Do MMMM YYYY") %>` - `<% tp.date.now("YYYY-MM-DD", -7) %>` （上周） - `<% tp.date.now("YYYY-MM-DD", "P1Y") %>` （明年） - `<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>` （文件名日期+1天） |
|  | `tomorrow` | `tp.date.tomorrow(format="YYYY-MM-DD")` | 获取明天的日期。 | `format`: 日期格式 | `<% tp.date.tomorrow("Do MMMM YYYY") %>` |
|  | `yesterday` | `tp.date.yesterday(format="YYYY-MM-DD")` | 获取昨天的日期。 | `format`: 日期格式 | `<% tp.date.yesterday() %>` |
|  | `weekday` | `tp.date.weekday(format="YYYY-MM-DD", weekday, reference?, reference_format?)` | 获取指定星期几的日期（0=本周一，7=下周一，-7=上周一）。 | \- `format`: 输出格式 - `weekday`: 星期偏移数 - `reference`: 参考日期 - `reference_format`: 参考格式 | \- `<% tp.date.weekday("YYYY-MM-DD", 0) %>` （本周一） - `<% tp.date.weekday("YYYY-MM-DD", 7) %>` （下周一） - `<% tp.date.weekday("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>` （基于文件名的周一） |
| **`tp.file`** | `content` | `tp.file.content` | 获取执行时当前文件的内容（只读）。 | \--- | `<% tp.file.content %>` |
|  | `create_new` | `tp.file.create_new(template, filename?, open_new=false, folder?)` | 创建新文件（内容或模板）。 | \- `template`: 字符串内容 或 `TFile` 模板 - `filename`: 文件名（默认 Untitled） - `open_new`: 是否打开新文件 - `folder`: 目标文件夹（路径或 `TFolder` ） | \- `<%* await tp.file.create_new("内容", "笔记") %>` - `<%* await tp.file.create_new(tp.file.find_tfile("模板"), "新笔记") %>` - `<% [[<(await tp.file.create_new("内容", "笔记")).basename>]] %>` （创建并插入链接） |
|  | `creation_date` | `tp.file.creation_date(format="YYYY-MM-DD HH:mm")` | 获取文件创建时间。 | `format`: 日期格式 | `<% tp.file.creation_date("dddd Do MMMM YYYY") %>` |
|  | `cursor` | `tp.file.cursor(order?)` | 设置光标位置（支持多光标）。 | `order`: 跳转顺序（相同值 = 多光标） | `<% tp.file.cursor(1) %>A<% tp.file.cursor(1) %>` |
|  | `cursor_append` | `tp.file.cursor_append(content)` | 在当前光标后追加内容。 | `content`: 要追加的文本 | `<% tp.file.cursor_append("附加文本") %>` |
|  | `exists` | `tp.file.exists(filepath)` | 检查文件是否存在（需完整相对路径+扩展名）。 | `filepath`: 文件路径（如 `"日记/2026.md"` ） | `<% await tp.file.exists("笔记/测试.md") %>` |
|  | `find_tfile` | `tp.file.find_tfile(filename)` | 根据文件名查找 `TFile` 对象。 | `filename`: 文件名（不含路径/扩展名） | `<% tp.file.find_tfile("模板").basename %>` |
|  | `folder` | `tp.file.folder(absolute=false)` | 获取文件所在文件夹名。 | `absolute`: 是否返回完整路径 | `<% tp.file.folder(true) %>` → `"日记/2026"` |
|  | `include` | `tp.file.include(include_link)` | 包含另一文件内容（支持节/块引用，模板会被解析）。 | `include_link`: 链接（如 `"[[文件]]"` 或 `TFile` ） | `<% await tp.file.include("[[模板#节]]") %>` |
|  | `last_modified_date` | `tp.file.last_modified_date(format="YYYY-MM-DD HH:mm")` | 获取最后修改时间。 | `format`: 日期格式 | `<% tp.file.last_modified_date() %>` |
|  | `move` | `tp.file.move(new_path, file_to_move?)` | 移动文件（路径不含扩展名）。 | \- `new_path`: 新路径（如 `"/新目录/新名"` ） - `file_to_move`: 要移动的文件（默认当前） | `<%* await tp.file.move("/归档/" + tp.file.title) %>` |
|  | `path` | `tp.file.path(relative=false)` | 获取文件系统绝对路径（或 Vault 相对路径）。 | `relative`: 是否返回相对路径 | `<% tp.file.path(true) %>` → `"日记/2026-01-18.md"` |
|  | `rename` | `tp.file.rename(new_title)` | 重命名文件（保留扩展名）。 | `new_title`: 新标题 | `<%* await tp.file.rename(tp.file.title + "2") %>` |
|  | `selection` | `tp.file.selection()` | 获取当前选中文本。 | \--- | `<% tp.file.selection() %>` |
|  | `tags` | `tp.file.tags` | 获取文件所有标签（字符串数组）。 | \--- | `<% tp.file.tags %>` |
|  | `title` | `tp.file.title` | 获取文件标题（不含路径/扩展名）。 | \--- | `<% tp.file.title %>` |
| **`tp.frontmatter`** | \--- | `tp.frontmatter` | 直接访问当前文件 frontmatter 中的所有字段（如 `tp.frontmatter.tags` ）。 | \--- | \--- |
| **`tp.hooks`** | `on_all_templates_executed` | `tp.hooks.on_all_templates_executed(callback)` | 所有模板执行完毕后触发回调（适用于 `include` / `create_new` 场景）。 | `callback`: 回调函数 | \--- |
| **`tp.obsidian`** | \--- | `tp.obsidian` | 完整暴露 Obsidian API（如 `tp.obsidian.App`, `Vault` 等）。 | \--- | \--- |
| **`tp.system`** | `clipboard` | `tp.system.clipboard()` | 获取剪贴板内容。 | \--- | `<% tp.system.clipboard() %>` |
|  | `prompt` | `tp.system.prompt(text?, default?, throw_on_cancel=false, multiline=false)` | 弹出输入框。 | \- `text`: 提示文字 - `default`: 默认值 - `throw_on_cancel`: 取消时是否报错 - `multiline`: 是否多行输入 | `<% await tp.system.prompt("心情?", "开心") %>` |
|  | `suggester` | `tp.system.suggester(text_items, items, ...)` | 弹出单选建议框。 | \- `text_items`: 显示文本列表 - `items`: 对应值列表 - 其他：取消行为、占位符等 | \- `<% await tp.system.suggester(["A","B"], ["a","b"]) %>` - `<% (await tp.system.suggester(f=>f.basename, vault.getMarkdownFiles())).basename %>` |
|  | `multi_suggester` | `tp.system.multi_suggester(...)` | 弹出多选建议框。 | 同 `suggester` ，但支持多选 | `<% await tp.system.multi_suggester(["A","B"], ["a","b"]) %>` |
| **`tp.web`** | `daily_quote` | `tp.web.daily_quote()` | 从 GitHub 获取每日一句名言（格式为 callout）。 | \--- | `<% await tp.web.daily_quote() %>` |
|  | `random_picture` | `tp.web.random_picture(size?, query?, include_size?)` | 从 Unsplash 获取随机图片。 | \- `size`: 尺寸（如 `"200x200"` ） - `query`: 搜索关键词（逗号分隔） - `include_size`: 是否在链接中包含尺寸 | `<% await tp.web.random_picture("400x300", "nature,water") %>` |
|  | `request` | `tp.web.request(url, path?)` | 发起 HTTP 请求（支持 JSON 路径提取）。 | \- `url`: 请求地址 - `path`: JSON 路径（如 `"0.title"` ） | \- `<% await tp.web.request("https://api.example.com/data") %>` - `<% await tp.web.request("https://api.example.com/posts", "0.title") %>` |

---

#### 💡 使用说明

- **异步函数** ：带 `await` 的函数（如 `create_new`, `include`, `prompt` ）必须使用 `<%* ... %>` 语法（注意星号 `*` ）。
- **日期格式** ：参考 [Moment.js 格式文档](https://momentjs.com/docs/#/displaying/format/) 。
- **路径规则** ：文件路径均为 **Vault 相对路径** ，需包含 `.md` 扩展名（ `exists` ）或不包含（ `move`, `rename` ）。

---

- **安全提示** ： `system` 和 `web` 模块涉及外部交互，请确保来源可信。