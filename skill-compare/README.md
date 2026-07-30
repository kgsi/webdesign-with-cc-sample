# Skillあり・なし比較デモ

Anthropic公式の frontend-design Skill の有無だけを変えて、同一プロンプトからコーポレートサイトを生成した比較デモです。プロンプト・モデル・その他の条件はすべて同じで、違いは Skill が有効かどうかだけです。

## ファイル構成

```
skill-compare/
├── prompt.md          # 両方で使った共通プロンプト
├── without-skill/
│   └── index.html     # Skillなしで生成した結果
├── with-skill/
│   ├── index.html     # frontend-design Skillありで生成した結果
│   └── .claude/
│       └── skills/
│           └── frontend-design/   # Skillの実物（SKILL.md + LICENSE.txt）
├── screenshots/       # 両者のキャプチャ（PC／モバイル）
└── README.md          # このファイル
```

## 再現手順

生成結果は実行のたびに変わります。ここに置いた2つの出力は 2026-07-29 に生成した一例です。

**Skillなし**

1. Skill を入れていない素の Claude Code を空のフォルダで起動する
2. `prompt.md` のプロンプトをそのまま実行する

**Skillあり**

1. Claude Code で `/plugin marketplace add anthropics/skills` を実行してマーケットプレイスを登録し、frontend-design プラグインをインストールする（または `with-skill/.claude/skills/frontend-design/` フォルダを制作フォルダへコピーする）
2. 同じプロンプトをそのまま実行する

## スクリーンショット

| | Skillなし | Skillあり |
| --- | --- | --- |
| PC | ![without PC](./screenshots/without-desktop.png) | ![with PC](./screenshots/with-desktop.png) |
| モバイル | ![without mobile](./screenshots/without-mobile.png) | ![with mobile](./screenshots/with-mobile.png) |

撮影条件：Chrome DevTools Protocolでビューポートをエミュレーションし（PC 1440×900、モバイル 375×667）、ページ全体を2倍解像度でキャプチャした。`index.html` は2つとも生成されたまま無改変。with-skill版は出現アニメーションを持つため、撮影用の一時コピーにだけ「アニメーション終了状態」のCSSを足して撮影した。

なお、without-skill版は375px幅でお問い合わせのメールアドレスが右へはみ出す（実測のページ幅は392px）。これも生成されたままの結果として、修正せず収録している。

## ライセンス

`with-skill/.claude/skills/frontend-design/` は Anthropic が公開している Skill の実物です（出典: https://github.com/anthropics/skills ）。Apache License 2.0 で提供されており、ライセンス全文を同フォルダの `LICENSE.txt` に同梱しています。改変せずそのまま収録しています。
