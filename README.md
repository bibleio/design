![Banner](https://github.com/user-attachments/assets/2572f6b0-9d8c-4e08-884d-0202980f7b9d)

Design version `1.5.0` - Library version `2.3.0`

UI kit for Bibleio, including React components and Tailwind configuration with color styles.

Built with Radix Primitives, other accessible React primitives, and Tailwind CSS.

Report issues or suggestions in this GitHub repo or in the [Discord](https://discord.gg/7eVCyQ5GGb).

# Documentation

See the [Figma file](https://www.figma.com/community/file/1398417551065522372/bibleio-design-kit) for design documentation.

Soon we plan to move docs over to [dev.bibleio.com/design/docs](https://dev.bibleio.com/design/docs).

# Installation

Install the module:

```bash
# pnpm
pnpm add @bibleio/design
# yarn
yarn add @bibleio/design
# npm
npm install @bibleio/design
```

Add Tailwind style preset:

```ts
// tailwind.config.ts
// Snippet of what to add
import { bibleioTheme } from '@bibleio/design'; // Add import

const config: Config = {
  presets: [bibleioTheme], // Add preset
};
```

Import main styles in your main layout:

```tsx
import '@bibleio/design/dist/index.css'; // Import styles
```

## Setup fonts

We use Lora for our main font.

Here are guides to setup fonts based on your framework.

### Next.js (plus JetBrains Mono)

Skip to the next section if you don't need JetBrains Mono.

Import Google fonts in `layout.tsx`:

```tsx
import { Lora, JetBrains_Mono } from 'next/font/google'; // Import fonts

const lora = Lora({ subsets: ['latin'], variable: '--font-lora' });

const jetBrainsMono = JetBrains_Mono({
  subsets: ['latin'],
  variable: '--font-jetbrains-mono',
});
```

Set css variables in your main body layout:

```html
<body className="{`${lora.variable}" ${jetBrainsMono.variable}`}></body>
```

In `tailwind.config.ts` override the default font theme to add variables:

```ts
import defaultTheme from 'tailwindcss/defaultTheme'; // Add default theme import

const config: Config = {
  presets: [bibleioTheme],
  theme: {
    fontFamily: {
      serif: ['var(--font-lora)', ...defaultTheme.fontFamily.serif],
      mono: ['var(--font-jetbrains-mono)', ...defaultTheme.fontFamily.mono],
    },
  },
};
```

### Next.js (just Lora)

Import Google fonts in `layout.tsx`:

```tsx
import { Lora } from 'next/font/google'; // Import fonts

const lora = Lora({ subsets: ['latin'] });
```

Set main font as Lora in your main layout (layout.tsx):

```html
<body className="{`${lora.classname}`}"></body>
```

### Astro / Any other framework that supports Fontsource

**Feel free to get rid of JetBrains Mono if you don't plan on using it.**

Install Fontsource fonts:

```bash
# pnpm
pnpm add @fontsource/lora @fontsource/jetbrains-mono
# yarn
yarn add @fontsource/lora @fontsource/jetbrains-mono
# npm
npm install @fontsource/lora @fontsource/jetbrains-mono
```

Import in your main layout (Astro as an example):

```astro
---
// Layout.astro
import "@fontsource/lora/*";
import "@fontsource/jetbrains-mono/*";
---
```

No extra Tailwind config is needed for Fontsource.

# Tailwind

The spacing system is literal, so `p-32` means exactly `32px`.

## Dark Mode Switcher

We do not provide a dark mode swticher, because this library could be used with any frame work that accepts React, and some of them could result in a FOUC. 

# Changelog

Look at the [releases](https://github.com/bibleio/design/releases).

# License

All of Bibleio's projects are licensed under the [MIT No Attribution](LICENSE.txt) license. You can copy, translate, modify, and distribute this resource, without restriction, and without needing to ask permission. Why? For the sake of the gospel (Matt 10:8).

Check out why you should do the same by clicking this:

[<img src="https://copy.church/badges/lcc_alt_pde.png" alt="Freely given, no conditions!" width="300"/>](https://copy.church/explain/importance/)
