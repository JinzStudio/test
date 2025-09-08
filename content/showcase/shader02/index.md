---
title: "噪声遮罩 Noise masking"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader02.gif"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### 代码部分
```gdscript
shader_type canvas_item;

float rand(vec2 p){return fract(sin(dot(p,vec2(12.3,45.6)))*43758.5);}

uniform float cutoff:hint_range(0,1)=0.5;

void fragment(){
    float r=rand(UV*vec2(300.0,TIME));
    COLOR=texture(TEXTURE,UV)*step(cutoff,r);
}
```

#### 编辑器调整
<img src="/showcase/shader02/editor2.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">