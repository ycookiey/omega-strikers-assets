# omega-strikers-assets

Omega Strikers 21 キャラのアイコン画像を、jsDelivr から配れる WebP に整えて置いた。CDN pin で参照するだけ。

素材は Odyssey Interactive の公式 [Game Asset Kit](https://drive.google.com/drive/folders/1XzdEqmnba4m-TrA0F67JlDkyiZdRX2hY) から。**Odyssey Interactive とは非関連の非公式ファン配布物**。詳細と削除依頼窓口は [LICENSE-IMAGES](./LICENSE-IMAGES)。

## 使い方

```html
<img
  src="https://cdn.jsdelivr.net/gh/ycookiey/omega-strikers-assets@v1.0.0/characters/juliette.webp"
  alt="Juliette"
  width="320"
  loading="lazy"
/>
```

キャラ全部を扱うなら [`manifest.json`](./manifest.json) を fetch:

```ts
const CDN = "https://cdn.jsdelivr.net/gh/ycookiey/omega-strikers-assets@v1.0.0"
const { characters } = await fetch(`${CDN}/manifest.json`).then((r) => r.json())
// characters: { id, displayName, displayNameJa, image }[]
```

### CDN pin

| pin | 用途 |
|---|---|
| `@v1.0.0` | 本番・再現性重視 |
| `@v1` | v1.x.x に追従、破壊的変更なし |
| `@main` | 動作確認・開発用 |

## License

- **画像**(`characters/*.webp`): © Odyssey Interactive、詳細は [LICENSE-IMAGES](./LICENSE-IMAGES)
- **コード / ドキュメント**: [MIT](./LICENSE)
