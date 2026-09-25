# omega-strikers-assets

Odyssey Interactive の公式 [Game Asset Kit](https://drive.google.com/drive/folders/1XzdEqmnba4m-TrA0F67JlDkyiZdRX2hY) をもとに、Omega Strikers のキャラクター close-up ポートレートを **WebP に変換 + kebab-case でリネーム**して並べた、ファンコミュニティ向けの静的アセットセット。

## 使い方

### 直接参照(CDN 配信)

[jsDelivr](https://www.jsdelivr.com/) の GitHub 配信を使うと、CDN 経由でキャッシュされた画像がそのまま参照できる:

```
https://cdn.jsdelivr.net/gh/ycookiey/omega-strikers-assets@main/characters/juliette.webp
```

タグ・commit SHA でピンも可能:

```
https://cdn.jsdelivr.net/gh/ycookiey/omega-strikers-assets@<sha>/characters/juliette.webp
```

### プログラムから参照

`manifest.json` に全キャラクターの一覧が入っている:

```json
{
  "characters": [
    { "id": "juliette", "displayName": "Juliette", "displayNameJa": "ジュリエット", "image": "characters/juliette.webp" }
  ]
}
```

## 収録キャラクター(21)

Ai.Mi / Asher / Atlas / Drek'ar / Dubu / Era / Estelle / Finii / Juliette / Juno / Kai / Kazan / Luna / Mako / Nao / Octavia / Rasmus / Rune / Vyce / X / Zentaro

## 帰属と権利

Omega Strikers およびキャラクターアートワークは Odyssey Interactive の著作物。本リポジトリの画像は、Odyssey Interactive が公式に配布している [Game Asset Kit](https://drive.google.com/drive/folders/1XzdEqmnba4m-TrA0F67JlDkyiZdRX2hY) の "Character Art - Transparent Backgrounds" に含まれる素材を、WebP に変換してキャラ ID を kebab-case に揃えた上で再配置したもの。

- 画像の著作権は Odyssey Interactive に帰属する
- 本リポジトリは非商用のファンコミュニティ用途を前提とする
- 配布元 Asset Kit の指定条件があれば、そちらが優先される
