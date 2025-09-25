---
title: "桶形/枕形畸变 Barrel/Pincushion Distortion"
description: "Shader"
date: 2025-09-15
category: "Canvas Item"
cover:
  image: "shader16.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform float k=0.2; // 正：桶形；负：枕形

void fragment(){
    vec2 p=UV*2.0-1.0;
    p *= 1.0 + k*dot(p,p);
    COLOR=texture(TEXTURE,(p+1.0)*0.5);
}
```
#### 编辑器调整
<img src="/showcase/shader16/editor16.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">