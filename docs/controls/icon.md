---
title: Icon
sidebar_label: Icon
slug: icon
---

Displays a Material icon.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

[Icons browser](https://flet-icons-browser.fly.dev/#/)

## Examples

### Icons with different colors and sizes

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):
    page.add(
        ft.Row(
            [
                ft.Icon(name=ft.icons.FAVORITE, color=ft.colors.PINK),
                ft.Icon(name=ft.icons.AUDIOTRACK, color=ft.colors.GREEN_400, size=30),
                ft.Icon(name=ft.icons.BEACH_ACCESS, color=ft.colors.BLUE, size=50),
                ft.Icon(name="settings", color="#c1c1c1"),
            ]
        )
    )

ft.app(target=main)
```
  </TabItem>
</Tabs>

<img src="/img/docs/controls/icon/custom-icons.png" className="screenshot-20" />

## Properties

### `color`

Icon color.

### `name`

The name of the icon. You can search through the list of all available icons using open-source [Icons browser](https://flet-icons-browser.fly.dev/#/) app [written in Flet](https://github.com/flet-dev/examples/blob/main/python/apps/icons-browser/main.py).

### `size`

Icon size. Default is 24.

### `tooltip`

The text displayed when hovering a mouse over the Icon.