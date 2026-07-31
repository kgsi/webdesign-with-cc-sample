# lp-site — AURORA AIRWAYSランディングページ（第3章）

第3章「Claude Codeでデザイン判断を磨く」でレビューの題材にする、架空の航空会社AURORA AIRWAYSのランディングページです。

## 構成

| ファイル | 内容 |
| --- | --- |
| `BRIEF.md` | 生成時にClaude Codeへ渡したブリーフ（目的・ターゲット・トーン・構成・素材・制約） |
| `moodboard/aurora-airways-moodboard.jpg` | デザインの方向性を示すムードボード |
| `images/` | LPで使う写真素材 |
| `index.html`・`css/style.css` | 上記のブリーフと素材からClaude Codeが生成した初稿 |
| `example-result/` | 第3章の修正指示を順に適用していく完成例（執筆の進行に合わせて更新。現在3-5節まで適用済み） |

`index.html` は生成後に手を加えていない初稿のままです。第3章では、この初稿とムードボードを見比べながら違和感を言語化し、修正指示で改善していきます。演習でファイルが大きく壊れたときは、このフォルダからコピーし直せば初稿からやり直せます。

## 開き方

`index.html` をブラウザで開くだけで表示できます。フォントはGoogle Fontsから読み込むため、初回表示時のみネット接続が必要です。

## 画像クレジット

`images/` の写真は [Unsplash](https://unsplash.com/) のフリー素材を使用しています（Unsplash License：商用利用可・改変可・帰属表示は任意）。

| ファイル | 撮影者 | 出典（Unsplash） |
| --- | --- | --- |
| `hero.jpg` | Ross Parmly | [photo](https://unsplash.com/photos/rf6ywHVkrlY) |
| `dest-paris.jpg` | Chris Karidis | [photo](https://unsplash.com/photos/nnzkZNYWHaU) |
| `dest-newyork.jpg` | Michael Discenza | [photo](https://unsplash.com/photos/5omwAMDxmkU) |
| `dest-maldives.jpg` | Mike Swigunski | [photo](https://unsplash.com/photos/k9Zeq6EH_bk) |
| `dest-singapore.jpg` | Mike Enerio | [photo](https://unsplash.com/photos/7ryPpZK1qV8) |
| `offer-europe.jpg` | Vatroslav Bank | [photo](https://unsplash.com/photos/QgjNdZH0hTI) |
| `offer-beach.jpg` | Ittemaldiviano 🇲🇻 | [photo](https://unsplash.com/photos/jmkMl20jNS0) |
| `offer-club.jpg` | Leonardo Yip | [photo](https://unsplash.com/photos/rn-NLirHQPY) |
| `hero-day.jpg` | Jametlene Reskp | [photo](https://unsplash.com/photos/cKmNURplLWE) |
| `dest-newyork-day.jpg` | Massimiliano Morosinotto | [photo](https://unsplash.com/photos/_ZEk8iXVWyI) |
| `dest-singapore-day.jpg` | Hanna Lazar | [photo](https://unsplash.com/photos/72FN9uljLwA) |

`*-day.jpg` の3枚は、3-3節でトーンを揃えるために差し替える昼の写真です。初稿（`index.html`）は差し替え前の写真のまま残しています。

`moodboard/aurora-airways-moodboard.jpg` は著者が作成したもので、AI画像生成による画像を含みます。

## アイコンクレジット

`example-result/index.html` のアイコン6種（armchair・utensils-crossed・headset・shield-check・menu・x）は [Lucide](https://lucide.dev/) を使用しています（ISC License：商用利用可・改変可）。サービス紹介の4種は3-4節、ハンバーガーメニューの2種は3-5節の修正指示で追加したものです。
