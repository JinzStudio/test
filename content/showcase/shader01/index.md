---
title: "纵向倾斜移行 Longitudinal oblique translation"
description: "Shader"
category: "Canvas Item"
cover:
  image: "01.jpg"
  alt: "元素Match 封面"
---
#### 代码部分
```gdscript
shader_type canvas_item;
uniform float shift=0.01;
void fragment(){
    vec2 uv=UV;
    if (int(floor(UV.y / TEXTURE_PIXEL_SIZE.y)) % 2 == 0) uv.x += shift;
    COLOR=texture(TEXTURE,uv);
}
```

#### 编辑器调整
<img src="/showcase/shader01/editor.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">