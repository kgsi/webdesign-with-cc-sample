# NOVARC コーポレートサイト（第5章）

『Claude CodeではじめるWebデザイン入門』第5章「実践：制作ルールを持ったWebサイトをつくる」で制作する架空のテック系コーポレートサイトです。

## 構成

| パス | 内容 |
|---|---|
| `index.html` | トップページ（9セクション） |
| `news.html` | ニュース一覧（5-5で追加） |
| `docs/requirements.md` | 5-1 要件 |
| `docs/sitemap.md`、`docs/wireframe.md` | 5-2 情報設計と構造記述 |
| `docs/tone.md` | 5-3 トーン設計メモ |
| `docs/log.md` | 制作ログ（プロンプトと結果） |
| `docs/checklist.md` | 5-6 公開前チェック |
| `DESIGN.md`、`CLAUDE.md` | 5-5 デザインシステムと制作ルール |
| `moodboard.png` | 出発点のムードボード |
| `images/` | 写真素材 |
| `screenshots/<版名>/` | 各版のスクリーンショット（375、768、1280） |
| `versions/v1-draft/`、`versions/v2-improved/` | 5-4 の初稿と改善版の `index.html`（画像は親の `images/` を参照） |

## 開き方

静的HTMLとTailwind CSS（CDN版）だけで動きます。フォントとTailwindの読み込みにネットワーク接続が必要です。

```bash
cd ch05-corporate-site
python3 -m http.server 8000
# http://localhost:8000/index.html
```

## 版

| 場所 | 内容 |
|---|---|
| `versions/v1-draft/index.html` | 5-4 初稿 |
| `versions/v2-improved/index.html` | 5-4 改善版 |
| ルートの `index.html`、`news.html` | 5-5 デザインシステム適用後（news.html 追加）＋ 5-6 チェックの修正（最終版） |

差分を見るには `diff versions/v1-draft/index.html versions/v2-improved/index.html` のように比較してください。

## 画像クレジット

写真は [Unsplash](https://unsplash.com/) の素材を使用しています（Unsplash License：商用利用可、帰属表示は任意）。

<!-- IMAGE_CREDITS -->
| ファイル | 撮影者 | 出典 |
|---|---|---|
| `images/hero.jpg` | Sean Pollock | https://unsplash.com/photos/PhYq704ffdA |
| `images/technology.jpg` | Alexandre Debiève | https://unsplash.com/photos/FO7JIlwjOtU |
| `images/about.jpg` | Nastuh Abootalebi | https://unsplash.com/photos/yWwob8kwOCk |
| `images/business-datacenter.jpg` | Taylor Vick | https://unsplash.com/photos/M5tzZtFCOfs |
| `images/business-network.jpg` | NASA | https://unsplash.com/photos/Q1p7bh3SHj8 |
| `images/business-energy.jpg` | Martin Pruskavec | https://unsplash.com/photos/LIK6u_HzQs4 |
| `images/sustainability.jpg` | Alessio Soggetti | https://unsplash.com/photos/KQXeabDx7dI |
