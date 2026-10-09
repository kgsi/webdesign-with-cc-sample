# さくら台内科クリニック（第4章）

『Claude CodeではじめるWebデザイン入門』第4章「FigmaとClaude Codeを組み合わせる」の実践パートで制作する、架空の内科・小児科クリニックのトップページです。Figmaのワイヤーフレームから初稿を出し、往復で直し、ズレをルールに反映するまでを1枚のページで追います。

## 構成

| パス | 内容 |
|---|---|
| `moodboard/clinic-moodboard.html` | 出発点のムードボード。ブラウザで開ける |
| `moodboard/photo_links.md` | ムードボードで参照している写真の出典一覧 |
| `docs/requirements.md` | 要件 |
| `docs/sitemap.md`、`docs/wireframe.md` | 情報設計と構造記述（Figmaの「構造」ページと対応） |
| `docs/tone.md` | トーン設計メモ（Figmaの「トーン」ページと対応） |
| `docs/rules.md` | 変数とコンポーネントの定義（Figmaの「ルール」ページと対応） |
| `docs/log.md` | 制作ログ（プロンプトと結果）。途中の版を作ったときのコミットも記載 |
| `wireframe/01-header.png`〜`09-footer.png` | Figmaのワイヤーフレームをセクションごとに書き出した9枚。初稿のプロンプトで構造として渡す |
| `index.html` | トップページ（4-4でルールを反映した最終版） |
| `screenshots/index-1280.png` | 最終版のスクリーンショット（1280px） |

## 開き方

静的HTMLとTailwind CSS（CDN版）だけで動きます。フォントとTailwindの読み込みにネットワーク接続が必要です。

```bash
cd ch04-clinic-site
python3 -m http.server 8000
# http://localhost:8000/index.html
```

## 写真について

`index.html` とムードボードの写真は [ぱくたそ](https://www.pakutaso.com/) の素材で、[利用規約](https://www.pakutaso.com/userpolicy.html) に従います。規約で再配布が認められているSサイズの画像を `images/` に同梱しています。使う前に `images/README.md` を読み、ぱくたその利用規約に同意してください。クレジットは同ファイル、素材の用途の一覧は `moodboard/photo_links.md` にあります。サイトに登場する医院名と人物名は架空で、人物写真はイメージです。

2026年9月の時点では、写真をぱくたその画像URLで直接参照していました。ぱくたその規約が直接リンクを禁じているため、2026年10月に同梱へ改めました。それより前のコミットには、直接参照の形が残っています。
