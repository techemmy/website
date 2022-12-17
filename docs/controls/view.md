---
title: View
sidebar_label: View
slug: view
---

View is the top most container for all other controls.

A root view is automatically created when a new user session started. From layout perspective the View represents a [Column](column) control, so it has a similar behavior and shares same properties.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Properties

### `appbar`

A [`AppBar`](/docs/controls/appbar) control to display at the top of the Page.

### `auto_scroll`

`True` if scrollbar should automatically move its position to the end when children update.

### `bgcolor`

Background color of the Page.

A color value could be a hex value in `#ARGB` format (e.g. `#FFCC0000`), `#RGB` format (e.g. `#CC0000`) or a named color from `flet.colors` module.

### `controls`

A list of Controls to display on the Page.

For example, to add a new control to a page:

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
page.controls.append(ft.Text("Hello!"))
page.update()
```

  </TabItem>
</Tabs>

or to get the same result as above using `page.add()` shortcut method:

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
page.add(ft.Text("Hello!"))
```

  </TabItem>
</Tabs>

To remove the top most control on the page:

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
page.controls.pop()
page.update()
```

  </TabItem>
</Tabs>
### `route`

View's route - not currently used by Flet framework, but can be used in a user program to update [`page.route`](/docs/controls/page#route) when a view poped.

### `floating_action_button`

A [`FloatingActionButton`](/docs/controls/floatingactionbutton) control to display on top of Page content.

### `horizontal_alignment`

How the child Controls should be placed horizontally.

Default value is `CrossAxisAlignment.START` which means on the left side of the Page.

Property value is `CrossAxisAlignment` enum with the following values:

* `START` (default)
* `CENTER`
* `END`
* `STRETCH`
* `BASELINE`

### `padding`

A space between page contents and its edges. Default value is 10 pixels from each side. To set zero padding:

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
page.padding = 0
page.update()
```

  </TabItem>
</Tabs>

See [`Container.padding`](container#padding) for more information and possible values.

### `scroll`

Enables a vertical scrolling for the Page to prevent its content overflow.

Property value is an optional `ScrollMode` enum with `None` as default.

Supported values:

* `None` (default) - the Row is non-scrollable and its content could overflow.
* `AUTO` - scrolling is enabled and scroll bar is only shown when scrolling occurs.
* `ADAPTIVE` - scrolling is enabled and scroll bar is always shown when running app as web or desktop.
* `ALWAYS` - scrolling is enabled and scroll bar is always shown.
* `HIDDEN` - scrolling is enabled, but scroll bar is always hidden.

### `spacing`

Vertical spacing between controls on the Page. Default value is 10 virtual pixels. Spacing is applied only when `alignment` is set to `start`, `end` or `center`.

### `vertical_alignment`

How the child Controls should be placed vertically.

For example, `MainAxisAlignment.START`, the default, places the children at the top of a Page.

Property value is `MainAxisAlignment` enum with the following values:

* `START` (default)
* `END`
* `CENTER`
* `SPACE_BETWEEN`
* `SPACE_AROUND`
* `SPACE_EVENLY`