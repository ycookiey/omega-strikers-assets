# omega-strikers-assets

Omega Strikers の 21 キャラの close-up ポートレートを、jsDelivr から配れる WebP に整えて置いた mirror。CDN pin で参照するだけ。

素材は Odyssey Interactive の公式 [Game Asset Kit](https://drive.google.com/drive/folders/1XzdEqmnba4m-TrA0F67JlDkyiZdRX2hY) の "Character Art - Transparent Backgrounds"。手を入れたのは WebP 変換と kebab-case への rename のみ。

> 本リポジトリは **Odyssey Interactive とは非関連の非公式ファン配布物** です。詳しくは [LICENSE-IMAGES](./LICENSE-IMAGES) を参照。

## 使い方

### CDN 経由(推奨)

[jsDelivr](https://www.jsdelivr.com/) の GitHub 配信を使うと、CDN 経由でキャッシュされた画像がそのまま参照できる。**安定運用ではリリース tag に pin する**のを推奨:

```html
<img
  src="https://cdn.jsdelivr.net/gh/ycookiey/omega-strikers-assets@v1.0.0/characters/juliette.webp"
  alt="Juliette"
  width="320"
  loading="lazy"
/>
```

TypeScript / JavaScript から manifest を fetch して 21 キャラ全部を扱う:

```ts
type Character = {
  id: string
  displayName: string
  displayNameJa: string
  image: string
}
type Manifest = { version: number; characters: Character[] }

const CDN = "https://cdn.jsdelivr.net/gh/ycookiey/omega-strikers-assets@v1.0.0"

const manifest: Manifest = await fetch(`${CDN}/manifest.json`).then((r) =>
  r.json()
)

for (const c of manifest.characters) {
  console.log(c.displayNameJa, `${CDN}/${c.image}`)
}
```

### CDN pin の粒度

| pin | 挙動 | 想定用途 |
|---|---|---|
| `@main` | 最新 main 追従。破壊的変更に晒される | preview / dev only |
| `@v1` | v1.x.x の最新 minor に追従、breaking なし | 追加自動反映を望む consumer |
| `@v1.0.0` | 完全固定 | production・再現性重視 |

## 収録キャラクター(21)

Ai.Mi / Asher / Atlas / Drek'ar / Dubu / Era / Estelle / Finii / Juliette / Juno / Kai / Kazan / Luna / Mako / Nao / Octavia / Rasmus / Rune / Vyce / X / Zentaro

全キャラの ID・英語名・日本語名・image path は [`manifest.json`](./manifest.json) を参照。

## リポジトリ構成

```
omega-strikers-assets/
├── LICENSE           # code / documentation の MIT
├── LICENSE-IMAGES    # 画像素材の帰属と非関連 disclaimer
├── README.md
├── manifest.json     # id / displayName / displayNameJa / image path 一覧
├── .gitattributes
└── characters/
    ├── ai-mi.webp
    ├── asher.webp
    ├── ...           # 全 21 ファイル
```

## 帰属と権利

**画像素材** (`characters/*.webp`): 著作権は Odyssey Interactive。本リポジトリは公式 [Game Asset Kit](https://drive.google.com/drive/folders/1XzdEqmnba4m-TrA0F67JlDkyiZdRX2hY) の "Character Art - Transparent Backgrounds" を WebP + kebab-case に整えた mirror。削除依頼窓口は [LICENSE-IMAGES](./LICENSE-IMAGES)。

**コード / ドキュメント**(`manifest.json` / `README.md` / `.gitattributes` 等): [MIT License](./LICENSE)。

**非関連宣言**: 本リポジトリは Odyssey Interactive とは非関連の非公式ファン配布物であり、非商用ファンコミュニティ用途 (大会運営 tool、fan wiki 等) を前提とする。

## 更新方針

- **新キャラ追加**: minor bump (`v1.x.0`)
- **既存 file の差し替え・rename / 削除**: major bump (`vX.0.0`)
- **旧 tag は残す**(rewrite しない)
- 公式 Asset Kit 側で差し替えがあれば追従する
- 安定 pin は `@v1.0.0` を推奨、`@main` は preview 用途に限る
