---
layout: post
title: "Useful batch commands"
categories: tips
author: "Son Pham"
meta: "batch dos cmd shell useful command"
comments: false
public: false
---


### Find task name
```
TASKLIST /v /fo list /fi "imagename eq QXDM.exe" | find "Window Title:"
```

### Run Microsoft Edge wit cmd
```
start msedge.exe lamegaton.github.io
```
You can also open a webpage in private mode by adding '- inprivate' at the end
```
start msedge.exe lamegaton.github.io -inprivate
```