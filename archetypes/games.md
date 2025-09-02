---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
description: ""
cover:
  image: "cover.jpg"
  alt: ""
  caption: ""
  hidden: false
rating:
free: true
tags: []
play_url: "/games/{{ .Name }}/"   # 如用本地静态可玩版本
---
在这里写游戏简介、操作说明等。
