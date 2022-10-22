---
title: NavigationRail
sidebar_label: NavigationRail
slug: navigationrail
---

A material widget that is meant to be displayed at the left or right of an app to navigate between a small number of views, typically between three and five.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Examples

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet
from flet import (
    Column,
    FloatingActionButton,
    Icon,
    NavigationRail,
    NavigationRailDestination,
    Page,
    Row,
    Text,
    VerticalDivider,
    icons,
)

def main(page: Page):

    rail = NavigationRail(
        selected_index=0,
        label_type="all",
        # extended=True,
        min_width=100,
        min_extended_width=400,
        leading=FloatingActionButton(icon=icons.CREATE, text="Add"),
        group_alignment=-0.9,
        destinations=[
            NavigationRailDestination(
                icon=icons.FAVORITE_BORDER, selected_icon=icons.FAVORITE, label="First"
            ),
            NavigationRailDestination(
                icon_content=Icon(icons.BOOKMARK_BORDER),
                selected_icon_content=Icon(icons.BOOKMARK),
                label="Second",
            ),
            NavigationRailDestination(
                icon=icons.SETTINGS_OUTLINED,
                selected_icon_content=Icon(icons.SETTINGS),
                label_content=Text("Settings"),
            ),
        ],
        on_change=lambda e: print("Selected destination:", e.control.selected_index),
    )

    page.add(
        Row(
            [
                rail,
                VerticalDivider(width=1),
                Column([Text("Body!")], alignment="start", expand=True),
            ],
            expand=True,
        )
    )

flet.app(target=main)
```
  </TabItem>
</Tabs>

<img src="/img/docs/controls/navigation-rail/custom-navrail.png" width="40%" />

## `NavigationRail` properties

### `destinations`

Defines the appearance of the button items that are arrayed within the navigation rail.

The value must be a list of two or more `NavigationRailDestination` instances.

### `selected_index`

The index into `destinations` for the current selected `NavigationRailDestination` or `None` if no destination is selected.

### `extended`

Indicates that the NavigationRail should be in the extended state.

The extended state has a wider rail container, and the labels are positioned next to the icons. `min_extended_width` can be used to set the minimum width of the rail when it is in this state.

The rail will implicitly animate between the extended and normal state.

If the rail is going to be in the extended state, then the `label_type` must be set to `none`.

The default value is `False`.

### `label_type`

Defines the layout and behavior of the labels for the default, unextended NavigationRail.

When a navigation rail is extended, the labels are always shown.

Supported values: `none` (default), `all`, `selected`.

### `bgcolor`

Sets the color of the Container that holds all of the NavigationRail's contents.

### `leading`

An optional leading control in the rail that is placed above the destinations.

Its location is not affected by `group_alignment`.

This is commonly a [`FloatingActionButton`](floatingactionbutton), but may also be a non-button, such as a logo.

### `trailing`

An optional trailing control in the rail that is placed below the destinations.

It's location is affected by `group_alignment`.

This is commonly a list of additional options or destinations that is usually only rendered when `extended` is `True`.

### `min_width`

The smallest possible width for the rail regardless of the destination's icon or label size.

The default is `72`.

This value also defines the min width and min height of the destinations.

To make a compact rail, set this to `56` and use `label_type='none'`.

### `min_extended_width`

The final width when the animation is complete for setting `extended` to `True`.

The default value is `256`.

### `group_alignment`

The vertical alignment for the group of destinations within the rail.

The NavigationRailDestinations are grouped together with the trailing widget, between the leading widget and the bottom of the rail.

The value must be between `-1.0` and `1.0`.

If `group_alignment` is `-1.0`, then the items are aligned to the top. If `group_alignment` is `0.0`, then the items are aligned to the center. If `group_alignment` is `1.0`, then the items are aligned to the bottom.

The default is `-1.0`.

## `NavigationRail` events

### `on_change`

Fires when selected destination changed.

## `NavigationRailDestination` properties

### `icon`

The name of the icon of the destination.

### `icon_content`

The icon `Control` of the destination. Typically the icon is an [`Icon`](icon) control. Used instead of `icon` property.

If `selected_icon_content` is provided, this will only be displayed when the destination is not selected.

To make the NavigationRail more accessible, consider choosing an icon with a stroked and filled version, such as `icons.CLOUD` and `icons.CLOUD_QUEUE`. The icon should be set to the stroked version and `selected_icon` to the filled version.

### `selected_icon`

The name of alternative icon displayed when this destination is selected.

### `selected_icon_content`

An alternative icon `Control` displayed when this destination is selected.

If this icon is not provided, the NavigationRail will display `icon_content` in either state.

### `label`

### `label_content`

The label `Control` for the destination.

The label must be provided when used with the NavigationRail. When `label_type='none'`, the label is still used for semantics, and may still be used if `extended` is `True`.

### `padding`

The amount of space to inset the destination item.

See [`Container.padding`](container#padding) for more information about padding and possible values.