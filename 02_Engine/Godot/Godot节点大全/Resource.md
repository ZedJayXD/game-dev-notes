# RefCounted

> **继承自:** `Object`  
> **子类:** `Array`, `Dictionary`, `Node`, `Resource` 等  
> **类别:** 核心类

## 概述

`RefCounted` 是 Godot 中实现**引用计数**内存管理的基类。当对象不再被任何变量引用时，自动释放内存。适合用作临时数据容器。

---

## 属性

| 属性 | 类型 | 描述 |
|------|------|------|
| `__reference_count__` | `int` | 当前对象的引用计数（只读，调试用） |

```gdscript
var damage = Damage.new()
print(damage.__reference_count__)  # 输出: 1
```

---

## 方法

### 核心方法

| 方法 | 返回类型 | 描述 |
|------|----------|------|
| `init()` | `void` | 对象初始化时调用（类似构造函数） |
| `reference()` | `bool` | 增加引用计数，返回 `true` 表示成功 |
| `unreference()` | `bool` | 减少引用计数，返回 `true` 表示对象已释放 |

### 常用操作

```gdscript
# 1. 创建对象
var obj = MyClass.new()

# 2. 复制对象（浅拷贝）
var copy = obj.duplicate()

# 3. 检查是否被引用
if obj.is_referenced():
    print("对象正在被使用")

# 4. 获取引用计数
print(obj.get_reference_count())  # 返回 int
```

### 内存管理

| 方法 | 描述 |
|------|------|
| `free()` | **不推荐！** 手动释放（RefCounted 应自动管理） |
| `is_referenced()` | 检查对象是否被引用 |
| `get_reference_count()` | 返回当前引用计数 |

---

## 信号

**❌ RefCounted 没有内置信号**

因为它是纯数据类，不需要信号机制。如果需要信号，应继承 `Node`。

---

## 使用示例

### 1. 基础用法

```gdscript
# Damage.gd
class_name Damage
extends RefCounted

var amount: int
var source: Node2D

func _init(p_amount: int = 0, p_source: Node2D = null):
    amount = p_amount
    source = p_source
```

```gdscript
# 使用
func take_damage():
    var damage = Damage.new(10, enemy)
    # 使用 damage...
    # 函数结束，damage 自动释放
```

### 2. 复杂数据对象

```gdscript
class_name InventoryItem
extends RefCounted

var id: String
var name: String
var quantity: int
var metadata: Dictionary

func _init(p_id: String, p_name: String):
    id = p_id
    name = p_name
    quantity = 1
    metadata = {}
```

### 3. 消息/事件对象

```gdscript
class_name GameEvent
extends RefCounted

enum EventType { COMBAT, LOOT, DIALOG }

var type: EventType
var data: Dictionary
var timestamp: int

func _init(p_type: EventType):
    type = p_type
    timestamp = Time.get_unix_time_from_system()
```

---

## 继承关系图

```
Object
  ├── RefCounted  ← 你在这里
  │   ├── Array
  │   ├── Dictionary
  │   ├── Node (通过 Resource)
  │   ├── Resource
  │   └── (自定义类)
  └── (其他)
```

---

## 最佳实践

### ✅ 适合使用 RefCounted

```gdscript
# 临时数据对象
class_name Damage extends RefCounted
class_name Message extends RefCounted
class_name ItemData extends RefCounted
```

### ❌ 不适合使用 RefCounted

```gdscript
# 需要显示在场景中的对象
class_name Player extends CharacterBody2D  # 使用 Node

# 需要信号的对象
class_name EventManager extends Node  # 使用 Node
```

---

## 注意事项

| 项目 | 说明 |
|------|------|
| **自动释放** | 引用计数归零时自动释放，无需手动 `free()` |
| **循环引用** | 小心两个对象互相引用，会导致内存泄漏 |
| **性能** | 比手动管理稍慢，但更安全 |
| **调试** | 使用 `get_reference_count()` 检查内存泄漏 |

---

## 与 Resource 的区别

| 特性 | RefCounted | Resource |
|------|------------|----------|
| 自动内存管理 | ✅ | ✅ |
| 序列化/保存 | ❌ | ✅ |
| 复用/共享 | ❌ | ✅ |
| 场景树支持 | ❌ | ❌ |

```gdscript
# RefCounted - 临时数据
var temp = Damage.new()

# Resource - 可保存的数据
var item = ItemResource.new()
ResourceSaver.save(item, "res://item.tres")
```

---

## 常见陷阱

### ❌ 错误用法

```gdscript
# 1. 手动释放（不需要！）
var obj = MyClass.new()
obj.free()  # ❌ 错误！

# 2. 循环引用
class A extends RefCounted:
    var b: B

class B extends RefCounted:
    var a: A

var a = A.new()
var b = B.new()
a.b = b
b.a = a  # ❌ 循环引用，内存泄漏！
```

### ✅ 正确用法

```gdscript
# 1. 让引用自动失效
func process():
    var obj = MyClass.new()
    # 使用 obj...
    # 函数结束，obj 自动释放

# 2. 手动解除引用
var obj = MyClass.new()
# 使用 obj...
obj = null  # ✅ 触发自动释放
```

---

## 相关类

- `Object` - 所有类的基类
- `Resource` - 可序列化的 RefCounted 子类
- `Node` - 场景树节点
- `Array` / `Dictionary` - 内置数据结构

---

**最后更新:** 2026-06-28