---
title: "颜色通道轮换 RGB Swapping"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader06.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

void fragment(){
    vec3 c=texture(TEXTURE,UV).rgb;
    COLOR=vec4(c.g, c.b, c.r, 1.0);
}
```

### 简单解释
```gdscript
R -> G G -> B B ->R
R G B 
G B R
```
#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">