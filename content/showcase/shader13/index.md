---
title: "细胞色块着色 Cell Noise Tint"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader13.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform float cells=30.0;

float hash(vec2 p){return fract(sin(dot(p,vec2(23.2,47.7)))*43758.5);}

void fragment(){
    vec2 id=floor(UV*cells);
    float r=hash(id);
    vec3 col=0.5+0.5*cos(vec3(0,2,4)+r*6.283);
    COLOR=vec4(col,1.0)*texture(TEXTURE,UV).a;
}
```
#### 编辑器调整
<img src="/showcase/shader13/editor13.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">