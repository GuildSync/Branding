# GuildSync Brand Guidelines & Visual Assets

Official brand resources, vector source files, and high-resolution raster assets for **[GuildSync](https://guildsync.me)**.

---

## 1. Brand Philosophy

**GuildSync** is a high-performance synchronization and community automation engine connecting Discord guilds, bots, and databases (Google Sheets, Excel, and external game APIs) in real time.

The visual identity is anchored by **opposing geometric vector arrows**, representing:

- **Bi-directional data synchronization** (instant push & pull / real-time sync).
- **High-throughput data flow** between Discord communities and external infrastructure.
- **Precision, modernism, and speed**.

---

## 2. Directory Structure & Asset Manifest

```text
branding/
├── README.md                                             # Brand usage rules, palette, clear space, and guidelines
├── LICENSE.md                                            # Trademark & proprietary asset license (All Rights Reserved)
│
├── vector/                                               # Vector master files (zero margins, pixel-perfect crop)
│   ├── guildsync-logo.svg                                # Primary lockup: Aquire Bold logotype + vector arrows connector
│   ├── guildsync-icon.svg                                # Standalone mark: vertical opposing arrows in 1:1 square canvas
│   └── guildsync-icon-tight.svg                          # Standalone mark: tight bounding box (317 × 328 px)
│
└── raster/                                               # High-resolution raster renders (Skia / resvg engine)
    ├── avatars/                                          # Discord circular avatar safe zone (~70% centered)
    │   ├── guildsync-avatar-black-512x512.png            # White mark on solid black (#000000)
    │   ├── guildsync-avatar-black-2048x2048.png          # White mark on solid black HQ
    │   ├── guildsync-avatar-transparent-512x512.png      # White mark on transparent background
    │   └── guildsync-avatar-transparent-2048x2048.png    # White mark on transparent background HQ
    │
    ├── icons/                                            # Edge-to-edge square mark (100% height, zero vertical padding)
    │   ├── guildsync-icon-black-512x512.png              # Mark touching boundaries on black square
    │   ├── guildsync-icon-black-2048x2048.png            # Mark touching boundaries on black square HQ
    │   ├── guildsync-icon-transparent-512x512.png        # Mark touching boundaries on transparent background
    │   └── guildsync-icon-transparent-2048x2048.png      # Mark touching boundaries on transparent background HQ
    │
    └── logos/                                            # Full horizontal logotype (edge-to-edge, ~3.78:1 ratio)
        ├── guildsync-logo-black-1024w.png                # White logo on black background (1024 × 271 px)
        ├── guildsync-logo-black-2048w.png                # White logo on black background HQ (2048 × 542 px)
        ├── guildsync-logo-transparent-1024w.png          # White logo on transparent background (1024 × 271 px)
        └── guildsync-logo-transparent-2048w.png          # White logo on transparent background HQ (2048 × 542 px)
```

---

## 3. Brand Architecture

### Standalone Mark / Icon (`vector/guildsync-icon.svg`)

- **Geometry:** Two vertical opposing arrows constructed from 45° beveled angles and strict vertical stems.
    - Left arrow points UP (events, upload, action, status).
    - Right arrow points DOWN (dispatch, download, reaction, persistence).
- **Proportions:** 317 × 328 units.
- **Canvas:** 328 × 328 square (`viewBox="0 0 328 328"`), touching top and bottom boundaries (0 vertical margin), horizontally centered.

### Horizontal Lockup / Logo (`vector/guildsync-logo.svg`)

- **Composition:** Combines **GUILD** (top-left), **SYNC** (bottom-right), and a 90° rotated interlocking arrow connector.
- **Proportions:** 695.4 × 184.2 units (~3.78:1 aspect ratio).
- **Format:** Tight crop, 0 margins around external bounding contours.

---

## 4. Typography

- **Primary Display Font:** **Aquire Bold**
- **Characteristics:** Futuristic, geometric sans-serif featuring distinctive diagonal stencil notches on `G`, `D`, and `C`.
- **Vector Implementation:** All letters in SVG assets are pre-converted to pure cubic/quadratic Bézier outlines extracted from the original OpenType font metrics. No font file dependencies are required to render the SVGs.

---

## 5. Color Palette

| Token | HEX | RGB | Purpose |
| :--- | :--- | :--- | :--- |
| **Pure Black** | `#000000` | `0, 0, 0` | Primary dark theme background, high contrast |
| **Pure White** | `#FFFFFF` | `255, 255, 255` | Primary mark, text, and vector iconography |
| **Discord Indigo** | `#5865F2` | `88, 101, 242` | Ecosystem accent, Discord UI integration |
| **Electric Indigo** | `#6366F1` | `99, 102, 241` | Modern UI highlights, glow effects, interactive states |
| **Sync Blue** | `#3B82F6` | `59, 130, 246` | Data sync indicator, API communication |

> **Note on SVG fill:**
> All master vector files use `fill="currentColor"`. When embedding in React/Next.js/Tailwind, change color via CSS (e.g., `text-white`, `text-indigo-400`, `text-emerald-400`).

---

## 6. Safe Zones & Clear Space

### Discord Avatars (`raster/avatars/`)

Discord and major social platforms mask avatars with a circle. To prevent corner clipping, the avatar renders use a **Safe Zone of ~70%**:

- Centered inside a 512×512 or 2048×2048 square.
- Max diagonal distance from center is `228 px` (< `256 px` radius on 512 canvas).
- Zero risk of clipped arrow tips when cropped to a circle.

### Edge-to-Edge Icons (`raster/icons/`)

- Height touches the top (`y = 0`) and bottom (`y = H - 1`) of the canvas.
- Ideal for favicons, video overlays, watermarks, and square badges.

### Banners & Headers (`raster/logos/`)

- Cropped directly to the outermost glyph boundaries.
- Ideal for GitHub README headers, documentation navbars, Discord server banners, and social preview cards.

---

## 7. Usage in Code

### React / Next.js

```tsx
import Image from 'next/image';

export function GuildSyncIcon({ className = "w-8 h-8" }: { className?: string }) {
  return (
    <Image
      src="/branding/vector/guildsync-icon.svg"
      alt="GuildSync Icon"
      width={32}
      height={32}
      className={className}
    />
  );
}
```

### Inline SVG (Dynamic Theming)

```html
<svg class="text-white hover:text-indigo-400 transition-colors" viewBox="0 0 328 328" width="48" height="48" fill="currentColor">
  <!-- Use vector/guildsync-icon.svg contents -->
</svg>
```

---

## 8. Brand Restrictions (Don'ts)

To preserve brand integrity:

- **Do not** stretch, skew, or distort the proportions of the mark or logotype.
- **Do not** round the sharp 45° beveled edges or corners of the arrows.
- **Do not** rearrange or alter the relative scale between the text and arrow connector.
- **Do not** apply heavy, low-quality drop shadows or thick outlines that blur the geometry.
- **Do not** rotate the mark to arbitrary angles (only vertical 0° and horizontal 90° lockups are permitted).

---

## 9. Licensing & Official Contact

All brand names, logotypes, iconography, vector sources, and raster renders in this directory are the exclusive proprietary intellectual property of **GuildSync** (All Rights Reserved) and are governed by the terms in [`LICENSE.md`](./LICENSE.md).

- **Official Website:** [https://guildsync.me](https://guildsync.me)
- **Business, Press & Licensing Inquiries:** [business@guildsync.me](mailto:business@guildsync.me)
