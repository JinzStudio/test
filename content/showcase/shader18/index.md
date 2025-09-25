---
title: "碎片随机溶解 fragment random dissolve shader"
description: "Shader"
category: "Canvas Item"
date: 2025-09-15
cover:
  image: "shader18.gif"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

float rand(vec2 p){return fract(sin(dot(p,vec2(12.3,45.6)))*43758.5);}
uniform float progress:hint_range(0,1)=0.5;

void fragment(){
    vec2 cell=floor(UV*40.0);
    float r=rand(cell);
    COLOR=texture(TEXTURE,UV)*step(progress,r);
}
```

#### GDScript 代码部分
```gdscript
extends TextureRect

func _process(delta):
	var mat = material
	if mat:
		var current_progress = mat.get_shader_parameter("progress")
		current_progress += delta  # 线性增加
		if current_progress > 3.0:
			current_progress = 0.0  # 超过1后重置为0循环
		mat.set_shader_parameter("progress", current_progress)
```
#### 编辑器调整
<img src="/showcase/shader18/editor18.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">