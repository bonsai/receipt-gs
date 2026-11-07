# ReceiptGS

3D Gaussian Splattingでロール紙から伸びるレシートを表現し、SVGでクイズを印字するブラウザアプリ。

## MVP決定事項
- 紙形状：ロールから伸びるレシート
- 対応環境：PC・スマートフォン
- 3D：PlayCanvas Engine + 3DGS
- 文字：SVGオーバーレイ
- 制御：JavaScript
- 問題データ：JSON
- WASM：必要性を検証してから導入

## 最初の縦切り
ロール紙を表示 → 紙が伸びる → 1問印字 → 3択回答 → 正誤・解説を印字。

## Docs
- [PRD](docs/PRD.md)
- [ADR](docs/ADR.md)
- [Data Spec](docs/DATA-SPEC.md)
- [Animation State](docs/ANIMATION-STATE.md)
- [Implementation Tasks](docs/IMPLEMENTATION-TASKS.md)

## Development
初期実装はVite + JavaScriptを想定。3DGSの読み込みはPlayCanvasの標準機能を優先し、独自WASMは性能測定後に判断する。

## Status
仕様確定・実装前。GSアセットおよびブラウザ実機検証は未実施。

## 応用：週刊サブちゃん第1回（2026-11-07 追記）

- ReceiptGSの実コンテンツとして、週刊サブちゃん第1回「安来節の原稿」をレシートに載せる方向（2026-11-07）。
- 原稿は800字。58mm幅・標準字（16字／行）で本文約21cm、見出しとQRコード込みで全長およそ25cmの細長い帯になる。
- **文字組（もじぐみ）が要注意**：文字は3DGS化すると滲んで読めなくなる。MVP決定事項のとおり文字はSVGオーバーレイ側で組を確定させ、3DGSは紙の丸まり・垂れ・置かれる空間を受け持つ分業にする。
- 末尾にSubstackへのQRコードを入れ、感熱紙の「消える紙」から「残る文章」への橋渡しにする。
