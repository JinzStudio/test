---
title: "投影 Projection"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader15.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform vec2  offset = vec2(2.0,2.0);
uniform vec4  shadow:source_color = vec4(0,0,0,0.5);

void fragment(){
    vec2 px = TEXTURE_PIXEL_SIZE*offset;
    vec4 s = vec4(shadow.rgb, shadow.a*texture(TEXTURE, UV+px).a);
    vec4 b = texture(TEXTURE, UV);
    COLOR = max(s, b);
}
```
#### 编辑器调整
<img src="/showcase/shader15/editor15.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">