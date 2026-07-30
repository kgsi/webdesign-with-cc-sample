# webdesign-with-cc-sample

書籍『Claude CodeではじめるWebデザイン入門』のサンプルファイルです。本文の演習・実践で使うフォルダを、章の登場順に収録しています。

## 内容

| フォルダ | 対応する節 | 内容 |
| --- | --- | --- |
| `profile-site/` | 2-2　基本的な制作サイクルを体験する | 導入演習で使う1枚もののプロフィールページ。`index.html` が演習の開始地点、`example-result/` が演習を終えた状態の一例 |
| `ec-site/` | 2-3　ミニ実践：シンプルなECサイトを作る | ミニ実践の完成形。トップ＋商品詳細の2ページ構成の静的サイトで、`CLAUDE.md`・`DESIGN.md`・ムードボードなど本文で扱うコンテキストファイルも含む |
| `skill-compare/` | 2-6　Skillsで繰り返しの作業を制作ルール化する | frontend-design Skillのあり・なしだけを変えて、同一プロンプトから生成した2つの出力の比較 |
| `lp-site/` | 第3章　Claude Codeでデザイン判断を磨く | 第3章でレビューの題材にする、架空の航空会社AURORA AIRWAYSのランディングページ。ブリーフ・ムードボード・写真素材と、Claude Codeが生成した初稿 |

各フォルダの詳しい使い方は、それぞれの `README.md` を参照してください。

## 使い方

gitに慣れている場合は、cloneで取得してください。

```bash
git clone https://github.com/kgsi/webdesign-with-cc-sample.git
```

慣れていない場合は、このページの「Code」ボタンから「Download ZIP」を選べば同じものが手に入ります。展開したフォルダは、書類フォルダなど自分が見つけやすい場所に置いてください。入手の手順は本書の2-1節で説明しています。

収録しているサイトはすべてビルド不要の静的HTMLです。`index.html` をブラウザで開くだけで表示できます。

## 注意

- AIの出力は同じ指示でも実行のたびに変わります。手元の結果が収録している例と違っていても問題ありません
- 演習でファイルが大きく壊れたときは、このリポジトリからコピーし直せば開始地点からやり直せます

## ライセンス

- このリポジトリのコードとドキュメントは [MIT License](./LICENSE) で提供します
- `ec-site/images/` と `lp-site/images/` の写真は [Unsplash](https://unsplash.com/) の素材で、[Unsplash License](https://unsplash.com/license) に従います。撮影者と出典の一覧は各フォルダの `README.md` に記載しています
- `skill-compare/with-skill/.claude/skills/frontend-design/` は [Anthropic公開のSkill](https://github.com/anthropics/skills) の実物で、Apache License 2.0 で提供されています（ライセンス全文を同フォルダに同梱）
