# CELESTE AIRWAYS ランディングページ制作ブリーフ

## 目的

架空の航空会社「CELESTE AIRWAYS」のランディングページを制作する。ブランドの世界観を伝えつつ、航空券検索と予約への導線を提供する。

## ターゲット

- 20〜40代の個人旅行者
- 移動の速さや運賃の安さよりも、快適さと安心感を重視する層

## トーン

- ネイビーを基調にした、誠実で上質な印象
- キーワード：心地よい、安心、洗練、旅への期待感
- デザインの方向性は `moodboard/celeste-airways-moodboard.jpg` を参照

## カラーパレット

| 役割 | HEX |
| --- | --- |
| ダークネイビー（ベース） | `#0B1D33` |
| ネイビー | `#1E3A5F` |
| ブルー（アクセント） | `#4A90D6` |
| ライトブルー | `#BBD7F0` |
| ペールブルー（背景） | `#EAF2F8` |
| ホワイト | `#FFFFFF` |
| ライトグレー（背景） | `#F3F5F7` |

## タイポグラフィ

- Noto Sans JP（見出し：Bold、本文：Regular）

## ページ構成

1. ヘッダー：ロゴ、ナビゲーション（旅先を探す／ご旅行の計画／ご搭乗サポート／Celeste Club）、ログイン
2. ヒーロー：キャッチコピー「まだ見ぬ世界へ、心地よい空の旅を。」、サブコピー、予約CTA
3. 航空券検索フォーム：往復・片道・複数都市の切り替え、出発地、到着地、出発日、搭乗者・クラス
4. おすすめの旅先：パリ ¥128,000〜／ニューヨーク ¥138,000〜／モルディブ ¥158,000〜／シンガポール ¥98,000〜
5. サービス紹介：快適な空の時間／こだわりの機内食／スムーズな旅をサポート／安全への取り組み
6. 特別なオファー：ヨーロッパ行き特別運賃 最大20%OFF／早期予約割引 南の楽園へ 最大15%OFF／Celeste Club会員限定 ボーナスマイルキャンペーン
7. フッター：ナビゲーション、SNSリンク、コピーライト

## 素材

- `images/hero.jpg`：ヒーロー用（雲海の上の翼）
- `images/dest-paris.jpg`・`images/dest-newyork.jpg`・`images/dest-maldives.jpg`・`images/dest-singapore.jpg`：旅先カード用
- `images/offer-europe.jpg`・`images/offer-beach.jpg`・`images/offer-club.jpg`：オファーカード用
- `moodboard/celeste-airways-moodboard.jpg`：ムードボード

## 制約

- 静的HTML＋CSSの1ページ構成（`index.html` と `css/style.css`）
- JavaScriptは使わない
- ビルドツールは使わない
- フォントはGoogle FontsのNoto Sans JPのみ
- 画像は `images/` にあるものだけを使う
