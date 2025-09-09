---
title: "旋转模糊 Spin Blur"
description: "Shader"
category: "Canvas Item"
cover:
  image: "shader09.jpg"
  alt: "一只可爱的胡萝卜君"
#play_url: "/play/cookie-clicker/" 
---
#### Shader 代码部分
```gdscript
shader_type canvas_item;

uniform int samples=6;
uniform float angle=0.2;

void fragment(){
    vec2 p=UV-0.5; float r=length(p); float a=atan(p.y,p.x);
    vec4 acc=vec4(0.0);
    for(int i=0;i<6;i++){
        float t=(float(i)/float(max(samples,1))-0.5)*angle;
        vec2 uv=0.5+vec2(cos(a+t),sin(a+t))*r;
        acc+=texture(TEXTURE,uv);
    }
    COLOR=acc/float(max(samples,1));
}

```

### 编辑器部分
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader09/editor09.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">

#### 原型参考
<!-- 固定显示 480px 宽，随屏幕缩小时能自适应 -->
<img src="/showcase/shader01/normal.jpg"
     alt="封面"
     style="width:200px;max-width:100%;height:200;border-radius:12px;">