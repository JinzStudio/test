---
title: "像素网格描边 Pixel Grid Outline"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader11.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;
uniform float size=20.0;
void fragment(){
    vec2 g=fract(UV*size);
    float edge=step(0.95,g.x)+step(0.95,g.y);
    COLOR=mix(texture(TEXTURE,UV),vec4(0,0,0,1),clamp(edge,0.0,1.0));
}
```
#### 编辑器调整
<img src="/showcase/shader11/editor11.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">