---
title: FilledButton
sidebar_label: FilledButton
slug: filledbutton
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

Filled buttons have the most visual impact after the [FloatingActionButton](floatingactionbutton), and should be used for important, final actions that complete a flow, like **Save**, **Join now**, or **Confirm**. See [Material 3 buttons](https://m3.material.io/components/buttons/overview) for more info.

<img src="/img/docs/controls/filled-button/basic-filled-buttons.png" className="screenshot-20" />

## Examples

### Filled button

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft


def main(page: ft.Page):
    page.title = "Basic filled buttons"
    page.add(
        ft.FilledButton(text="Filled button"),
        ft.FilledButton("Disabled button", disabled=True),
        ft.FilledButton("Button with icon", icon="add"),
    )

ft.app(target=main)
```
  </TabItem>

</Tabs>

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