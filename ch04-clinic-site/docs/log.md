# 制作ログ

第4章の実践パートで残す5つの版と、それぞれのプロンプトと結果を記録する。版ができるたびに追記する。

| 版 | 節 | 内容 | 状態 |
|---|---|---|---|
| v1-draft | 4-2 | ワイヤーフレームと構造記述から出した初稿 | 完了 |
| v2-loop1 | 4-3 | 1周目：hero（H1の折り返しをFigmaへ戻して直す） | 完了 |
| v3-loop2 | 4-3 | 2周目：services（アイコンの差し色をトーン定義に合わせる） | 完了 |
| v4-loop3 | 4-3 | 3周目：予約導線（reserve と header の電話・受付時間） | 完了 |
| v5-rules | 4-4 | ズレを振り分け、ルールに反映した版 | 未着手 |

## 4-2 初稿 v1-draft

### 渡した材料

| 層 | 材料 | 渡し方 |
|---|---|---|
| 構造 | `wireframe/01-header.png` 〜 `09-footer.png`（Figma `top-wireframe` をセクションごとに書き出した9枚） | `wireframe/` に置き、プロンプトでパスを指定 |
| 構造 | `docs/wireframe.md`（構造記述：優先順位、各セクションの内容） | ファイルを参照させる |
| 構造 | `docs/requirements.md`（目的、読者、成功条件） | ファイルを参照させる |
| ルール | `CLAUDE.md`（Figmaの変数を `get_variable_defs` で読み取り、CSSカスタムプロパティとして整理した制作ルール） | ディレクトリに置く（自動で読まれる） |

トーンの層（`docs/tone.md`、`moodboard/`）は初稿では渡していない。ルールの色と文字がトーンをどこまで再現するかを4-3で見るため。

セクション画像は Figma MCP の `download_assets` でセクションのフレームごとに書き出した（1280px幅、等倍）。変数は `get_variable_defs` をルールページに対して実行したが、返るのはそのページで使われている13個（色9、space/sm、space/md、radius/md、radius/pill）だけだった。未使用の5個は `use_figma` の `getLocalVariablesAsync` で取得し、18個の値を `CLAUDE.md` の表に写した。

### プロンプト（Claude Codeへ、ch04-clinic-site で新規セッション）

```
さくら台内科クリニックのトップページの初稿を index.html として作ってください。

材料
- 構造：wireframe/ にあるセクションごとの画像9枚（01-header.png 〜 09-footer.png）。Figmaのワイヤーフレームを上から順に切り出したものです。すべて見てください
- 構造の言葉：docs/wireframe.md。各セクションの内容と、冒頭の「優先順位と注記」を守ってください
- 目的と読者：docs/requirements.md
- 制作ルール：CLAUDE.md（色、余白、角丸、文字、コンポーネントの定義）

条件
- 静的HTML＋Tailwind CSS（CDN版）。JavaScriptは書かない
- PC幅 1280px だけ。レスポンシブの分岐は書かない
- 色は CLAUDE.md の9色だけ。CSSカスタムプロパティとして定義し、tailwind.config からそれを参照する
- 写真は同梱しないので、moodboard/photo_links.md のMサイズ画像URLを img で直接参照する
- 文言はワイヤーフレームの画像と docs/wireframe.md にあるものを使う。本文が2段落と指定されていて画像にない部分は、クリニックとして自然な内容を仮で書く
- 作るのは index.html 1ファイルだけ。docs や CLAUDE.md は変更しない
- 完了前に CLAUDE.md の「完了前の確認」を実行し、変更したファイルと判断に迷った点を報告する
```

### 結果（Claude Codeの報告から）

- 9セクションを構造記述の順に実装。`<style>` に `--color-*` 9色、`--space-*` 6段階、`--radius-*` 3段階を定義し、`tailwind.config` の `theme.colors`、`fontSize`（H1〜Captionの5段階）、`spacing`、`borderRadius` からその変数を参照した
- 色クラスの確認は bg、pale、primary、primary-light、white、line、ink、muted の範囲に収まった。mint は未使用（ワイヤーフレームに差し色の指定がないため）
- message の配置は `docs/wireframe.md`（左テキスト、右写真）と画像（左写真、右テキスト）が食い違っていたため、画像に合わせた
- muted（#6f8697）は白地で約3.8:1、bg 地で約3.6:1 と、要件の 4.5:1 を満たさない。本文段落は ink にし、muted は構造記述が明示する箇所（hero のリード文、日付、電話番号、©）だけに使った、との報告。primary 上の白文字も約4.2:1
- header の受付時間は、要件（ヘッダーと予約セクションの両方）ではなく構造記述（電話番号のみ）に従った
- reserve の縦余白 80px はトークンにないため `py-20`。白いボタンは寸法を primary と同じにして面 white、文字 primary にした
- ホバーは `hover:opacity-90`。住所、徒歩分数、services の説明文、message と doctor の本文、news の見出しは指定がないため仮の内容を作文した

### ブラウザ確認（screenshots/v1-draft/）

headless Chrome で 1280px 幅を撮影（`--window-size=1280,4727`、ページの実高さに合わせた）。

観測したズレ：

| 分類 | 内容 |
|---|---|
| 構造 | H1「いつもの暮らしに、あんしんを。」が左6カラムに収まらず「を。」だけ2行目に落ちる。Figma の `hero` フレームでも同じ位置で折り返しており（テキスト幅588、高さ120）、設計の段階から2行。原因はブラウザではなく設計側 |
| 構造 | message のH2「患者さんに寄り添う医療を、これからも」も「も」だけ2行目に落ちる。こちらも Figma で同じ（高さ84）。H1 と同じ種類の問題として記録し、3周には含めない |
| 構造 | message の写真とテキストの左右が構造記述と逆（画像に合わせた結果。構造記述の側を直す） |
| 構造 | header に受付時間がなく、要件の成功条件を満たしていない |
| トーン | 写真はトーン定義どおり明るく白と淡い青が多い。ただし hero と message の余白がFigmaより広く感じる |
| トーン | muted の文字が薄く、hero のリード文が読みにくい。コントラスト比 4.5:1 未満 |
| 情報密度 | 問題なし。services 5枚、news 4件、footer の診療時間表は構造記述どおり |

想定していた「Tailwind標準のグレーが混ざる」は起きなかった。色は `theme.colors` の上書きで構造的に防がれた。セクションの縦余白（96px、64px、80px）と角丸 14px、ボタンの pill もFigmaの値どおりだった。

## 4-3 1周目 v2-loop1（hero）

### 前提

4-2 で観測したズレのうち hero に閉じたもの1件を扱う。H1「いつもの暮らしに、あんしんを。」の折り返しは Figma の `hero` フレームでも同じ位置で起きている（テキスト幅588px、高さ120px＝2行）。ブラウザのズレではなく設計側の問題なので、行き先は「Figmaへ戻す」。Figma の H1 テキスト（2:20）を `use_figma` で「いつもの暮らしに、」の後で改行した2行に更新し、`wireframe/02-hero.png` を `download_assets` で書き出し直した（2026-09-21）。

header の受付時間、message の左右、muted のコントラストは hero の外なので、この周では触れない。

### プロンプト（Claude Codeへ、ch04-clinic-site で新規セッション）

```
hero セクション（index.html の <section aria-labelledby="hero-heading">）の見出しを直してください。
Figma の「hero」フレーム（wireframe/02-hero.png、更新済み）と比較して、次の1点を修正してください。
1. H1「いつもの暮らしに、あんしんを。」が、ブラウザでは左6カラム（幅588px）に収まらず、末尾の「を。」だけが2行目に落ちています。Figma 側でも1行には収まらないため、設計を読点の後で改行する2行に改めました。コードでも「いつもの暮らしに、」の直後に <br> を入れ、同じ位置で改行してください。

意図：読点の後で切ると意味のまとまりで2行になり、末尾の「を。」だけが孤立しません。

条件
- 変更するのは index.html の hero セクションだけ。他のセクション、<style>、tailwind.config には触れない
- 文字サイズや幅で収めようとしない。改行の位置だけを指示どおりにする
- 変更後、変更したファイルと差分の要点を報告する
```

### 結果

- 差分は `index.html` の1行だけ。H1 の「いつもの暮らしに、」の直後に `<br>` が入った。他のセクション、`<style>`、`tailwind.config` に変更なし
- ブラウザ確認（`screenshots/v2-loop1/index-1280.png`、1280×4727）：H1 が「いつもの暮らしに、」「あんしんを。」の2行になり、末尾の「を。」の孤立は解消。ページの高さは v1 と同じ4727px（Figma と同じく設計の段階から2行分の高さだったため）
- 判断：採用。ズレの層は構造。行き先は「Figmaへ戻す」で、Figma のテキストとコードの両方に同じ改行が入った状態
- この周で触れなかったもの：message の H2 の折り返し（同じ種類の問題だが別セクション。4-4 で扱う）、header の受付時間（3周目）、muted のコントラスト（4-4）

## 4-3 2周目 v3-loop2（services）

### 前提

初稿ではトーンの層（`docs/tone.md`）を渡していない。services のアイコンの丸は v1 で pale になったが、`tone.md` は mint を「差し色。アイコンの丸、Tag の一部」と定めており、mint はページ内で未使用のまま。Figma の `services` フレームは構造ページの灰色ワイヤーフレームで色を持たないため、この周の参照点はフレームではなく `tone.md`。構造記述（`docs/wireframe.md`）の「pale の面」は `tone.md` に合わせて mint に直した（2026-09-21）。

### プロンプト（Claude Codeへ、ch04-clinic-site で新規セッション）

```
services セクション（index.html の <section id="services">）のトーンを直してください。
Figma の「services」フレーム（wireframe/04-services.png）は色を持たないワイヤーフレームなので、色の参照点は docs/tone.md です。次の1点を修正してください。
1. 各カードのアイコンの丸（40px、rounded-pill）が、現状は pale（#EDF6FA）でカードの白い面に沈んでいます。docs/tone.md は mint（#79BEA7）を「差し色。アイコンの丸、Tag の一部。面積は小さく」と定義しています。丸の面を mint にしてください。

意図：診療案内はページで最初に色の変化が出る場所なので、差し色を小さく置いて5枚のカードの入口を目に留まりやすくします。差し色は丸の面だけに留め、カードの罫線、見出し、本文には使いません。

条件
- 変更するのは index.html の services セクションだけ。他のセクション、<style>、tailwind.config には触れない
- docs/tone.md は読んでよいが変更しない
- 変更後、変更したファイルと差分の要点を報告する
```

### 結果

- 差分は `index.html` の services 内5行だけ。アイコンの丸の `bg-pale` が `bg-mint` になった。他のセクション、`<style>`、`tailwind.config` に変更なし
- ブラウザ確認（`screenshots/v3-loop2/index-1280.png`、1280×4727）：白いカードの左上に mint の丸が5つ並び、bg 地の上で差し色として見える。面積は丸だけで、罫線や文字には広がっていない
- 判断：採用。ズレの層はトーン。行き先は「コードを直す」だが、原因は初稿にトーンの層を渡していなかったこと。`tone.md` の mint の用途は 4-4 で CLAUDE.md のルールに写す候補
- 見送ったもの：カード本文は Figma のワイヤーフレームでは薄い灰色（muted 相当）だが、コントラストのため v1 で ink にした判断を維持。意図的な不一致として 4-4 で扱う

## 4-3 3周目 v4-loop3（予約導線：header と reserve）

### 前提

要件の成功条件「電話番号と受付時間がヘッダーと予約セクションの両方にある」に対し、v1 の header には電話番号だけがある。初稿の時点で見つけていたが、hero と services の周では手を広げずに置いた。原因は Figma の `header` フレームと構造記述に受付時間がなかったこと（要件と設計の食い違い）。行き先は「Figmaへ戻す」で、Figma の `header-right` に受付時間の Caption を追加して `wireframe/01-header.png` を書き出し直し、構造記述も直した（2026-09-21）。reserve 側は Figma のノード URL を渡し、`get_design_context` で値を照合させる。

### プロンプト（Claude Codeへ、ch04-clinic-site で新規セッション）

```
予約の導線を整えるため、header と reserve セクション（index.html の <header> と <section id="reserve">）を直してください。

1. header：要件（docs/requirements.md）は「電話番号と受付時間がヘッダーと予約セクションの両方にある」ですが、現状の header には電話番号だけで受付時間がありません。Figma の「header」フレーム（wireframe/01-header.png、更新済み）に合わせ、電話番号の下に Caption「受付 9:00〜18:00（平日）」を右揃えで加えてください。2行とも Caption、muted。header の高さ 80px は変えません。
2. reserve：参照先ノードのURL https://www.figma.com/design/0fjzmyH6ipz6kg3ou3oFtU/?node-id=2-66
   上記のノードを Figma MCP の get_design_context で読み込み、上下の余白、電話番号の文字サイズ、右カラムの3行の並びが現状のコードと一致しているか確認してください。一致していればコードは変えず、確認した値を報告してください。違いがあれば直してください。

意図：初めての患者が電話とWEBのどちらでも予約できることを、ページの入口（header）と予約セクションの両方で同じ情報で示します。

条件
- 変更するのは index.html の header と reserve だけ。他のセクション、<style>、tailwind.config には触れない
- docs は読んでよいが変更しない
- 変更後、変更したファイル、差分の要点、Figma から確認した値を報告する
```

### 結果

- 差分は `index.html` の header 内だけ。電話番号を縦並びの `div`（右揃え）で包み、その下に Caption「受付 9:00〜18:00（平日）」を追加した。2行とも `text-caption text-muted`。reserve、他のセクション、`<style>`、`tailwind.config` に変更なし
- reserve は Figma の `reserve` フレーム（2:66）と照合し一致：上下余白 80px（コードは `py-20`）、電話番号 28px（`text-h2`）、右カラムは「お電話でのご予約」「03-1234-5678」「受付時間 9:00〜18:00（平日）」の3行。コードは変えていない
- ブラウザ確認（`screenshots/v4-loop3/index-1280.png`、1280×4727、高さは v1 から変わらず）：header 右端に電話番号と受付時間が2行で右揃えになり、WEB予約ボタンと並ぶ。header の高さ 80px は維持
- 判断：採用。ズレの層は構造（要件にある情報が設計に抜けていた）。行き先は「Figmaへ戻す」で、この周は Figma と構造記述を先に直してからコードに反映した。reserve のようにノードURLを渡して照合させると、ズレがないことも確認結果として残せる
- 残り：header の受付時間の表記「受付」と reserve の「受付時間」が揃っていない。用語の統一は 4-4 のルール化で扱う
