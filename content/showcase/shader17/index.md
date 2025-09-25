---
title: "太阳光芒叠加 sun flare overlay shader"
description: "Shader"
date: 2025-09-15
category: "Canvas Item"
cover:
  image: "shader17.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform vec2 center=vec2(0.5);
uniform float rays=24.0;

void fragment(){
    float ang=atan(UV.y-center.y, UV.x-center.x);
    float k=abs(sin(ang*rays));
    COLOR=texture(TEXTURE,UV) + vec4(vec3(k*0.15),0.0);
}
```
#### 编辑器调整
<img src="/showcase/shader17/editor17.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">