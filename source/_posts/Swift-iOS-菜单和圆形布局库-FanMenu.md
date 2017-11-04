---
layout: title
title: Swift iOS 菜单和圆形布局库 FanMenu
date: 2017-11-04 08:26:42
tags:
- swift库
---

### FanMenu 是一个菜单和 圆形布局类库，基于 [Macaw](https://github.com/exyte/fan-menu)，用Swift编写。介绍在我上一篇文章中有讲。

<!-- more -->

![p1.gif](https://ooo.0o0.ooo/2017/11/04/59fdb3713ca9d.gif)



![p2.gif](https://ooo.0o0.ooo/2017/11/04/59fdb3710d8dc.gif)

用法** 

1. 在您的故事板或程序中创建UIView。 
2. 将FanMenu设置为UIView类 
3. 设置按钮 

```swift
fanMenu.button = FanMenuButton(
id: "main",
image: "plus",
color: Color(val: 0x7C93FE)
)
```

**4. 设置菜单项** 

```swift
fanMenu.items = [
FanMenuButton(
id: "exchange_id",
image: "exchange",
color: Color(val: 0x9F85FF)
),
  ...
FanMenuButton(
id: "visa_id",
image: "visa",
color: Color(val: 0xF55B58)
)
]
```

**5. 添加事件处理程序**

```swift
//call before animation
fanMenu.onItemDidClick = { button in
print("ItemDidClick: \(button.id)")
}
// call after animation

fanMenu.onItemWillClick = { button in
print("ItemWillClick: \(button.id)")
}
```
