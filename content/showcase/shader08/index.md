---
title: "漩涡扭转 Polar Warping"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader08.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform vec2 center = vec2(0.5);
uniform float power = 1.0;

void fragment() {
    vec2 p = UV - center;
    float r = length(p);
    float a = atan(p.y,p.x) + power*r;
    vec2 uv = center + vec2(cos(a), sin(a))*r;
    COLOR = texture(TEXTURE, uv);
}

```

### 编辑器部分
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader08/editor08.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">