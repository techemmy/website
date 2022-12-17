---
title: Column
sidebar_label: Column
slug: column
---

A control that displays its children in a vertical array.

To cause a child control to expand and fill the available vertical space set its `expand` property.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Examples

### Column spacing

<img src="/img/docs/controls/column/column-spacing.gif" className="screenshot-50"/>

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):
    def items(count):
        items = []
        for i in range(1, count + 1):
            items.append(
                ft.Container(
                    content=ft.Text(value=str(i)),
                    alignment=ft.alignment.center,
                    width=50,
                    height=50,
                    bgcolor=ft.colors.AMBER,
                    border_radius=ft.border_radius.all(5),
                )
            )
        return items

    def spacing_slider_change(e):
        col.spacing = int(e.control.value)
        col.update()

    gap_slider = ft.Slider(
        min=0,
        max=100,
        divisions=10,
        value=0,
        label="{value}",
        width=500,
        on_change=spacing_slider_change,
    )

    col = ft.Column(spacing=0, controls=items(5))

    page.add(ft.Column([ ft.Text("Spacing between items"), gap_slider]), col)

ft.app(target=main)
```
  </TabItem>
</Tabs>

### Column wrapping

<img src="/img/docs/controls/column/column-wrapping.gif" className="screenshot-70"/>

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

HEIGHT = 400

def main(page: ft.Page):
    def items(count):
        items = []
        for i in range(1, count + 1):
            items.append(
                ft.Container(
                    content=ft.Text(value=str(i)),
                    alignment=ft.alignment.center,
                    width=30,
                    height=30,
                    bgcolor=ft.colors.AMBER,
                    border_radius=ft.border_radius.all(5),
                )
            )
        return items

    def slider_change(e):
        col.height = float(e.control.value)
        col.update()

    width_slider = ft.Slider(
        min=0,
        max=HEIGHT,
        divisions=20,
        value=HEIGHT,
        label="{value}",
        width=500,
        on_change=slider_change,
    )

    col = ft.Column(
        wrap=True,
        spacing=10,
        run_spacing=10,
        controls=items(10),
        height=HEIGHT,
    )

    page.add(
        ft.Column(
            [
                ft.Text(
                    "Change the column height to see how child items wrap onto multiple columns:"
                ),
                width_slider,
            ]
        ),
        ft.Container(content=col, bgcolor=ft.colors.AMBER_100),
    )

ft.app(target=main)
```
  </TabItem>
</Tabs>

### Column vertical alignments

<img src="/img/docs/controls/column/column-alignment.png"  className="screenshot-70"/>

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):
    def items(count):
        items = []
        for i in range(1, count + 1):
            items.append(
                ft.Container(
                    content=ft.Text(value=str(i)),
                    alignment=ft.alignment.center,
                    width=50,
                    height=50,
                    bgcolor=ft.colors.AMBER_500,
                )
            )
        return items

    def column_with_alignment(align: ft.MainAxisAlignment):
        return ft.Column(
            [
                ft.Text(str(align), size=10),
                ft.Container(
                    content=ft.Column(items(3), alignment=align),
                    bgcolor=ft.colors.AMBER_100,
                    height=400,
                ),
            ]
        )

    page.add(
        ft.Row(
            [
                column_with_alignment(ft.MainAxisAlignment.START),
                column_with_alignment(ft.MainAxisAlignment.CENTER),
                column_with_alignment(ft.MainAxisAlignment.END),
                column_with_alignment(ft.MainAxisAlignment.SPACE_BETWEEN),
                column_with_alignment(ft.MainAxisAlignment.SPACE_AROUND),
                column_with_alignment(ft.MainAxisAlignment.SPACE_EVENLY),
            ],
            spacing=30,
            alignment=ft.MainAxisAlignment.START,
        )
    )

ft.app(target=main)
```
  </TabItem>
</Tabs>

### Column horizontal alignments

<img src="/img/docs/controls/column/column-horiz-alignment.png"  className="screenshot-50" />

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page: ft.Page):
    def items(count):
        items = []
        for i in range(1, count + 1):
            items.append(
                ft.Container(
                    content=ft.Text(value=str(i)),
                    alignment=ft.alignment.center,
                    width=50,
                    height=50,
                    bgcolor=ft.colors.AMBER_500,
                )
            )
        return items

    def column_with_horiz_alignment(align: ft.CrossAxisAlignment):
        return ft.Column(
            [
                ft.Text(str(align), size=16),
                ft.Container(
                    content=ft.Column(
                        items(3),
                        alignment=ft.MainAxisAlignment.START,
                        horizontal_alignment=align,
                    ),
                    bgcolor=ft.colors.AMBER_100,
                    width=100,
                ),
            ]
        )

    page.add(
        ft.Row(
            [
                column_with_horiz_alignment(ft.CrossAxisAlignment.START),
                column_with_horiz_alignment(ft.CrossAxisAlignment.CENTER),
                column_with_horiz_alignment(ft.CrossAxisAlignment.END),
            ],
            spacing=30,
            alignment=ft.MainAxisAlignment.START,
        )
    )

ft.app(target=main)
```
  </TabItem>
</Tabs>

## Properties

### `alignment`

How the child Controls should be placed vertically.

Property value is `MainAxisAlignment` enum with the following values:

* `START` (default)
* `END`
* `CENTER`
* `SPACE_BETWEEN`
* `SPACE_AROUND`
* `SPACE_EVENLY`

### `auto_scroll`

`True` if scrollbar should automatically move its position to the end when children update.

### `controls`

A list of Controls to display inside the Column.

### `horizontal_alignment`

How the child Controls should be placed horizontally.

Property value is `CrossAxisAlignment` enum with the following values:

* `START` (default)
* `CENTER`
* `END`
* `STRETCH`
* `BASELINE`

### `scroll`

Enables a vertical scrolling for the Column to prevent its content overflow.

Property value is an optional `ScrollMode` enum with `None` as default.

Supported values:

* `None` (default) - the Row is non-scrollable and its content could overflow.
* `AUTO` - scrolling is enabled and scroll bar is only shown when scrolling occurs.
* `ADAPTIVE` - scrolling is enabled and scroll bar is always shown when running app as web or desktop.
* `ALWAYS` - scrolling is enabled and scroll bar is always shown.
* `HIDDEN` - scrolling is enabled, but scroll bar is always hidden.

### `spacing`

Spacing between controls in a Column. Default value is 10 virtual pixels. Spacing is applied only when `alignment` is set to `start`, `end` or `center`.

### `run_spacing`

Spacing between runs when `wrap=True`. Default value is 10.

### `tight`

Specifies how much space should be occupied vertically. Default is `False` - allocate all space to children.

### `wrap`

When set to `True` the Column will put child controls into additional columns (runs) if they don't fit a single column.

## Expanding children

When a child Control is placed into a Column you can "expand" it to fill the available space. Every Control has `expand` property that can have either a boolean value (`True` - expand control to fill all available space) or an integer - an "expand factor" specifying how to divide a free space with other expanded child controls. For example, this code creates a column with a Container taking all available space and a Text control at the bottom serving as a status bar:

```python
r = ft.Column([
  ft.Container(expand=True, content=ft.Text("Here is search results")),
  ft.Text("Records found: 10")
])
```

The following example with numeric expand factors creates a Column with 3 containers in it and having heights of `20% (1/5)`, `60% (3/5)` and `20% (1/5)` respectively:

```python
r = ft.Column([
  ft.Container(expand=1, content=ft.Text("Header")),
  ft.Container(expand=3, content=ft.Text("Body")),
  ft.Container(expand=1, content=ft.Text("Footer"))
])
```

In general, the resulting height of a child in percents is calculated as `expand / sum(all expands) * 100%`.