---
title: Stack
sidebar_label: Stack
slug: stack
---

A control that positions its children on top of each other.

This control is useful if you want to overlap several children in a simple way, for example having some text and an image, overlaid with a gradient and a button attached to the bottom.

Stack is also useful if you want to implement [implicit animations](/docs/guides/python/animations) that require knowing absolute position of a target value.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Examples

### Transparent title over an image

<img src="/img/docs/controls/stack/image-title.png" className="screenshot-50" />

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):
    st = ft.Stack(
        [
            ft.Image(
                src=f"https://picsum.photos/300/300",
                width=300,
                height=300,
                fit=ft.ImageFit.CONTAIN,
            ),
            ft.Row(
                [
                    ft.Text(
                        "Image title",
                        color="white",
                        size=40,
                        weight="bold",
                        opacity=0.5,
                    )
                ],
                alignment=ft.MainAxisAlignment.CENTER,
            ),
        ],
        width=300,
        height=300,
    )

    page.add(st)

ft.app(target=main)
```

  </TabItem>
</Tabs>

### Avatar with online status

<img src="/img/docs/controls/stack/avatar-with-status.png" className="screenshot-10"/>

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page):
    page.add(
        ft.Stack(
            [
                ft.CircleAvatar(
                    foreground_image_url="https://avatars.githubusercontent.com/u/5041459?s=88&v=4"
                ),
                ft.Container(
                    content=ft.CircleAvatar(bgcolor=ft.colors.GREEN, radius=5),
                    alignment=ft.alignment.bottom_left,
                ),
            ],
            width=40,
            height=40,
        )
    )

ft.app(target=main, view=ft.WEB_BROWSER)
```

  </TabItem>
</Tabs>

### Absolute positioning inside Stack

<img src="/img/docs/controls/stack/absolute-positioned.png" className="screenshot-50"/>

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):

    page.horizontal_alignment = ft.CrossAxisAlignment.CENTER
    page.vertical_alignment = ft.MainAxisAlignment.CENTER

    page.add(
        ft.Container(
            ft.Stack(
                [
                    ft.Container(width=20, height=20, bgcolor=ft.colors.RED, border_radius=5),
                    ft.Container(
                        width=20,
                        height=20,
                        bgcolor=ft.colors.YELLOW,
                        border_radius=5,
                        right=0,
                    ),
                    ft.Container(
                        width=20,
                        height=20,
                        bgcolor=ft.colors.BLUE,
                        border_radius=5,
                        right=0,
                        bottom=0,
                    ),
                    ft.Container(
                        width=20,
                        height=20,
                        bgcolor=ft.colors.GREEN,
                        border_radius=5,
                        left=0,
                        bottom=0,
                    ),
                    ft.Column(
                        [
                            ft.Container(
                                width=20,
                                height=20,
                                bgcolor=ft.colors.PURPLE,
                                border_radius=5,
                            )
                        ],
                        left=35,
                        top=35,
                    ),
                ]
            ),
            border_radius=8,
            padding=5,
            width=100,
            height=100,
            bgcolor=ft.colors.BLACK,
        )
    )

ft.app(target=main)
```

  </TabItem>
</Tabs>

## Properties

### `clip_behavior`

The content will be clipped (or not) according to this option.

Property value is `ClipBehavior` enum with supported values:

* `NONE`
* `ANTI_ALIAS`
* `ANTI_ALIAS_WITH_SAVE_LAYER`
* `HARD_EDGE` (default)

### `controls`

A list of Controls to display inside the Stack. The last control in the list is displayed on top.