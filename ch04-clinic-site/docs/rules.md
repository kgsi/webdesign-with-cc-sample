# ルールページの定義

4-4の成果物の元。Figmaの「ルール」ページに置く変数とコンポーネントの一覧。`get_variable_defs` で読み取れる形と、`DESIGN.md` へ書き写す形の両方の起点になる。

## 変数コレクション `clinic`

### 色（COLOR）

| 変数名 | 値 | スコープ |
|---|---|---|
| color/primary | #2F7FD0 | 面、文字 |
| color/primary-light | #8FC8F2 | 面 |
| color/mint | #79BEA7 | 面 |
| color/pale | #EDF6FA | 面 |
| color/bg | #F7FBFD | 面 |
| color/line | #DBE8EF | 線 |
| color/white | #FFFFFF | 面、文字 |
| color/ink | #18364D | 文字 |
| color/muted | #6F8697 | 文字 |

### 余白（FLOAT）

| 変数名 | 値 |
|---|---|
| space/xs | 8 |
| space/sm | 16 |
| space/md | 24 |
| space/lg | 40 |
| space/xl | 64 |
| space/section | 96 |

### 角丸（FLOAT）

| 変数名 | 値 |
|---|---|
| radius/sm | 12 |
| radius/md | 14 |
| radius/pill | 999 |

## テキストスタイル

`docs/tone.md` の5段階（H1、H2、H3、Body、Caption）をそのまま登録する。

## コンポーネント

### Button

- バリアント `variant=primary`：面 color/primary、文字 color/white
- バリアント `variant=secondary`：面 color/white、枠 color/primary 1px、文字 color/primary
- 高さ 48px、左右パディング 28px、角丸 radius/pill、文字は Body 500

### Card

- 面 color/white、枠 color/line 1px、角丸 radius/md、パディング space/md
- 上からアイコンの丸（40px、color/pale）、H3、Body。縦の間隔は space/sm

### Tag

- 面 color/pale、文字 Caption、色 color/ink、左右パディング 12px、高さ 24px、角丸 radius/pill
