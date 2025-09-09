---
title: "液体涟漪遮罩 Ripple mask"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader05.gif"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform vec2 center=vec2(0.5);

void fragment(){
    float r=distance(UV,center);
    float ripple=sin(r*50.0-TIME*5.0)*0.05;
    COLOR=texture(TEXTURE,UV+normalize(UV-center)*ripple);
}
```

#### 编辑器调整
<img src="/showcase/shader05/editor05.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">