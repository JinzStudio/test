---
title: "斜向线性擦除 Diagonal Linear Wipe"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader10.gif"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform float progress:hint_range(0,1)=0.5;
uniform float slope=1.0;

void fragment(){
    float line = UV.x + UV.y*slope;
    float mask = step(line, progress*(1.0+slope));
    COLOR = texture(TEXTURE,UV)*mask;
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

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">