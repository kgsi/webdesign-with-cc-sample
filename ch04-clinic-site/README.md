# さくら台内科クリニック（第4章）

『Claude CodeではじめるWebデザイン入門』第4章「Figmaと連携する」の実践パートで制作する、架空の内科・小児科クリニックのトップページです。Figmaのワイヤーフレームから初稿を出し、往復で直し、ズレをルールに反映するまでを1枚のページで追います。

## 構成

| パス | 内容 |
|---|---|
| `moodboard/clinic-moodboard.html` | 出発点のムードボード。ブラウザで開ける |
| `moodboard/photo_links.md` | ムードボードで参照している写真の出典一覧 |
| `docs/requirements.md` | 要件 |
| `docs/sitemap.md`、`docs/wireframe.md` | 情報設計と構造記述（Figmaの「構造」ページと対応） |
| `docs/tone.md` | トーン設計メモ（Figmaの「トーン」ページと対応） |
| `docs/rules.md` | 変数とコンポーネントの定義（Figmaの「ルール」ページと対応） |
| `docs/log.md` | 制作ログ（プロンプトと結果） |
| `index.html` | トップページ（4-2以降で追加） |
| `versions/` | 各版の `index.html`（4-2以降で追加） |
| `screenshots/` | 各版のスクリーンショット（4-2以降で追加） |

## 開き方

静的HTMLとTailwind CSS（CDN版）だけで動きます。フォントとTailwindの読み込みにネットワーク接続が必要です。

```bash
cd ch04-clinic-site
python3 -m http.server 8000
# http://localhost:8000/index.html
```

## 写真について

ムードボードの写真は [ぱくたそ](https://www.pakutaso.com/) の素材で、[利用規約](https://www.pakutaso.com/userpolicy.html) に従います。CC0ではないため、画像ファイルはこのリポジトリに同梱していません。素材ページと撮影者の一覧は `moodboard/photo_links.md` にあります。手元で試すときは、各素材ページから取得して `images/` に置いてください。
