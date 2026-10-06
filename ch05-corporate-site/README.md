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
| `screenshots/` | 最終版のスクリーンショット（`index.html` と `news.html`、375、768、1280） |

## 開き方

静的HTMLとTailwind CSS（CDN版）だけで動きます。フォントとTailwindの読み込みにネットワーク接続が必要です。

```bash
cd ch05-corporate-site
python3 -m http.server 8000
# http://localhost:8000/index.html
```

## 収録している版

ルートの `index.html` と `news.html` は、5-5 のデザインシステムを適用し、5-6 の公開前チェックの修正を反映した最終版です。5-4 の初稿と改善版は収録していません。各版で何を変えたかは `docs/log.md` に記録しています。

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
