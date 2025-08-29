---
title: "Godot 信号（Signal）基础教程"
date: 2025-08-29
tags: ["Godot", "教程"]
categories: ["开发"]
draft: false
---
信号是Godot中非常重要的通信机制，允许节点在特定事件发生时通知其他节点。
下面是最基本、最简单的信号使用用例。
### 1. 内置信号 - 按钮点击
```gdscript
extends Control

func _ready():
    # 获取按钮节点（假设场景中有一个名为 Button 的按钮）
    var button = $Button

    # 连接按钮的 pressed 信号到自定义方法
    button.pressed.connect(_on_button_pressed)

# 当按钮背按下时调用的方法
func _on_button_pressed():
    print("按钮被点击了！")
```

### 2. 自定义信号 - 定义和发射
```gdscript
extends Node

# 1. 定义自定义信号
signal player_scored(points)
signal game_over

func _ready():
    # 2. 连接自定义信号到处理方法
    player_scored.connect(_on_player_scored)
    game_over.connect(_on_game_over)

# 3. 在某个条件下发射信号
func add_score(amount):
    print("获取分数：", amount)
    player_scored.emit(amount)   # 发射信号并传递参数

func end_game():
    game_over.emit() # 发射无参数信号

# 4. 处理信号的方法
func _on_player_scored(points):
    print("玩家获得了 %d 分" % points)

func _on_game_over():
    print("游戏结束！")
```

### 3. 通过编辑器连接信号
不写代码也可以连接信号，可以在编辑器中操作：
1. 选择节点
2. 在“节点”选项中选择“信号”标签
3. 双击想要连接的信号
4. 选择目标节点和方法名称
Godot会自动生成代码
```gdscript
func _ready():
    $Button.pressed.connect(_on_button_pressed)
```

### 4. 定时器超时信号
```gdscript
extends Node

func _ready():
    # 创建定时器并设置
    var timer = Timer.new()
    add_child(timer)
    timer.wait_time = 2.0 # 2秒
    timer.one_shot = true # 只执行一次

    # 连接超时信号
    timer.timeout.connect(_on_timer_timeout)

    # 启动定时器
    timer.start()

func _on_timer_timeout():
    print("定时器超时！")
```

### 5. 物体进入区域信号
```gdscript
extends Area2D

func _ready():
    # 连接区域进入信号
    body_entered.connect(_on_body_entered)

func _on_body_entered(body):
    print("有物体进入区域：", body.name)
```

### 关键概念总结
1. **定义信号**:使用``signal signal_name``在脚本顶部定义
2. **连接信号**:使用``signal_name.connect(method_name)``
3. **发射信号**:使用``signal_name.emit()``或``signal_name.emit(parameters)``
4. **处理信号**：创建接收信号的方法， 参数与信号定义匹配



