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
