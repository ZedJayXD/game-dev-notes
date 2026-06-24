---
type: meta
tags:
  - AI规范
  - 项目上下文
created: 2026-06-24
version: "001"
---

# AGENTS.md — GameDev Vault AI 上下文

> 本文件是 AI 助手进入此仓库时的"快速入门手册"。
> 详细规则见 `99_Meta/Obsidian书写规则/` 下的三份文档。

---

## 📦 项目概述

**GameDev Vault** 是一个独立游戏开发知识库（Obsidian Vault），用于管理：
- 引擎学习笔记（Unity 2D / C# → Godot 4 / GDScript 迁移中）
- 游戏项目文档
- 可复用代码片段
- 游戏设计文档
- 每日开发日报与 Bug 追踪

**用户背景**：Unity 2D + C# 开发经验，正在学习 Godot 4，采用"边学边记"模式。

---

## 📁 目录结构速览

| 文件夹 | 用途 | 模板 |
|--------|------|------|
| `00_Dashboard/` | 仓库入口，总览导航 | — |
| `01_Projects/` | 游戏项目文档 | T-项目笔记 |
| `02_Engine/` | 引擎学习笔记（Unity/Godot） | T-学习笔记 |
| `03_Design/` | 游戏设计（机制/关卡/美术） | T-设计文档 |
| `04_CodeSnippets/` | 可复用代码片段 | T-代码片段 |
| `05_References/` | 参考资料（API/教程/书籍） | T-参考资料 |
| `06_Templates/` | 笔记模板（勿直接编辑） | — |
| `07_Archive/` | 已完成/废弃项目归档 | — |
| `08_Daily/` | 日报 | T-日报 |
| `09_Issues/` | Bug 追踪 | T-问题记录 |
| `99_Meta/` | 仓库元数据（规则文档） | — |
| `Assets/` | 图片资源（Screenshots/Diagrams/Excalidraw） | — |

---

## ⚠️ AI 操作强制规则（速查）

> 完整规则见 [[Obsidian-强制规则与管理规范]]，此处仅速查。

1. **R1 先读再写** — 改文件前必须先 Read 完整内容
2. **R2 精准修改** — 只改用户要求的部分，做 diff 确认
3. **R3 Frontmatter 保护** — `---` 块不碰，除非用户明确要求
4. **R4 编码保护** — UTF-8；禁用 PowerShell `Out-File`/`Set-Content`
5. **R5 改动预览** — 修改前展示方案，用户确认后再执行
6. **R6 语法保护** — `[[链接]]`、`#标签`、`![[嵌入]]`、`^块引用`、`==高亮==`、缩进原样保留
7. **R7 一次一个文件** — 批量操作先列清单经确认
8. **R8 不懂就问** — 有歧义先问，不猜测

**经验教训与操作经验**：
- [[Obsidian-经验教训]] — 4 条踩坑记录
- [[Obsidian-操作经验]] — 5 条最佳实践

---

## 📝 模板速查

| 模板 | 适用场景 | 关键 frontmatter |
|------|---------|-----------------|
| `T-学习笔记` | 引擎/框架学习 | `type: learning`, `engine`, `subject` |
| `T-项目笔记` | 游戏项目主页 | `type: project`, `engine`, `status` |
| `T-代码片段` | 可复用代码 | `type: code`, `language`, `engine` |
| `T-设计文档` | 机制/关卡/美术设计 | `type: design`, `category` |
| `T-参考资料` | API/教程/书籍笔记 | `type: reference`, `source` |
| `T-日报` | 每日开发记录 | `type: daily` |
| `T-问题记录` | Bug 追踪 | `type: issue`, `severity`, `status` |
| `T-Excalidraw` | 手绘图表 | `type: drawing` |

**Templater 文件夹模板自动套用**：
- `01_Projects/` → T-项目笔记
- `02_Engine/` → T-学习笔记
- `04_CodeSnippets/` → T-代码片段

---

## 🏷️ 命名规范速查

| 类型 | 格式 | 示例 |
|------|------|------|
| 学习笔记 | `主题名.md` | `CorgiEngine-斜坡移动原理.md` |
| 项目笔记 | `项目名-描述.md` | `造梦西游3-角色控制系统.md` |
| 代码片段 | `功能描述.cs.md` | `2D斜坡移动控制器.cs.md` |
| 设计文档 | `DESIGN-描述.md` | `DESIGN-战斗系统.md` |
| 截图 | `描述-日期.png` | `野猪-碰撞层设置-20260623.png` |

**禁止**：`Pasted image xxx.png`、`未命名.md`、`测试.md` 等无意义命名。

---

## ⚡ 常用工作流

### 学习新教程时
1. 在 `02_Engine/<引擎>/<教程名>/` 下新建笔记
2. 用 `T-学习笔记` 模板，填好 `subject` 字段（系列名）
3. 按"学习目标 → 内容笔记 → 关键要点 → 参考来源 → 相关笔记"结构记录
4. 系列笔记用 `[[00.基础项目]] → [[01.相机]] → ...` 做导航链
5. 截图重命名为 `主题-描述.png` 再粘贴

### 记录 Bug 时
1. 在 `09_Issues/` 用 `T-问题记录` 新建
2. 填 `severity`（low/medium/high/critical）和 `status`（open/resolved）
3. 解决后填 `resolved` 日期，把 `status` 改为 `resolved`

### 写日报时
1. 在 `08_Daily/` 用 `T-日报` 新建，文件名 `YYYY-MM-DD`
2. 按"今日完成 → 遇到问题 → 明日计划"结构记录

---

## 🔌 关键插件

| 插件 | 用途 |
|------|------|
| Templater | 模板系统，支持文件夹自动套用 |
| Dataview | 动态查询笔记列表/表格/任务 |
| Excalidraw | 手绘图表嵌入 |
| obsidian-git | 自动 Git 备份 |
| Media Extended | 视频嵌入与时间戳 |

---

## 🚨 注意事项

- **Obsidian 可能正在运行**：文件被锁定时 Edit 会报 EBUSY，重试或等几秒
- **Git 自动提交**：obsidian-git 会定期提交，大批量改动前可手动 commit 做快照
- **附件路径**：Obsidian 设置里附件文件夹为 `Assets/Screenshots/`
- **中文路径**：本仓库大量中文文件名，shell 操作时注意引号
- **Dataview 性能**：避免 `FROM ""` 全库扫描 + 复杂 WHERE，优先用文件夹或 subject 字段过滤

---

## 📚 相关文档

- [[使用手册]] — 完整使用手册
- [[Obsidian-强制规则与管理规范]] — AI 操作强制规则
- [[Obsidian-操作经验]] — 操作最佳实践
- [[Obsidian-经验教训]] — 踩坑记录
