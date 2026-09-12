# 公開前チェック

5-6の成果物。Claude Codeに実行させた自動チェックと、著者が目視で確認した項目を分けて記録する。対象は v3（`corporate-site/v3-final`）。

## チェック項目と結果

| # | 項目 | 方法 | 結果 |
|---|---|---|---|
| 1 | レスポンシブ（375、768、1280で横スクロールなし） | headless Chromeのスクリーンショット（`screenshots/v3-final/`）＋ ブラウザで `scrollWidth` を確認 | ○ 両ページとも3幅で `scrollWidth == clientWidth`（375: 360、768: 753、1280: 1265。差分15pxはスクロールバー）。スクリーンショットでも溢れなし |
| 2 | リンク切れ | `grep` で `href` を列挙し、`#`、`#id`、`news.html`、`index.html`、外部URL以外が無いこと | ○ `href` は `#`（48件、リンク先未作成のナビ・SNS・ボタン）、`#about` 等のページ内アンカー、`news.html`、`index.html`、`index.html#〜`、Google Fonts の3種だけ。アンカー先の `id` は全て存在 |
| 3 | 画像の alt | `grep '<img'` で全 `img` に `alt` があること。装飾画像は `alt=""` | ○ `img` は index.html に8個、すべて `alt` あり。news.html に `img` なし。ヒーローは `background-image` で `alt` の対象外 |
| 4 | コントラスト比 | 使っている文字色と背景色の組み合わせを計算（WCAG AA：本文 4.5:1、大きな文字 3:1） | △→修正 white on navy-950 18.6、slate-200 on navy-950 15.1、navy-900 on white 17.4、accent on white 5.2、slate-500 on white 4.8 は AA 合格。**slate-500 on navy-950 3.9、on navy-900 3.7、on teal-900 2.7、on slate-200 3.9 は 12px 文字で AA 未満**。ダーク面の Caption を `slate-200/70`（navy-950 で 7.8、navy-900 で 7.4、teal-900 で 6.0）、BUSINESS帯（slate-200）のラベルを `slate-700`（8.4）に変更し、DESIGN.md と CLAUDE.md に面別のルールを追記。accent on navy-950 3.6 はアイコン（`aria-hidden`）だけなので 3:1 の基準で合格 |
| 5 | フォント読み込み | Google Fonts の `<link>` が両ページにあり、`font-sans` が Noto Sans JP を指すこと | ○ 両ページに Google Fonts の `preconnect` と `<link>`、`fontFamily.sans` が Noto Sans JP。ネットワーク遮断時は sans-serif にフォールバック |
| 6 | OGP | `og:title`、`og:description`、`og:image` | ×→追加 未実装だった。`og:type`、`og:site_name`、`og:title`、`og:description`、`og:image`、`twitter:card` を両ページに追加。`og:image` は相対パス `images/hero.jpg` のままなので、公開時は絶対URLに置き換える必要がある（著者確認） |
| 7 | favicon | `<link rel="icon">` | ×→追加 未実装だった。navy-950 の角丸四角に白の N を描いた SVG を data URI で `<link rel="icon">` に追加。両ページ |
| 8 | 素材の出典 | `images/` の全ファイルが `README.md` のクレジット表にあること | ○ `images/` の7ファイルすべてが `README.md` のクレジット表にあり、HTMLからの参照も7ファイルで一致 |
| 9 | 色の逸脱 | `grep -oE '(bg|text|border)-[a-z]+-?[0-9]*'` で8色以外が無いこと | ○ 色クラスは navy-950/900、teal-900、slate-700/500/200、white、accent と、その不透明度違い（navy-950/60、navy-900/60、white/10、slate-200/70）だけ。`md:`、`sm:`、`shadow` は0件 |

## 自動チェックと目視の境界

- 自動で判定できたもの：2、3、5、6、7、8、9 と、1 の `scrollWidth`、4 の比率計算
- 目視が要るもの：1 の「溢れていないが読めるか」（375pxのH1の折返し、リスト行の2段組）、4 の「基準は満たすが読みにくくないか」（`slate-200/70` のラベルはダーク面で薄い）、6 の OGP 画像の見え方（SNSのプレビューは実機で確認）
- チェックで見つけた修正はすべて `corporate-site/v3-final` に含めた

実施：2026-09-11、Claude Code（Fable 5.1）。目視の確認は著者が行う。
