---
title: "像素马赛克 Pixel Mosaic"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader12.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform float block=40.0;

void fragment(){
    vec2 uv=floor(UV*block)/block;
    COLOR=texture(TEXTURE,uv);
}
```
#### 编辑器调整
<img src="/showcase/shader12/editor12.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">