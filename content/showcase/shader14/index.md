---
title: "伪色分档 False Color Grading"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader14.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform int bands = 3;

void fragment() {
    vec3 c = texture(TEXTURE, UV).rgb;
    COLOR = vec4(floor(c*float(bands))/float(bands), 1.0);
}
```
#### 编辑器调整
<img src="/showcase/shader14/editor14.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">