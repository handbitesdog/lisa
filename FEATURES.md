# lisa features

A single-file normalizer + utility class system.

## Normalizer

- `box-sizing: border-box` on all elements.
- Margin reset on headings, `p`, `figure`, `blockquote`, `dl`, `dd`.
- Headings inherit font size/weight until a `.text-*`/`.font-*` utility is applied, but default to `--leading-tight` line-height.
- Lists (`ul`, `ol`) unstyled, no margin/padding.
- Media elements (`img`, `picture`, `video`, `canvas`, `svg`) are block-level, capped at
  `max-width: 100%`, with `height: auto` to preserve aspect ratio.
- Links use `--color-link`, fade to `--color-link-dark` on hover.
- Form controls inherit font/color; buttons are reset (no background/border/padding, `cursor: pointer`).
- Text inputs and `textarea` have native appearance/border-radius removed (checkbox and radio
  are left native since they'd otherwise lose their indicator, but get `accent-color:
  var(--color-blue)` so their checked state matches the theme instead of browser default blue).
- `textarea` resizes vertically only.
- Tables collapse borders; `hr` uses `--color-border`.

## Theme

Override CSS custom properties on `:root` to theme the page:

- `--color-bg`, `--color-text`, `--color-link` (+ `--color-link-dark`, auto-derived).
- `--font-sans`, `--font-serif`, `--fade-speed`.
- Utilities: `.font-serif`, `.font-sans`, `.text-body`, `.text-link`, `.bg-body`.

## Layout

- `.container` — centered, `max-width: 840px`, with `--space-32` side padding.
- `.wide-container` — centered, `max-width: 1200px`, with `--space-32` side padding.
- Display: `.block`, `.inline-block`, `.inline`, `.flex`, `.inline-flex`, `.grid`, `.inline-grid`, `.hidden`.
- Flex: `.flex-row`, `.flex-col`, `.flex-wrap`, `.flex-nowrap`, `.flex-1`, `.flex-auto`, `.flex-none`, `.grow`, `.shrink-0`.
- Grid: `.grid-cols-{1,2,3,4,6}`, `.col-span-full`.
- Alignment: `.items-{start,center,end,stretch}`, `.justify-{start,center,end,between,around}`.

## Spacing

Scale: `8, 16, 32, 40, 80` (px), exposed as `--space-*`.

- Padding: `.p-*`, `.pt-*`, `.pr-*`, `.pb-*`, `.pl-*`, `.px-*`, `.py-*`.
- Margin: `.m-*`, `.mt-*`, `.mr-*`, `.mb-*`, `.ml-*`, `.mx-*`, `.my-*`, plus `.mx-auto`.
- Gap: `.gap-*`, `.gap-x-*`, `.gap-y-*`.

All support `0` and the five scale values (e.g. `.p-0` … `.p-80`).

## Typography

- Size: `.text-xs` … `.text-3xl` (12–48px).
- Weight: `.text-normal`, `.text-medium`, `.text-semibold`, `.text-bold`.
- Line height: `.leading-tight`, `.leading-normal`, `.leading-loose`.
- Align: `.text-left`, `.text-center`, `.text-right`.
- Color: `.text-{black,dark-gray,gray,light-gray,white,dark-blue,blue,light-blue,pale-blue,dark-green,green,light-green,pale-green,dark-red,red,light-red,pale-red,dark-yellow,yellow,light-yellow,pale-yellow,dark-purple,purple,light-purple,pale-purple,dark-orange,orange,light-orange,pale-orange,dark-brown,brown,light-brown,cream}`.

## Color

Palette: black, dark-gray, gray, light-gray, white, dark-blue, blue, light-blue, pale-blue,
dark-green, green, light-green, pale-green, dark-red, red, light-red, pale-red, dark-yellow,
yellow, light-yellow, pale-yellow, dark-purple, purple, light-purple, pale-purple, dark-orange,
orange, light-orange, pale-orange, dark-brown, brown, light-brown, cream — flat values, no
auto-derived light/dark variants (each shade, where present, is its own named color).

- Background: `.bg-{color}` for all thirty-three.

## Borders

- `.border`, `.border-2`, `.border-0`.
- Sides: `.border-t`, `.border-r`, `.border-b`, `.border-l`.
- Color: `.border-{black,dark-gray,gray,light-gray,white,dark-blue,blue,light-blue,pale-blue,dark-green,green,light-green,pale-green,dark-red,red,light-red,pale-red,dark-yellow,yellow,light-yellow,pale-yellow,dark-purple,purple,light-purple,pale-purple,dark-orange,orange,light-orange,pale-orange,dark-brown,brown,light-brown,cream}`.
- Radius: `.rounded-4`, `.rounded-8`, `.rounded-16`, `.rounded-full`.

## Position

- `.relative`, `.absolute`, `.fixed`.

## Interactivity

- `.pointer-events-none`.
- Cursor: `.cursor-{auto,default,pointer,text,move,grab,grabbing,wait,help,not-allowed,crosshair,zoom-in,zoom-out,none}`.

## Components

- `.btn` — `--space-8`/`--space-16` padding, `--radius-8` corners, 1px light-gray border.
  Declared before the utility sections so `.bg-*`/`.border-*`/`.p-*` etc. can still override it
  by source order.
- `.btn-filled` — the fill lives on a `::before` layer (inherits `background-color` and
  `border-radius` from the button) that sits above the button's own background but below its
  text, and covers the border strip too so the border reads as the same color as the fill
  instead of light-gray. On hover, only that layer gets `filter: brightness(0.92)`, so the fill
  darkens without dragging the text down with it. Compose like `.btn .btn-filled .bg-blue`.
- `.btn-unfilled` — on hover, `filter: brightness(0.92)` applies to the whole button, darkening
  border and text together since both are drawn directly on it. Compose like
  `.btn .btn-unfilled .border-blue`.
- `.btn-disabled` — `cursor: not-allowed` and `pointer-events: none` (which also keeps
  `:hover` from ever matching, so it's inert on both filled and unfilled buttons), plus a
  light-gray border and dark-gray text regardless of composed color. Background is
  variant-specific: `.btn-filled.btn-disabled` gets a light-gray fill, `.btn-unfilled.btn-disabled`
  stays white. Declared after the utility sections — the opposite placement from `.btn` — so
  it overrides whatever color is composed in.
- `.input` — same `--space-8`/`--space-16` padding, `--radius-8` corners, and 1px light-gray
  border as `.btn`, for text-like inputs and `textarea`. Declared alongside `.btn` (before the
  utility sections) so it can be overridden the same way. `background-color: inherit` so it
  takes on whatever background the parent has instead of a fixed color. On `textarea`, the
  resize-handle glyph is replaced with a Lucide `chevrons-up-down` icon via
  `::-webkit-resizer` (WebKit/Blink only — Chrome, Safari, Edge; Firefox has no equivalent
  hook and keeps its native grip), sized up to `--space-16` with the icon at `10px` so it
  doesn't sit flush in the corner.
- `.select` — same padding/border/radius as `.input`, and also inherits its background. Unlike
  `.input`, the native arrow is dropped (`appearance: none`) in favor of a Lucide
  `chevron-down` icon inlined as a data-URI background-image (`stroke` is a literal
  `--color-dark-gray` value, not `currentColor`, since a background-image SVG doesn't inherit
  the host element's CSS `color`) — the native arrow's spacing isn't consistently controllable
  across browsers via padding, but the custom one is drawn with a guaranteed 16px gap
  (`background-position: right var(--space-16) center`) on both sides via
  `padding-right: calc(var(--space-40) + var(--space-8))`.
- Focus: `.btn:focus-visible`, `.input:focus-visible`, `.select:focus-visible` get a 2px blue
  outline with a 2px offset. A work in progress; more input styling is planned.
