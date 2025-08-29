---
title: "Godot 节点（Node）基础教程"
date: 2025-08-29
tags: ["Godot", "教程"]
categories: ["开发"]
draft: false
---
下面介绍Godot中最基本和常用的节点类型，以及它们的简单代码示例，包括显示、隐藏和相互作用。
### 1. Node（基础节点）
所有节点的基类，用于组织和结构化场景。
```gdscript
extents Node

func _ready():
    # 添加一个子界定啊
    var child_node = Node.new()
    add_child(child_node)

    # 移除子节点
    remove_child(child_node)

    # 检查是否有子节点
    if get_child_count() > 0:
        print("此节点有子节点")
```
### 2. Sprite2D （2D精灵）
用于显示2D图像。
```gdscript
extends Sprite2D

func _ready():
    # 设置纹理
    var texture = load("res://path_to_your_image.png")
    self.texture = texture

    # 显示纹理
    self.show()

    # 隐藏
    # self.hide()

    # 或者通过visible属性
    self.visible = false

func _input(event):
    # 点击交互
    if event is InputEventMouseButton and event.pressed:
        if event.button_index == MOUSE_BUTTON_LEFT:
            # 切换显示/隐藏
            visible = !visible
```
### 3. Label (标签)
用于显示文本。
```gdscript
extends Label

func _ready():
    # 设置文本
    self.text = "Hello, Godot!"

    # 设置字体大小
    self.add_theme_font_size_override("font_size", 24)

    # 设置文本颜色
    self.module = Color(1, 0, 0)  # 红色文本
```
### 4. Button（按钮）
可点击的按钮。
```gdscript
extends Button

func _ready():
    # 设置按钮文本
    self.text = "点击我！"

    # 连接按下信号
    self.pressed.connect(_on_button_pressed)

func _on_button_pressed():
    print("按钮被点击了！")
    # 点击后禁用按钮
    self.disabled = true
    # 2秒后禁用按钮
    get_tree().create_timer(2.0).timeout.connect(
        func(): self.disabled = false
    )
```
### 5. TextureRect (纹理矩形)
用于显示图像，常用于UI。
```gdscript
extends TextureRect

func _ready():
    # 设置纹理
    var texture = load("res://path_to_your_image.png")
    self.texture = texture

    # 设置拉伸模式
    self.stretch_mode = TextureRect.STRETCH_KEEP

    # 点击交互
    self.gui_input.connect(_on_texture_rect_gui_input)

func _on_texture_rect_gui_input(event):
    if event is InputEventMouseButton and event.pressed:
        if event.button_index == MOUSE_BUTTON_LEFT:
            # 切换显示/隐藏
            visible = !visible
```
### 6. Area2D（2D区域）
用于检测于其他区域的交互
```gdscript
extends Area2D

func _ready():
    # 连接信号
    self.body_entered.connect(_on_body_entered)
    self.body_exited.connect(_on_body_exited)
    self.area_entered.connect(_on_area_entered)

    # 默认隐藏，当有物体进入时显示
    self.hid()

func _on_body_entered(body):
    print("物体进入区域： ", body.name)
    self.show()

func _on_body_exited(body):
    print("物体离开区域： ", body.name)
    self.hid()

func _on_area_entered(area):
    print("其他区域进入： ", area.name)
```
### 7. CollisionShape2D (2D碰撞形状)
为物理或区域检测提供形状。
```gdscript
extends CollisionShape2D

func _ready():
    # 创建一个矩形形状
    var shape = RectangleShape2D.new()
    shape.size = Vector2(50, 50)
    self.shape = shape

    # 禁用碰撞（隐藏）
    # self.disabled = true

    # 启用碰撞（显示）
    # self.disable = false
```
### 8. Timer（定时器）
用于定时触发事件。
```gdscript
extends Timer

func _ready():
    # 设置定时器
    self.wait_time = 2.0 # 2秒
    self.one_shot = true # 只执行一次

    # 连接超时信号
    # self.timeout.connect(_on_timer_timeout)

    # 启动定时器
    self.start()

func _on_timer_timeout():
    print("定时器超时！")
    # 可以在这里执行周期性任务
    # 如果需要循环，设置one_shot = false
```
### 9. 节点交互示例
下面是一个综合示例，展示多个节点如何交互：
```gdscript
extends Node2D

@onready var sprite = $Sprite2D
@onready var label = $Lable
@onready var button = $Button

func _ready():
    # 初始隐藏标签
    label.hide()

    # 连接按钮信号
    button.pressed.connect(_on_button_pressed)

func _on_button_pressed():
    # 显示标签
    lable.show()

    # 2秒后隐藏标签
    get_tree().create_timer(2.0).timeout.connect(
        func(): lable.hide()
    )

    # 移动精灵
    var tween = create_tween()
    tween.tween_property(sprite, "position", Vector2(100, 100), 1.0)
```
### 节点基本操作总结
1. **创建节点**：``var node = NodeType.new()``
2. **添加节点**：``add_child(node)``
3. **移动节点**：``remove_child(node)``或``node.queue_free()``
4. **显示节点**：``node.show()``或``node.visible = true``
5. **隐藏节点**：``node.hide()``或``node.visible = false``
6. **查找节点**：``get_node("路径")``或``$路径``
7. **连接信号**：``node.signal_name.connect(method_name)``