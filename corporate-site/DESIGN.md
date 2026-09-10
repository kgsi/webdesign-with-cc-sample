# NOVARC デザインシステム

第5章5-5の成果物。`index.html`（v2）で手作業で決めた内容をルールに昇格させた、人が読む仕様書。Claude Codeに読ませる制作ルールは `CLAUDE.md` にある。実装は `index.html` と `news.html` がこの仕様に従う。

## 1. ブランド

| 項目 | 内容 |
|---|---|
| 企業名 | NOVARC Inc.（架空） |
| コンセプトコピー | 信頼を、デザインする。 |
| サブコピー | 先進的なテクノロジーと確かな実績で、社会の課題を解決し、より良い未来をつくる。 |
| キーワード | 信頼、先進性、ミニマル、クール、知性、グローバル |
| ロゴ | 「NOVARC」のテキストワードマーク。20px、Bold、字間 0.2em |

## 2. 色

8色だけを使う。`tailwind.config` の `theme.colors` をこの8色で上書きしているため、定義外の色クラス（`gray-*`、`slate-400` など）は生成されない。

| トークン | HEX | 役割 |
|---|---|---|
| `navy-950` | #0B1320 | ヘッダー、フッター、ヒーローのオーバーレイ、ダーク面のカードの面 |
| `navy-900` | #111B27 | TECHNOLOGY帯、ライト面の見出しと本文、写真のオーバーレイ（カード） |
| `teal-900` | #1F3537 | INVESTOR RELATIONS帯 |
| `slate-700` | #334155 | ダーク面の罫線、ライト面のセカンダリボタンの枠 |
| `slate-500` | #64748B | ライト面（white）のCaption：日付、英語ラベル |
| `slate-200` | #E2E8F0 | ダーク面の本文、ライト面の罫線、BUSINESS帯の背景、ダーク面のセカンダリボタンの枠 |
| `white` | #FFFFFF | ダーク面の見出し、ライト面の背景、ライト面のカードの面 |
| `accent` | #2563EB | テキストリンク、カードの矢印、Tag、IRリンクの矢印 |

面の組み合わせ：

| 面 | 背景 | 見出し | 本文 | 罫線 |
|---|---|---|---|---|
| ダーク | navy-950 / navy-900 / teal-900 | white | slate-200 | slate-700 |
| ライト | white / slate-200 | navy-900 | navy-900 | slate-200 |

Captionの色は面で変える。white の上は `slate-500`（4.76:1）、slate-200 の上は `slate-700`、ダーク面の上は `slate-200/70`。`slate-500` をダーク面や slate-200 の上に置くとコントラスト比が 4.5:1 を下回る（5-6のチェックで判明）。

写真の上に文字を載せるときは `navy-950/60`（ヒーロー）または `navy-900/60`（カード画像の色調整）のオーバーレイを重ねる。

## 3. 文字

Noto Sans JP（Google Fonts、400 / 500 / 700）。

| 用途 | 1024px以上 | 1023px以下 | ウェイト | クラス |
|---|---|---|---|---|
| H1 | 40 / 56 | 32 / 44 | 700 | `text-[32px] leading-[44px] lg:text-[40px] lg:leading-[56px] font-bold` |
| H2 | 28 / 40 | 24 / 36 | 700 | `text-[24px] leading-[36px] lg:text-[28px] lg:leading-[40px] font-bold` |
| H3 | 20 / 32 | 同じ | 500 | `text-[20px] leading-[32px] font-medium` |
| Body | 16 / 28 | 同じ | 400 | body に設定済み |
| Small | 14 / 24 | 同じ | 400 | `text-[14px] leading-[24px]`（ナビ、フッターのリンク） |
| Caption | 12 / 20 | 同じ | 400 | `text-[12px] leading-[20px]` |

- 英語ラベル（セクション名）：Caption、`tracking-[0.2em] uppercase` ＋ 面に応じたCaptionの色（white の上 `text-slate-500`、slate-200 の上 `text-slate-700`、ダーク面 `text-slate-200/70`）。H2の直上に置き、H2は `mt-2`
- 本文の1行は最大 640px（`max-w-[640px]`）

## 4. レイアウト

| 項目 | 値 | クラス |
|---|---|---|
| コンテナ | 1280px | `mx-auto max-w-container` |
| 左右マージン | 80px（1023px以下は 24px） | `px-6 lg:px-20` |
| グリッド | 12カラム、ガター 24px | `grid grid-cols-12 gap-6` |
| セクション縦余白 | 96px（1023px以下は 64px） | `py-16 lg:py-24` |
| ヘッダー高さ | 72px | `h-[72px]` |
| レイアウト切替 | 1024px（`lg:`） | 768pxはモバイルレイアウト |

角丸は `rounded-sm`（2px）だけ。影は使わない。罫線は 1px。

## 5. コンポーネント

### プライマリボタン

高さ 48px（ヘッダー内は 40px）、`rounded-sm`、`font-medium`、`px-6`。

- ダーク面：`bg-white text-navy-950 hover:bg-slate-200`
- ライト面：`bg-navy-950 text-white hover:bg-navy-900`

### セカンダリボタン

高さ 48px、`rounded-sm`、`font-medium`、`px-6`、1pxの枠線。

- ダーク面：`border border-slate-200 text-white hover:bg-white/10`
- ライト面：`border border-slate-700 text-navy-900 hover:bg-slate-200`

### テキストリンク

`inline-flex items-center gap-2 text-accent hover:underline` ＋ 矢印アイコン。「一覧を見る」のように文末に矢印を置く。

### Tag

`rounded-sm border border-accent px-2 text-[12px] leading-[20px] text-accent`。種類はお知らせ、IR、サステナビリティ、テクノロジー。絞り込みで選択中を表すときは `bg-accent text-white` に反転する。

### カード

`flex flex-col` のリンク。上に 16:9 の画像（`aspect-video w-full object-cover`）、`p-6` の本文部に H3、Body、右下に矢印。矢印は `mt-auto pt-6 flex justify-end text-accent` で下端に固定する。

- ダーク面：`border border-slate-700 bg-navy-950`
- ライト面：`bg-white`（枠線なし）

### リストの行（NEWS、IRリンク）

`border-b` の罫線で区切る。NEWSの行は日付（Caption、slate-500）＋Tag＋タイトル（Body）。1024px以上は横並びで日付とTagの列幅 240px、1023px以下は2行に折る。

### ページネーション

新しい部品は作らず、テキストリンクの組み合わせで作る。`flex items-center justify-center gap-6` に数字を並べ、現在ページは `font-medium text-navy-900`（リンクにしない、`aria-current="page"`）、他のページと「次へ」はテキストリンク。「次へ」の末尾に矢印アイコン。

### アイコン

24pxのSVG、`fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"`。矢印は `M5 12h14M13 6l6 6-6 6`。SNSアイコンは 20px。

## 6. セクションの型

| 型 | 構成 | 使用箇所 |
|---|---|---|
| 見出し＋カード3枚 | 英語ラベル、H2、Body 1文、`mt-12` にカード3枚（`lg:col-span-4`） | TECHNOLOGY、BUSINESS |
| 写真＋テキスト | 写真 6カラム、テキスト 5カラム、間に 1カラム。`lg:items-center` | ABOUT US（写真左）、SUSTAINABILITY（写真右） |
| 見出し＋リスト | 左 5カラムに見出しとボタン、右 6カラムにリスト | INVESTOR RELATIONS |
| 下層ページの見出し | 英語ラベル、H1、`py-16 lg:py-24`、背景 navy-950 | news.html |

## 7. ページ

- `index.html`：ヘッダー → ヒーロー → NEWS → TECHNOLOGY → ABOUT US → BUSINESS → SUSTAINABILITY → INVESTOR RELATIONS → フッター
- `news.html`：ヘッダー → 下層ページの見出し → Tagの絞り込み → 記事リスト → ページネーション → フッター。ヘッダーとフッターは `index.html` と同じマークアップ

## 8. 写真

クールトーン、高コントラスト、余白を活かす。暖色が入る写真は navy-900/60 のオーバーレイで抑える。出典は `README.md`。
