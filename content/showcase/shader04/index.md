---
title: "阈值黑白 Threshold black and white"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader04.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform float threshold : hint_range(0,1)=0.5;

void fragment() {
    float g = dot(texture(TEXTURE, UV).rgb, vec3(0.299,0.587,0.114));
    COLOR = vec4(vec3(step(threshold, g)), 1.0);
}
```

#### 编辑器调整
<img src="/showcase/shader04/editor04.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">