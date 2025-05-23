---
sidebar_position: 2
description: Learn how to use Yazi's Lua API.
---

# Layout

Text, List, Bar, Border, and Gauge are renderable elements; others need to be placed within any of them.

## Rect {#rect}

A Rect is represented an area within the terminal by four attributes:

```lua
ui.Rect {
	x = 10, -- x position
	y = 10, -- y position
	w = 20, -- width
	h = 30, -- height
}

ui.Rect.default  -- Equal to `ui.Rect { x = 0, y = 0, w = 0, h = 0 }`
```

You can get a pre-computed `Rect` through [`ui.Layout()`](#layout).
Note that if you intend to create a `Rect` yourself, ensure these values are calculated accurately; otherwise, it may cause Yazi to crash!

### `x` {#rect.x}

X position of the rect.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `y` {#rect.y}

Y position of the rect.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `w` {#rect.w}

Width of the rect.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `h` {#rect.h}

Height of the rect.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `left` {#rect.left}

Left position of the rect.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `right` {#rect.right}

Right position of the rect.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `top` {#rect.top}

Top position of the rect.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `bottom` {#rect.bottom}

Bottom position of the rect.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `pad(self, padding)` {#rect.pad}

Apply a `padding` to the rect.

| In/Out    | Type          |
| --------- | ------------- |
| `self`    | `Rect`        |
| `padding` | [`Pad`](#pad) |
| Return    | `self`        |

### `__new(value)` {#rect.\_\_new}

| In/Out  | Type                                                     |
| ------- | -------------------------------------------------------- |
| `value` | `{ x: integer?, y: integer?, w: integer?, h: integer? }` |
| Return  | `Rect`                                                   |

## Pad {#pad}

`Pad` represents a padding, and all of its parameters are integers:

```lua
ui.Pad(top, right, bottom, left)
```

### `top` {#pad.top}

Top padding.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `right` {#pad.right}

Right padding.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `bottom` {#pad.bottom}

Bottom padding.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `left` {#pad.left}

Left padding.

|      |           |
| ---- | --------- |
| Type | `integer` |

### `top(top)` {#pad.Top}

Create a padding with only top value, which is equal to `ui.Pad(top, 0, 0, 0)`.

| In/Out | Type      |
| ------ | --------- |
| `top`  | `integer` |
| Return | `Pad`     |

### `right(right)` {#pad.Right}

Create a padding with only right value, which is equal to `ui.Pad(0, right, 0, 0)`.

| In/Out  | Type      |
| ------- | --------- |
| `right` | `integer` |
| Return  | `Pad`     |

### `bottom(bottom)` {#pad.Bottom}

Create a padding with only bottom value, which is equal to `ui.Pad(0, 0, bottom, 0)`.

| In/Out   | Type      |
| -------- | --------- |
| `bottom` | `integer` |

| Return | `Pad` |

### `left(left)` {#pad.Left}

Create a padding with only left value, which is equal to `ui.Pad(0, 0, 0, left)`.

| In/Out | Type      |
| ------ | --------- |
| `left` | `integer` |
| Return | `Pad`     |

### `x(x)` {#pad.X}

Create a padding on both x-axis, which is equal to `ui.Pad(0, x, 0, x)`.

| In/Out | Type      |
| ------ | --------- |
| `x`    | `integer` |
| Return | `Pad`     |

### `y(y)` {#pad.Y}

Create a padding on both y-axis, which is equal to `ui.Pad(y, 0, y, 0)`.

| In/Out | Type      |
| ------ | --------- |
| `y`    | `integer` |
| Return | `Pad`     |

### `xy(x, y)` {#pad.XY}

Create a padding on both x and y-axis, which is equal to `ui.Pad(y, x, y, x)`.

| In/Out | Type      |
| ------ | --------- |
| `x`    | `integer` |
| `y`    | `integer` |
| Return | `Pad`     |

### `__new(top, right, bottom, left)` {#pad.\_\_new}

| In/Out   | Type      |
| -------- | --------- |
| `top`    | `integer` |
| `right`  | `integer` |
| `bottom` | `integer` |
| `left`   | `integer` |
| Return   | `Pad`     |

## Style {#style}

Create a style:

```lua
ui.Style()
```

### `fg(self, color)` {#style.fg}

Apply a foreground color.

| In/Out  | Type                                             |
| ------- | ------------------------------------------------ |
| `self`  | `Style`                                          |
| `color` | [`Color`](/docs/configuration/theme#types.color) |
| Return  | `self`                                           |

### `bg(self, color)` {#style.bg}

Apply a background color.

| In/Out  | Type                                             |
| ------- | ------------------------------------------------ |
| `self`  | `Style`                                          |
| `color` | [`Color`](/docs/configuration/theme#types.color) |
| Return  | `self`                                           |

### `bold(self)` {#style.bold}

Apply a bold style.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `dim(self)` {#style.dim}

Apply a dim style.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `italic(self)` {#style.italic}

Apply an italic style.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `underline(self)` {#style.underline}

Apply an underline style.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `blink(self)` {#style.blink}

Apply a blink style.

Note that this style may not be supported by all terminals.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `blink_rapid(self)` {#style.blink-rapid}

Apply a rapid blink style.

Note that this style may not be supported by all terminals.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `reverse(self)` {#style.reverse}

Apply a reverse style.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `hidden(self)` {#style.hidden}

Apply a hidden style.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `crossed(self)` {#style.crossed}

Apply a crossed style.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `reset(self)` {#style.reset}

Apply a reset style.

| In/Out | Type    |
| ------ | ------- |
| `self` | `Style` |
| Return | `self`  |

### `patch(self, another)` {#style.patch}

Patch the style with `another`.

| In/Out    | Type    |
| --------- | ------- |
| `self`    | `Style` |
| `another` | `Style` |
| Return    | `self`  |

### `__new()` {#style.\_\_new}

| In/Out | Type    |
| ------ | ------- |
| Return | `Style` |

## Span {#span}

`ui.Span` is the smallest unit of text, yet a component of `ui.Line`. Create a span:

```lua
ui.Span("foo")
```

For convenience, `ui.Span` can also accept itself as a argument:

```lua
ui.Span(ui.Span("bar"))
```

### `visible(self)` {#span.visible}

Whether the span is visible, i.e. includes any printable characters.

| In/Out | Type      |
| ------ | --------- |
| `self` | `Span`    |
| Return | `boolean` |

### `style(self, style)` {#span.style}

Set the style of the span.

| In/Out  | Type              |
| ------- | ----------------- |
| `self`  | `Span`            |
| `style` | [`Style`](#style) |
| Return  | `self`            |

Besides applying the whole `Style`, you can also call those methods of `Style` directly on it, which means:

```lua
local style = ui.Style():fg("white"):bg("black"):bold()
ui.Span("Hello world"):style(style)
```

can be also written as:

```lua
ui.Span("Hello world"):fg("white"):bg("black"):bold()
```

### `__new(value)` {#span.\_\_new}

| In/Out  | Type               |
| ------- | ------------------ |
| `value` | `string` \| `Span` |
| Return  | `Span`             |

## Line {#line}

`ui.Line` represents a line, consisting of multiple `ui.Span`s, and it accepts a table of them:

```lua
ui.Line { ui.Span("foo"), ui.Span("bar") }
```

For convenience, the following types are also supported:

```lua
-- string
ui.Line("foo")

-- ui.Span
ui.Line(ui.Span("bar"))

-- ui.Line itself
ui.Line(ui.Line("baz"))

-- Mixed table of string, ui.Span, ui.Line
ui.Line { "foo", ui.Span("bar"), ui.Line("baz") }
```

### `area(self, rect)` {#line.area}

Set the area of the line.

| In/Out | Type                      |
| ------ | ------------------------- |
| `self` | `Line`                    |
| `rect` | [`Rect?`](#rect)          |
| Return | `self` \| [`Rect`](#rect) |

If `rect` is not specified, it returns the current area.

### `width(self)` {#line.width}

Calculate the width of the line.

| In/Out | Type      |
| ------ | --------- |
| `self` | `Line`    |
| Return | `integer` |

### `align(self, align)` {#line.align}

Set the alignment of the line.

| In/Out  | Type    |
| ------- | ------- |
| `self`  | `Line`  |
| `align` | `Align` |
| Return  | `self`  |

The `align` accepts the following constants:

- `ui.Line.LEFT`
- `ui.Line.CENTER`
- `ui.Line.RIGHT`

### `visible(self)` {#line.visible}

Whether the line is visible, i.e. includes any printable characters.

| In/Out | Type      |
| ------ | --------- |
| `self` | `Line`    |
| Return | `boolean` |

### `style(self, style)` {#line.style}

Set the style of the line.

| In/Out  | Type              |
| ------- | ----------------- |
| `self`  | `Line`            |
| `style` | [`Style`](#style) |
| Return  | `self`            |

Like with [`Span`](#span), you can also call the [`Style`](#style) methods on it directly:

```lua
ui.Line("Hello world"):fg("white"):bg("black"):bold()
```

### `__new(value)` {#line.\_\_new}

| In/Out  | Type                                                     |
| ------- | -------------------------------------------------------- |
| `value` | `string` \| `Span` \| `Line` \| `(string\|Span\|Line)[]` |
| Return  | `Line`                                                   |

## Text {#text}

`ui.Text` is used to represent multi-line text, it takes a table of `ui.Line`:

```lua
ui.Text { ui.Line("foo"), ui.Line("bar") }
```

For convenience, the following types are also supported:

```lua
-- string
ui.Text("foo\nbar")

-- ui.Line
ui.Text(ui.Line("foo"))

-- ui.Span
ui.Text(ui.Span("bar"))

-- Mixed table of string, ui.Line, ui.Span
ui.Text { "foo", ui.Line("bar"), ui.Span("baz") }
```

You can also use `ui.Text.parse(code)` to parse an [ANSI escape sequence](https://en.wikipedia.org/wiki/ANSI_escape_code) string into a text.

### `area(self, rect)` {#text.area}

Set the area of the text.

| In/Out | Type                      |
| ------ | ------------------------- |
| `self` | `Text`                    |
| `rect` | [`Rect?`](#rect)          |
| Return | `self` \| [`Rect`](#rect) |

If `rect` is not specified, it returns the current area.

### `align(self, align)` {#text.align}

Set the alignment of the text.

| In/Out  | Type    |
| ------- | ------- |
| `self`  | `Text`  |
| `align` | `Align` |
| Return  | `self`  |

The `align` accepts the following constants:

- `ui.Text.LEFT`
- `ui.Text.CENTER`
- `ui.Text.RIGHT`

### `wrap(self, wrap)` {#text.wrap}

Set the wrap of the text.

| In/Out | Type   |
| ------ | ------ |
| `self` | `Text` |
| `wrap` | `Wrap` |
| Return | `self` |

The `wrap` accepts the following constants:

- `ui.Text.WRAP_NO` - No wrap
- `ui.Text.WRAP` - Wrap at the end of the line
- `ui.Text.WRAP_TRIM` - Wrap at the end of the line, and trim the leading whitespace

### `max_width(self)` {#text.max-width}

Calculate the maximum width of the text across all lines.

| In/Out | Type      |
| ------ | --------- |
| `self` | `Text`    |
| Return | `integer` |

### `style(self, style)` {#text.style}

Set the style of the text.

| In/Out  | Type              |
| ------- | ----------------- |
| `self`  | `Text`            |
| `style` | [`Style`](#style) |
| Return  | `self`            |

Like with [`Span`](#span), you can also call the [`Style`](#style) methods on it directly:

```lua
ui.Text("Hello world"):fg("white"):bg("black"):bold()
```

### `__new(value)` {#text.\_\_new}

| In/Out  | Type                                                     |
| ------- | -------------------------------------------------------- |
| `value` | `string` \| `Span` \| `Line` \| `(string\|Span\|Line)[]` |
| Return  | `Text`                                                   |

## Layout {#layout}

Create a layout:

```lua
local areas = ui.Layout()
	:direction(ui.Layout.HORIZONTAL)
	:constraints({ ui.Constraint.Percentage(50), ui.Constraint.Percentage(50) })
	:split(area)

local left = areas[1] -- The first rect
local right = areas[2] -- The second rect
```

### `direction(self, direction)` {#layout.direction}

Set the direction of the layout.

| In/Out      | Type        |
| ----------- | ----------- |
| `self`      | `Layout`    |
| `direction` | `Direction` |
| Return      | `self`      |

The `direction` accepts the following constants:

- `ui.Layout.HORIZONTAL`
- `ui.Layout.VERTICAL`

### `margin(self, margin)` {#layout.margin}

Set the margin of the layout.

| In/Out   | Type      | Note             |
| -------- | --------- | ---------------- |
| `self`   | `Layout`  | -                |
| `margin` | `integer` | Positive integer |
| Return   | `self`    | -                |

### `margin_h(self, margin)` {#layout.margin-h}

Set the horizontal margin of the layout.

| In/Out   | Type      | Note             |
| -------- | --------- | ---------------- |
| `self`   | `Layout`  | -                |
| `margin` | `integer` | Positive integer |
| Return   | `self`    | -                |

### `margin_v(self, margin)` {#layout.margin-v}

Set the vertical margin of the layout.

| In/Out   | Type      | Note             |
| -------- | --------- | ---------------- |
| `self`   | `Layout`  | -                |
| `margin` | `integer` | Positive integer |
| Return   | `self`    | -                |

### `constraints(self, constraints)` {#layout.constraints}

Set the constraints of the layout.

| In/Out        | Type                               |
| ------------- | ---------------------------------- |
| `self`        | `Layout`                           |
| `constraints` | [`table<Constraint>`](#constraint) |
| Return        | `self`                             |

### `split(self, rect)` {#layout.split}

Split the layout into multiple [Rect](#rect)s according to the constraints.

| In/Out | Type                   |
| ------ | ---------------------- |
| `self` | `Layout`               |
| `rect` | [`Rect`](#rect)        |
| Return | [`table<Rect>`](#rect) |

### `__new()` {#layout.\_\_new}

| In/Out | Type     |
| ------ | -------- |
| Return | `Layout` |

## Constraint {#constraint}

A constraint that defines the size of a layout element.

Constraints can be used to specify a fixed size, a percentage of the available space, a ratio of
the available space, a minimum or maximum size or a fill proportional value for a layout
element.

Relative constraints (percentage, ratio) are calculated relative to the entire space being
divided, rather than the space available after applying more fixed constraints (min, max,
length).

Constraints are prioritized in the following order:

1. `ui.Constraint.Min(min)`
2. `ui.Constraint.Max(max)`
3. `ui.Constraint.Length(len)`
4. `ui.Constraint.Percentage(p)`
5. `ui.Constraint.Ratio(num, den)`
6. `ui.Constraint.Fill(scale)`

### `Min(min)` {#constraint.Min}

Applies a minimum size constraint to the element.

| In/Out | Type         |
| ------ | ------------ |
| `min`  | `integer`    |
| Return | `Constraint` |

The element size is set to at least the specified amount.

```lua
-- { Percentage(100), Min(20) }
-- ┌────────────────────────────┐┌──────────────────┐
-- │            30 px           ││       20 px      │
-- └────────────────────────────┘└──────────────────┘

-- { Percentage(100), Min(10) }
-- ┌──────────────────────────────────────┐┌────────┐
-- │                 40 px                ││  10 px │
-- └──────────────────────────────────────┘└────────┘
```

### `Max(max)` {#constraint.Max}

Applies a maximum size constraint to the element.

| In/Out | Type         |
| ------ | ------------ |
| `max`  | `integer`    |
| Return | `Constraint` |

The element size is set to at most the specified amount.

```lua
-- { Percentage(0), Max(20) }
-- ┌────────────────────────────┐┌──────────────────┐
-- │            30 px           ││       20 px      │
-- └────────────────────────────┘└──────────────────┘

-- { Percentage(0), Max(10) }
-- ┌──────────────────────────────────────┐┌────────┐
-- │                 40 px                ││  10 px │
-- └──────────────────────────────────────┘└────────┘

```

### `Length(len)` {#constraint.Length}

Applies a length constraint to the element.

| In/Out | Type         |
| ------ | ------------ |
| `len`  | `integer`    |
| Return | `Constraint` |

The element size is set to the specified amount:

```lua
-- { Length(20), Length(20) }
-- ┌──────────────────┐┌──────────────────┐
-- │       20 px      ││       20 px      │
-- └──────────────────┘└──────────────────┘

-- { Length(20), Length(30) }
-- ┌──────────────────┐┌────────────────────────────┐
-- │       20 px      ││            30 px           │
-- └──────────────────┘└────────────────────────────┘
```

### `Percentage(p)` {#constraint.Percentage}

Applies a percentage of the available space to the element.

| In/Out | Type         |
| ------ | ------------ |
| `p`    | `integer`    |
| Return | `Constraint` |

Converts the given percentage to a floating-point value and multiplies that with area.
This value is rounded back to an integer as part of the layout split calculation.

```lua
-- { Percentage(75), Fill(1) }
-- ┌────────────────────────────────────┐┌──────────┐
-- │                38 px               ││   12 px  │
-- └────────────────────────────────────┘└──────────┘

-- { Percentage(50), Fill(1) }
-- ┌───────────────────────┐┌───────────────────────┐
-- │         25 px         ││         25 px         │
-- └───────────────────────┘└───────────────────────┘
```

### `Ratio(num, den)` {#constraint.Ratio}

Applies a ratio of the available space to the element.

| In/Out | Type         |
| ------ | ------------ |
| `num`  | `integer`    |
| `den`  | `integer`    |
| Return | `Constraint` |

Converts the given ratio to a floating-point value and multiplies that with area.
This value is rounded back to an integer as part of the layout split calculation.

```lua
-- { Ratio(1, 2), Ratio(1, 2) }
-- ┌───────────────────────┐┌───────────────────────┐
-- │         25 px         ││         25 px         │
-- └───────────────────────┘└───────────────────────┘

-- { Ratio(1, 4), Ratio(1, 4), Ratio(1, 4), Ratio(1, 4) }
-- ┌───────────┐┌──────────┐┌───────────┐┌──────────┐
-- │   13 px   ││   12 px  ││   13 px   ││   12 px  │
-- └───────────┘└──────────┘└───────────┘└──────────┘
```

### `Fill(scale)` {#constraint.Fill}

Applies the scaling factor proportional to all other `Fill` elements
to fill excess space.

| In/Out  | Type         |
| ------- | ------------ |
| `scale` | `integer`    |
| Return  | `Constraint` |

The element will only expand or fill into excess available space, proportionally matching
other `Fill` elements while satisfying all other constraints.

```lua
-- { Fill(1), Fill(2), Fill(3) }
-- ┌──────┐┌───────────────┐┌───────────────────────┐
-- │ 8 px ││     17 px     ││         25 px         │
-- └──────┘└───────────────┘└───────────────────────┘

-- { Fill(1), Percentage(50), Fill(1) }
-- ┌───────────┐┌───────────────────────┐┌──────────┐
-- │   13 px   ││         25 px         ││   12 px  │
-- └───────────┘└───────────────────────┘└──────────┘
```

See https://docs.rs/ratatui/latest/ratatui/layout/enum.Constraint.html for more information.

## List {#list}

Create a `List` that takes a table of `ui.Text`:

```lua
ui.List { ui.Text("foo"), ui.Text("bar") }
```

For convenience, the following types are also supported:

```lua
-- Table of string
ui.List { "foo", "bar" }

-- Table of ui.Line
ui.List { ui.Line("foo"), ui.Line("bar") }

-- Table of ui.Span
ui.List { ui.Span("foo"), ui.Span("bar") }

-- Mixed table of string, ui.Line, ui.Span
ui.List { "foo", ui.Line("bar"), ui.Span("baz") }
```

### `area(self, rect)` {#list.area}

Set the area of the list.

| In/Out | Type                      |
| ------ | ------------------------- |
| `self` | `List`                    |
| `rect` | [`Rect?`](#rect)          |
| Return | `self` \| [`Rect`](#rect) |

If `rect` is not specified, it returns the current area.

### `style(self, style)` {#list.style}

Set the style of the list.

| In/Out  | Type              |
| ------- | ----------------- |
| `self`  | `List`            |
| `style` | [`Style`](#style) |
| Return  | `self`            |

### `__new(value)` {#list.\_\_new}

| In/Out  | Type                                                                     |
| ------- | ------------------------------------------------------------------------ |
| `value` | `string` \| `Span` \| `Line` \| `Text` \| `(string\|Span\|Line\|Text)[]` |
| Return  | `List`                                                                   |

## Bar {#bar}

Create a bar:

```lua
ui.Bar(direction)
```

The first attribute denotes the direction of the bar and accepts the following constants:

- `ui.Bar.NONE`
- `ui.Bar.TOP`
- `ui.Bar.RIGHT`
- `ui.Bar.BOTTOM`
- `ui.Bar.LEFT`
- `ui.Bar.ALL`

### `area(self, rect)` {#bar.area}

Set the area of the bar.

| In/Out | Type                      |
| ------ | ------------------------- |
| `self` | `Bar`                     |
| `rect` | [`Rect?`](#rect)          |
| Return | `self` \| [`Rect`](#rect) |

If `rect` is not specified, it returns the current area.

### `symbol(self, symbol)` {#bar.symbol}

Set the symbol of the bar.

| In/Out | Type     |
| ------ | -------- |
| `self` | `string` |
| Return | `self`   |

### `style(self, style)` {#bar.style}

Set the style of the bar.

| In/Out  | Type              |
| ------- | ----------------- |
| `self`  | `Bar`             |
| `style` | [`Style`](#style) |
| Return  | `self`            |

### `__new(value)` {#bar.\_\_new}

| In/Out  | Type        |
| ------- | ----------- |
| `value` | `Direction` |
| Return  | `Bar`       |

## Border {#border}

Create a border:

```lua
ui.Border(position)
```

The first attribute denotes the position of the border and accepts the following constants:

- `ui.Border.NONE`
- `ui.Border.TOP`
- `ui.Border.RIGHT`
- `ui.Border.BOTTOM`
- `ui.Border.LEFT`
- `ui.Border.ALL`

### `area(self, rect)` {#border.area}

Set the area of the border.

| In/Out | Type                      |
| ------ | ------------------------- |
| `self` | `Border`                  |
| `rect` | [`Rect?`](#rect)          |
| Return | `self` \| [`Rect`](#rect) |

If `rect` is not specified, it returns the current area.

### `type(self, type)` {#border.type}

Set the type of the border.

| In/Out | Type      |
| ------ | --------- |
| `self` | `Border`  |
| `type` | `integer` |
| Return | `self`    |

The `type` accepts the following constants:

- `ui.Border.PLAIN`
- `ui.Border.ROUNDED`
- `ui.Border.DOUBLE`
- `ui.Border.THICK`
- `ui.Border.QUADRANT_INSIDE`
- `ui.Border.QUADRANT_OUTSIDE`

### `style(self, style)` {#border.style}

Set the style of the border.

| In/Out  | Type              |
| ------- | ----------------- |
| `self`  | `Border`          |
| `style` | [`Style`](#style) |
| Return  | `self`            |

### `__new(value)` {#border.\_\_new}

| In/Out  | Type       |
| ------- | ---------- |
| `value` | `Position` |
| Return  | `Border`   |

## Gauge {#gauge}

Create a gauge:

```lua
ui.Gauge()
```

### `area(self, rect)` {#gauge.area}

Set the area of the gauge.

| In/Out | Type                      |
| ------ | ------------------------- |
| `self` | `Gauge`                   |
| `rect` | [`Rect?`](#rect)          |
| Return | `self` \| [`Rect`](#rect) |

If `rect` is not specified, it returns the current area.

### `percent(self, percent)` {#gauge.percent}

Set the percentage of the gauge.

| In/Out    | Type      |
| --------- | --------- |
| `self`    | `Gauge`   |
| `percent` | `integer` |
| Return    | `self`    |

### `ratio(self, ratio)` {#gauge.ratio}

Set the ratio of the gauge.

| In/Out  | Type     | Note            |
| ------- | -------- | --------------- |
| `self`  | `Gauge`  | -               |
| `ratio` | `number` | Between 0 and 1 |
| Return  | `self`   | -               |

### `label(self, label)` {#gauge.label}

Set the label of the gauge.

| In/Out  | Type     |
| ------- | -------- |
| `self`  | `Gauge`  |
| `label` | `string` |
| Return  | `self`   |

### `style(self, style)` {#gauge.style}

Set the style of everything except the gauge itself.

| In/Out  | Type              |
| ------- | ----------------- |
| `self`  | `Gauge`           |
| `style` | [`Style`](#style) |
| Return  | `self`            |

### `gauge_style(self, style)` {#gauge.gauge-style}

Set the style of the gauge itself.

| In/Out  | Type              |
| ------- | ----------------- |
| `self`  | `Gauge`           |
| `style` | [`Style`](#style) |
| Return  | `self`            |

### `__new()` {#gauge.\_\_new}

| In/Out | Type    |
| ------ | ------- |
| Return | `Gauge` |

## Clear {#clear}

Clear the content of a specific area, which is a [Rect](#rect). Place it followed by the component that you want to clear:

```lua
local components = {
	ui.Text("..."):area(rect),
	-- ...

	ui.Clear(rect),
}
```

### `area(self, rect)` {#clear.area}

Set the area of the clear.

| In/Out | Type                      |
| ------ | ------------------------- |
| `self` | `Clear`                   |
| `rect` | [`Rect?`](#rect)          |
| Return | `self` \| [`Rect`](#rect) |

If `rect` is not specified, it returns the current area.

### `__new()` {#clear.\_\_new}

| In/Out | Type            |
| ------ | --------------- |
| `rect` | [`Rect`](#rect) |
| Return | `Clear`         |
