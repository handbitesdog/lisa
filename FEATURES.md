# lisa features

A single-file normalizer + utility class system.

## Normalizer

- `box-sizing: border-box` on all elements.
- Margin reset on headings, `p`, `figure`, `blockquote`, `dl`, `dd`.
- Headings inherit font size/weight until a `.text-*`/`.font-*` utility is applied.
- Lists (`ul`, `ol`) unstyled, no margin/padding.
- Media elements (`img`, `picture`, `video`, `canvas`, `svg`) are block-level and capped at `max-width: 100%`.
- Links use `--color-link`, fade to `--color-link-dark` on hover.
- Form controls inherit font/color; buttons are reset (no background/border/padding, `cursor: pointer`).
- `textarea` resizes vertically only.
- Tables collapse borders; `hr` uses `--color-border`.

## Theme

Override CSS custom properties on `:root` to theme the page:

- `--color-bg`, `--color-text`, `--color-link` (+ `--color-link-dark`, auto-derived).
- `--font-sans`, `--font-serif`, `--fade-speed`.
- Utilities: `.font-serif`, `.font-sans`, `.text-body`, `.text-link`, `.bg-body`.

## Layout

- `.container` — centered, `max-width: 1200px`, gains `--space-32` side padding below that width.
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
- Weight: `.font-normal`, `.font-medium`, `.font-semibold`, `.font-bold`.
- Line height: `.leading-tight`, `.leading-normal`, `.leading-loose`.
- Align: `.text-left`, `.text-center`, `.text-right`.
- Color: `.text-{black,dark-gray,white,light-gray,blue,green,red,yellow,purple,orange}`.

## Color

Palette: black, dark-gray, white, light-gray, blue, green, red, yellow, purple, orange.

- Background: `.bg-{color}` for all ten.
- Light/dark variants (auto-derived via `color-mix`) for blue, green, red, yellow, purple, orange: `.bg-{color}-light`, `.bg-{color}-dark`.

## Borders

- `.border`, `.border-2`, `.border-0`.
- Sides: `.border-t`, `.border-r`, `.border-b`, `.border-l`.
- Color: `.border-{black,dark-gray,blue,green,red,yellow,purple,orange}`.
- Radius: `.rounded-4`, `.rounded-8`, `.rounded-16`, `.rounded-full`.
