---
title: Tabs
sidebar_label: Tabs
slug: tabs
---

The Tabs control is used for navigating frequently accessed, distinct content categories. Tabs allow for navigation between two or more content views and relies on text headers to articulate the different sections of content.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Examples

### Tabs

<img src="/img/docs/controls/tabs/tabs-simple.gif" className="screenshot-60"/>

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):

    t = ft.Tabs(
        selected_index=1,
        animation_duration=300,
        tabs=[
            ft.Tab(
                text="Tab 1",
                content=ft.Container(
                    content=ft.Text("This is Tab 1"), alignment=ft.alignment.center
                ),
            ),
            ft.Tab(
                tab_content=ft.Icon(ft.icons.SEARCH),
                content=ft.Text("This is Tab 2"),
            ),
            ft.Tab(
                text="Tab 3",
                icon=ft.icons.SETTINGS,
                content=ft.Text("This is Tab 3"),
            ),
        ],
        expand=1,
    )

    page.add(t)

ft.app(target=main)
```
  </TabItem>
</Tabs>

## `Tabs` properties

### `animation_duration`

Duration of animation in milliseconds of swtiching between tabs. Default is `50`.

### `selected_index`

The index of currently selected tab.

### `tabs`

A list of `Tab` controls.

## `Tabs` events

### `on_change`

Fires when `selected_index` changes.

## `Tab` properties

### `content`

A `Control` to display below the Tab when it is selected.

### `icon`

An icon to display on the left of Tab text.

### `tab_content`

A `Control` representing custom tab content replacing `text` and `icon`.

### `text`

Tab's display name.