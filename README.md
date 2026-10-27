# omega-strikers-assets

Portraits of 21 Omega Strikers™ characters as WebP files, for non-commercial fan sites and community tools that load them from the jsDelivr CDN. The images are converted to WebP from the official [Game Asset Kit](https://drive.google.com/drive/folders/1XzdEqmnba4m-TrA0F67JlDkyiZdRX2hY) distributed by Odyssey Interactive. This is an unofficial fan project, not affiliated with or endorsed by Odyssey Interactive.

## Usage

Each image is at `characters/<id>.webp`. [`manifest.json`](manifest.json) lists the `id`, English name, Japanese name, and image path of every character. The images are 256×256, except `kazan.webp` (100×100).

```html
<img
  src="https://cdn.jsdelivr.net/gh/ycookiey/omega-strikers-assets@v1.0.1/characters/juliette.webp"
  alt="Juliette"
  width="256"
  height="256"
  loading="lazy"
/>
```

```ts
const CDN = "https://cdn.jsdelivr.net/gh/ycookiey/omega-strikers-assets@v1.0.1"
const { characters } = await fetch(`${CDN}/manifest.json`).then((r) => r.json())
// characters: { id, displayName, displayNameJa, image }[]
const urls = characters.map((c) => `${CDN}/${c.image}`)
```

The part after `@` selects the version:

| Version | Serves |
|---|---|
| `@v1.0.1` | The files of that release. Use it in production |
| `@v1` | The latest `v1.x.x` release. A new release can take up to 7 days to appear |
| `@main` | The `main` branch. A new commit can take up to 12 hours to appear. Use it only for testing |

## License

- Images (`characters/*.webp`): © Odyssey Interactive. See [LICENSE-IMAGES](LICENSE-IMAGES), which also explains how to request removal
- Everything else: [MIT](LICENSE)
