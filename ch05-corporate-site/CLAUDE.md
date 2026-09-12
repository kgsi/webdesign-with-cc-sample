# NOVARC コーポレートサイト 制作ルール

このディレクトリのHTMLを作成・変更するときは、先に `DESIGN.md` を読み、そこにある値とコンポーネントだけを使うこと。

## 技術

- 静的HTML＋Tailwind CSS（CDN版）。JavaScriptは書かない（`tailwind.config` の記述だけ例外）
- `tailwind.config` は `index.html` の `<head>` にあるものをそのままコピーする。色は8色の上書き定義、`maxWidth.container` は 1280px
- Noto Sans JP を Google Fonts で読み込む（`index.html` と同じ `<link>`）
- 新しいページを作るときは、ヘッダーとフッターを `index.html` からそのままコピーする。ナビの現在ページには `text-white` を付ける

## 色

- `DESIGN.md` の8色だけを使う。`gray-*`、`zinc-*`、`neutral-*`、定義外の `slate-*` は使わない
- ダーク面の本文は `text-slate-200`、ライト面の本文は `text-navy-900`。Caption の色は面で変える（white の上 `text-slate-500`、slate-200 の上 `text-slate-700`、ダーク面 `text-slate-200/70`）。`text-slate-500` はライト面の Caption 以外に使わない
- `accent` はテキストリンク、矢印、Tag に限る。ボタンの塗りや背景に使わない

## 文字と余白

- 文字サイズは `DESIGN.md` の6段階だけ。それ以外の `text-[..px]` を書かない
- セクションは `py-16 lg:py-24`、コンテナは `mx-auto max-w-container px-6 lg:px-20`
- レイアウトの切替は `lg:` だけを使う。`md:` や `sm:` を使わない

## コンポーネント

- ボタン、テキストリンク、Tag、カード、リストの行は `DESIGN.md` 5章のクラスをそのまま使う。新しい見た目のボタンやカードを作らない
- カードの矢印は `mt-auto pt-6` で下端に固定する
- アイコンは 24px のライン SVG（`stroke-width="1.5"`）。絵文字やアイコンフォントを使わない
- 角丸は `rounded-sm` だけ。影（`shadow-*`）を使わない

## 完了前の確認

- `<head>` に `og:title`、`og:description`、`og:image`、`<link rel="icon">` があるか（`index.html` からコピー）
- 使っている色クラスが8色に収まっているか（`grep -oE 'bg-\w+|text-\w+|border-\w+'` で確認）
- 375px、768px、1280px で横スクロールが出ないか
- 画像に `alt` があるか（装飾画像は `alt=""`）
- 変更したファイルと判断した点を報告する
