# 制作ログ

第4章の実践パートで残す5つの版と、それぞれのプロンプトと結果を記録する。版ができるたびに追記する。

| 版 | 節 | 内容 | 状態 |
|---|---|---|---|
| v1-draft | 4-2 | ワイヤーフレームと構造記述から出した初稿 | 完了 |
| v2-loop1 | 4-3 | 1周目：hero（H1の折り返しをFigmaへ戻して直す） | 未着手 |
| v3-loop2 | 4-3 | 2周目：services（アイコンの差し色をトーン定義に合わせる） | 未着手 |
| v4-loop3 | 4-3 | 3周目：予約導線（reserve と header の電話・受付時間） | 未着手 |
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
