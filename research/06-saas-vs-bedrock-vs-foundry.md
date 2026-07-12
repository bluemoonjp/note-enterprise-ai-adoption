# SaaS Enterprise vs AWS Bedrock vs Microsoft Foundry

> ステータス: アウトライン
> 確認日: 2026-07-12
> 関連Issue: （起票後に記入）

法人SaaS（Claude/ChatGPT の Enterprise 等）と、AWS Bedrock / Microsoft Foundry
（Azure AI Foundry）経由の利用をどう使い分けるか、どちらがどの用途に向くかを整理する。

## 要約（結論先出し）

- （執筆時に記入）

## 1. 3構成の位置づけ

- **法人SaaS Enterprise**: 導入が速く、統制機能も揃う。通常業務〜社外秘（マスキング前提）。
- **Bedrock / Foundry 経由**: データが自社クラウド境界内で処理される構成を取りやすい。
  顧客データ・個人情報を含む処理の受け皿。
- （参考: オンプレ／ローカルLLM、または入力禁止＝最も機微な領域）

## 2. 比較の観点

- データの所在・越境移転の整理しやすさ／利用できるモデル／統制・監査／構築運用コスト・
  必要スキル／導入スピード。

## 3. 比較表（記入予定）

| 観点 | SaaS Enterprise | AWS Bedrock | Microsoft Foundry |
| --- | --- | --- | --- |
| データ所在 | | | |
| 利用モデル | | | |
| 統制・監査 | | | |
| 導入スピード | | | |
| 必要スキル/運用 | | | |
| 向く用途 | | | |

## 4. 使い分けの指針（草案）

- 通常業務は SaaS、機微度が高い領域は Bedrock/Foundry、という階層化が実務的。
- 既存クラウド（AWS/Azure）との親和性が選択に効く。

## 5. 自社（情シス小規模導入）への当てはめ

- まず SaaS で知見を得て、Bedrock/Foundry が要る領域（[05](05-vendor-plans.md)の入力NG領域）を特定する。

## 留意点・免責

- 各基盤の対応モデル・リージョン・機能は変動。確認日と一次情報必須。

## 参考文献

<!-- AWS Bedrock / Azure AI Foundry / 各社Enterprise の公式ドキュメントを追加 -->
