# さくら台内科クリニック サイト 制作ルール

このディレクトリのHTMLを作成・変更するときは、先にこのファイルと `docs/requirements.md` を読むこと。ここにある値だけを使う。

## 技術

- 静的HTML＋Tailwind CSS（CDN版）。JavaScriptは書かない（`tailwind.config` の記述だけ例外）
- Noto Sans JP を Google Fonts で読み込む
- PC幅（1280px）だけを対象にする。レスポンシブの分岐（`sm:` `md:` `lg:`）は書かない
- 写真は同梱しない。写真の位置には `moodboard/photo_links.md` のMサイズ画像URLを `<img>` で直接参照する。地図は OpenStreetMap の `export/embed.html` を `<iframe>` で埋め込む

## デザイントークン

Figmaファイル「book-ch04 さくら台内科クリニック」のルールページにある変数を、`get_variable_defs` と `use_figma` で読み取った値（2026-09-21。`get_variable_defs` はページで使われている13個だけを返すため、残り5個は `use_figma` で取得。2026-09-21 に color/muted を #6f8697 から #5c7384 へ変更）。`<style>` のCSSカスタムプロパティとして定義し、`tailwind.config` の `theme.colors` などからその変数を参照する。値を直接クラスに書かない（`text-[#18364d]` のような書き方をしない）。

### 色（Figma `color/*` → CSS `--color-*`）

| Figma変数 | CSS変数 | 値 | 用途 |
|---|---|---|---|
| color/primary | --color-primary | #2f7fd0 | ボタンの面、リンク、ホバー |
| color/primary-light | --color-primary-light | #8fc8f2 | グラデーションの終点 |
| color/mint | --color-mint | #79bea7 | 差し色。Card のアイコンの丸だけに使う |
| color/pale | --color-pale | #edf6fa | プレースホルダーの面、Tag、フッター |
| color/bg | --color-bg | #f7fbfd | セクションの背景 |
| color/line | --color-line | #dbe8ef | 罫線、カードの枠 |
| color/white | --color-white | #ffffff | 面、ダーク面の文字 |
| color/ink | --color-ink | #18364d | 見出しと本文 |
| color/muted | --color-muted | #5c7384 | 補足の文字（白地で 4.9:1、bg 地で 4.7:1） |

この9色だけを使う。Tailwind標準の `gray-*` `slate-*` `blue-*` などは使わない。

### 余白（Figma `space/*` → CSS `--space-*`）

| Figma変数 | CSS変数 | 値 |
|---|---|---|
| space/xs | --space-xs | 8px |
| space/sm | --space-sm | 16px |
| space/md | --space-md | 24px |
| space/lg | --space-lg | 40px |
| space/xl | --space-xl | 64px |
| space/section | --space-section | 96px |

### 角丸（Figma `radius/*` → CSS `--radius-*`）

| Figma変数 | CSS変数 | 値 |
|---|---|---|
| radius/sm | --radius-sm | 12px |
| radius/md | --radius-md | 14px |
| radius/pill | --radius-pill | 999px |

### テキストスタイル（Noto Sans JP）

| 名前 | サイズ / 行送り | 太さ |
|---|---|---|
| H1 | 40px / 60px | 700 |
| H2 | 28px / 42px | 700 |
| H3 | 20px / 32px | 500 |
| Body | 16px / 30px | 400 |
| Caption | 13px / 20px | 400 |

この5段階だけを使う。

## コンポーネント

- Button primary：面 primary、文字 white。高さ 48px、左右パディング 28px、角丸 pill、文字は Body の太さ 500
- Button secondary：面 white、枠 primary 1px、文字 primary。寸法は primary と同じ
- Card：面 white、枠 line 1px、角丸 md、パディング md。上からアイコンの丸（40px、mint）、H3、Body（ink）。縦の間隔は sm
- Tag：面 pale、文字 Caption の ink、左右パディング 12px、高さ 24px、角丸 pill
- 影（`shadow-*`）を使わない。アイコンは 24px のライン SVG か、色面だけで表す。絵文字を使わない

## レイアウト

- コンテナは幅 1200px を中央寄せ（`mx-auto max-w-[1200px]`）
- グリッドは12カラム、ガター 24px
- セクションの縦余白は `docs/wireframe.md` の指定に従う（96px が基本）

## 用語

- 診療時間の案内は「受付時間 9:00〜18:00（平日）」と書く。「受付」だけに略さない

## Figma と意図的に違えている点

Figma のワイヤーフレームやトークンと一致しないが、理由があってコード側を正とする点。Figma には戻さない。

- reserve の縦余白は 80px（`py-20`）。トークン（space/*）にない値だが、使うのはこの1箇所だけなので変数を増やさない
- Card の本文はワイヤーフレームでは薄い灰色だが、コードでは ink。本文サイズの文字に muted を使わない

## 完了前の確認

- 使っている色クラスが9色に収まっているか（`grep -oE '(bg|text|border|from|to)-[a-z-]+' index.html | sort -u` で確認）
- 1280px で横スクロールが出ないか
- 画像のプレースホルダーに `aria-hidden="true"` か `alt=""` があるか
- 変更したファイルと、判断に迷った点を報告する
