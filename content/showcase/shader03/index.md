---
title: "噪声边缘擦除 Noise edge erasing"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader03.gif"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

float hash(vec2 p){return fract(sin(dot(p,vec2(17.3,41.7)))*43758.5);}

uniform float progress:hint_range(0,1)=0.5;

void fragment(){
    float n=hash(UV*600.0);
    float m=step(UV.x + (n-0.5)*0.05, progress);
    COLOR=texture(TEXTURE,UV)*m;
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
<img src="/showcase/shader03/editor03.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">