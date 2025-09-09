---
title: "颜色替换 Color replacement"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader07.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform vec3 from_col=vec3(1,0,0);
uniform vec3  to_col=vec3(0,1,1);
uniform float tol:hint_range(0,1)=0.2;

void fragment(){
    vec4 c=texture(TEXTURE,UV);
    float w=smoothstep(tol,0.0,distance(c.rgb,from_col));
    COLOR=vec4(mix(c.rgb, to_col, w), c.a);
}
```

### 编辑器部分
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader07/editor07.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">