# LOSS IS MORE FUKUOKA — Website Prototype

福岡市東区香椎にオープンする LOSS IS MORE 旗艦店のサイトプロトタイプです。LP寄りの構造に、AIO / SEO / MEO 対策を組み込んだ単一ファイルのSPA（ハッシュルーティング）として実装しています。

このリポジトリは、本番実装フェーズ（WordPress化 or microCMS化）に進む前の **動作確認・関係者共有用のプロトタイプ** です。

---

## 店舗概要

- **店名**: LOSS IS MORE FUKUOKA
- **業態**: クラフト蒸留酒のショップ＆バー（試飲・物販・軽食）
- **所在地**: 福岡県福岡市東区香椎4丁目13-18
- **オープン**: 2026年（時期確定中）
- **運営**: 株式会社 LOSS IS MORE

---

## ファイル構成

```
.
├── README.md                       … このファイル
├── index.html                      … メインプロトタイプ（5ページSPA、単一ファイル）
├── llms.txt                        … AI検索向けインデックス
├── llms-full.txt                   … AI検索向けフルテキスト
└── docs/
    └── GBP_setup_checklist.docx    … Google Business Profile 設定チェックリスト
```

---

## プロトタイプの内容

`index.html` は単一HTMLファイル内に5つのページをハッシュルーティングで実装しています。

| ハッシュURL | ページ |
|---|---|
| `#/` | TOP（ファーストビュー〜ABOUT〜MENU〜NEWS〜ACCESS〜FAQ〜Links） |
| `#/news/` | NEWS一覧（タグフィルター付き） |
| `#/news/{slug}` | NEWS詳細記事 |
| `#/menu/` | MENU一覧 |
| `#/menu/{slug}` | MENU詳細 |

### 仕込んでいるもの

- **JSON-LD構造化データ**: Restaurant / FAQPage / NewsArticle / MenuItem / BreadcrumbList
- **OGP / canonical** メタタグ一式
- **llms.txt 連携**: head内に `<link rel="alternate" type="text/markdown">` で参照
- **SPAルーティング**: ブラウザの戻る・進む対応
- **ヒーロースライドショー**: 4枚自動送り（Ken Burns効果付き）
- **アクセシビリティ**: aria属性、prefers-reduced-motion対応
- **3層revealフォールバック**: JS無効でもCSSアニメで表示

### 仮置きしているもの

実装時に差し替える必要があります：

- **店舗の写真**（ヒーロースライド、ABOUT、各メニュー、各記事）→ いまはグラデーションで仮置き
- **オープン日**（`2026.MM.DD` 表記）
- **電話番号**（`092-XXX-XXXX`）
- **最寄駅からの徒歩分数**

---

## ローカルで動作確認する

特別な環境構築は不要です。`index.html` をブラウザで直接開くだけで動きます。

```bash
# ダブルクリックで開く、または
open index.html
```

ローカルサーバーで動かす場合：

```bash
# Python3
python3 -m http.server 8000

# Node.js (npxが使える場合)
npx serve .
```

その後 `http://localhost:8000/` にアクセス。

---

## GitHub Pages でホスティングする

このリポジトリはそのまま GitHub Pages にデプロイできます。

1. リポジトリの `Settings` → `Pages` を開く
2. `Source` を `Deploy from a branch` に
3. `Branch` で `main` / `(root)` を選択
4. `Save`

数分後に `https://[ユーザー名].github.io/[リポジトリ名]/` でアクセス可能になります。

---

## SEO / AIO / MEO 対策の方針

### SEO（Google検索）
- 構造化データ（JSON-LD）で店舗情報をマシンリーダブルに
- canonical URL の設定で重複コンテンツ対策
- セマンティックHTML（`<header>`, `<main>`, `<article>`, `<nav>` 等）

### AIO（AI検索：ChatGPT / Claude / Perplexity / Google AI Overview）
- `llms.txt` および `llms-full.txt` の設置
- FAQ を「質問H2 → 1〜2文の明快な回答」構造で記述
- E-E-A-T を意識した素材ストーリーの記事化（NEWSのStory記事）

### MEO（Google マップ）
- Google Business Profile 設定チェックリストを `docs/GBP_setup_checklist.docx` に用意
- サイト内 NAP（Name / Address / Phone）を完全統一
- LocalBusiness / Restaurant スキーマで店舗情報を構造化

詳細は `docs/GBP_setup_checklist.docx` を参照。

---

## 本番化に向けたロードマップ

### Phase 1（オープン3ヶ月前）
- [ ] 店舗情報の確定（オープン日、電話番号、最寄駅徒歩分数）
- [ ] GBP（Google Business Profile）の登録・オーナー確認
- [ ] 店舗・商品・素材の本撮影

### Phase 2（オープン1〜2ヶ月前）
- [ ] WordPress または microCMS への実装
- [ ] 各ページに撮影写真を反映
- [ ] llms.txt / llms-full.txt をルートに配置
- [ ] サーチコンソール登録、サイトマップ送信
- [ ] GBP の写真・メニュー登録

### Phase 3（オープン後 継続運用）
- [ ] NEWS の継続更新（週1〜月2目安、店舗スタッフ運用）
- [ ] 店内QRから口コミ導線の定着
- [ ] GBP インサイトの月次モニタリング

---

## ブランドファミリー

- [LOSS IS MORE 公式サイト](https://lossismore.jp/)
- [LOSS IS MORE Online Shop](https://shop.lossismore.jp/)
- [Instagram](https://www.instagram.com/loss_is_more/)

---

## ライセンス・著作権

© 2026 LOSS IS MORE Co., Ltd. All Rights Reserved.

このリポジトリのコードおよびコンテンツは、LOSS IS MORE FUKUOKA 店舗ウェブサイトの開発目的にのみ使用されます。第三者による無断複製・転用を禁じます。
