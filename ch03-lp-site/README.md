# NAGARE ランディングページ（第3章）

第3章「Claude Codeでデザイン判断を磨く」でレビューの題材にする、架空の業務プラットフォームSaaS「NAGARE」のランディングページです。

## 構成

| ファイル | 内容 |
| --- | --- |
| `BRIEF.md` | 生成時にClaude Codeへ渡すブリーフ（目的・ターゲット・トーン・構成・素材・制約） |
| `moodboard/nagare-moodboard.png` | デザインの方向性を示すムードボード |
| `images/` | LPで使うイラスト素材9点 |
| `index.html`・`css/style.css` | 上記のブリーフと素材からClaude Codeが生成した初稿。3-1節の演習の開始地点 |
| `example-result/` | 3-2節から3-5節の修正指示を順に適用した完成例 |
| `example-result/CLAUDE.md` | 3-6節で、2回以上書いた判断を書き出した制作ルール |

`index.html` は、Claude Codeが一発生成した初稿に、3-1節で読者が追加で頼む「キービジュアルのイラストをもう少し大きく表示して」の変更（`.hero-image` の幅指定）だけを加えた状態です。それ以外は生成結果のまま手を加えていません。第3章では、この状態とムードボードを見比べながら違和感を言語化し、修正指示で改善していきます。演習でファイルが大きく壊れたときは、このフォルダからコピーし直せば開始地点からやり直せます。

`example-result/CLAUDE.md` は、Claude Codeを `example-result/` で起動したときに最初から読み込まれます。`ch03-lp-site/` で起動したときは、Claude Codeが `example-result/` の中のファイルを開くまで読み込まれません。

## 開き方

`index.html` をブラウザで開くだけで表示できます。フォントはGoogle Fontsから読み込むため、初回表示時のみネット接続が必要です。

## 画像・アイコンのクレジット

`images/` のイラストと `moodboard/` のムードボードは、著者がAI画像生成で作成したものです。

`example-result/index.html` のフッターにあるSNSアイコンと、ヘッダーのメニュー開閉ボタンのアイコンは、[Bootstrap Icons](https://icons.getbootstrap.com/) v1.13.1（MIT License）のSVGを埋め込んでいます。
