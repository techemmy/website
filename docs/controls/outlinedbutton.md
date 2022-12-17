---
title: OutlinedButton
sidebar_label: OutlinedButton
slug: outlinedbutton
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

Outlined buttons are medium-emphasis buttons. They contain actions that are important, but aren’t the primary action in an app.
Outlined buttons pair well with filled buttons to indicate an alternative, secondary action. See [Material 3 buttons](https://m3.material.io/components/buttons/overview) for more info.

## Examples

### Basic outlined buttons

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft


def main(page: ft.Page):
    page.title = "Basic outlined buttons"
    page.add(
        ft.OutlinedButton(text="Outlined button"),
        ft.OutlinedButton("Disabled button", disabled=True),
    )

ft.app(target=main)
```
  </TabItem>

</Tabs>

<img src="/img/docs/controls/outlined-button/basic-outlined-buttons.png" className="screenshot-40" />

### Outlined buttons with icons

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft


def main(page: ft.Page):
    page.title = "Outlined buttons with icons"
    page.add(
        ft.OutlinedButton("Button with icon", icon="chair_outlined"),
        ft.OutlinedButton(
            "Button with colorful icon",
            icon="park_rounded",
            icon_color="green400",
        ),
    )

ft.app(target=main)
```
  </TabItem>

</Tabs>

<img src="/img/docs/controls/outlined-button/outlined-buttons-with-icons.png" className="screenshot-50" />

### Outlined button with `click` event

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft


def main(page: ft.Page):
    page.title = "Outlined button with 'click' event"

    def button_clicked(e):
        b.data += 1
        t.value = f"Button clicked {b.data} time(s)"
        page.update()

    b = ft.OutlinedButton("Button with 'click' event", on_click=button_clicked, data=0)
    t = ft.Text()

    page.add(b, t)

ft.app(target=main)
```

  </TabItem>

</Tabs>

<img src="/img/docs/controls/outlined-button/outlined-button-with-click-event.gif" className="screenshot-50" />

### Outlined button with custom content 

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):
    page.title = "Outlined buttons with custom content"
    page.add(
        ft.OutlinedButton(
            width=150,
            content=ft.Row(
                [
                    ft.Icon(name=ft.icons.FAVORITE, color="pink"),
                    ft.Icon(name=ft.icons.AUDIOTRACK, color="green"),
                    ft.Icon(name=ft.icons.BEACH_ACCESS, color="blue"),
                ],
                alignment=ft.MainAxisAlignment.SPACE_AROUND,
            ),
        ),
        ft.OutlinedButton(
            content=ft.Container(
                content=ft.Column(
                    [
                        ft.Text(value="Compound button", size=20),
                        ft.Text(value="This is secondary text"),
                    ],
                    alignment=ft.MainAxisAlignment.CENTER,
                    spacing=5,
                ),
                padding=ft.padding.all(10),
            ),
        ),
    )

ft.app(target=main)

```

  </TabItem>
  
</Tabs>

<img src="/img/docs/controls/outlined-button/outlined-buttons-with-custom-content.png" className="screenshot-50" />


## Properties

### `autofocus`

True if the control will be selected as the initial focus. If there is more than one control on a page with autofocus set, then the first one added to the page will get focus.

### `content`

A Control representing custom button content.

### `icon`

Icon shown in the button.

### `icon_color`

Icon color.

### `style`

See [ElevatedButton.style](/docs/controls/elevatedbutton#style) for more information about this property.

### `text`

The text displayed on a button.

### `tooltip`

The text displayed when hovering the mouse over the button.

## Events

### `on_click`

Fires when a user clicks the button.

### `on_hover`

Fires when a mouse pointer enters or exists the button response area. `data` property of event object contains `true` (string) when cursor enters and `false` when it exits.

### `on_long_press`

Fires when the button is long-pressed.