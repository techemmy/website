---
title: ProgressRing
sidebar_label: ProgressRing
slug: progressring
---

A material design circular progress indicator, which spins to indicate that the application is busy.

A control that shows progress along a circle.

There are two kinds of circular progress indicators:

* *Determinate*. Determinate progress indicators have a specific value at each point in time, and the value should increase monotonically from `0.0` to `1.0`, at which time the indicator is complete. To create a determinate progress indicator, use a non-null value between `0.0` and `1.0`.
* *Indeterminate*. Indeterminate progress indicators do not have a specific value at each point in time and instead indicate that progress is being made without indicating how much progress remains. To create an indeterminate progress indicator, use a null value.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Examples

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
from time import sleep
import flet as ft

def main(page: ft.Page):
    pr = ft.ProgressRing(width=16, height=16, stroke_width = 2)

    page.add(
        ft.Text("Circular progress indicator", style="headlineSmall"),
        ft.Row([pr, ft.Text("Wait for the completion...")]),
        ft.Text("Indeterminate cicrular progress", style="headlineSmall"),
        ft.Column(
            [ft.ProgressRing(), ft.Text("I'm going to run for ages...")],
            horizontal_alignment=ft.CrossAxisAlignment.CENTER,
        ),
    )

    for i in range(0, 101):
        pr.value = i * 0.01
        sleep(0.1)
        page.update()

ft.app(target=main)
```
  </TabItem>
</Tabs>

<img src="/img/docs/controls/progress-ring/custom-progress-rings.gif" className="screenshot-30"/>

## Properties

### `bgcolor`

Color of the circular track being filled by the circular indicator.

### `color`

The progress indicator's color.

### `stroke_width`

The width of the line used to draw the circle.

### `tooltip`

The text displayed when hovering the mouse over the control.

### `value`

The value of this progress indicator. A value of 0.0 means no progress and 1.0 means that progress is complete. The value will be clamped to be in the range 0.0-1.0. If null, this progress indicator is indeterminate, which means the indicator displays a predetermined animation that does not indicate how much actual progress is being made.