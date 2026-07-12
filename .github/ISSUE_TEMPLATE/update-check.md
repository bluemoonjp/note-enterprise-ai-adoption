---
name: 定期更新（鮮度確認）
about: 各社仕様・価格・認証など可変情報の四半期ごとの再確認
title: "[update] YYYY-Q? 可変情報の再確認"
labels: ["type:infra"]
assignees: []
---

## 目的

各社のプラン・価格・仕様・認証は変化する。可変情報を再確認し、記事の確認日・
再確認期限を更新する。

## 確認対象

- [ ] research/05-security-legal-procurement.md
- [ ] research/06-vendor-plans.md
- [ ] research/07-delivery-architecture-exit.md
- [ ] research/08-it-dept-agents.md（コネクタ/権限仕様）
- [ ] research/09-coding-agents.md（データ取り扱い/除外設定）
- [ ] その他、確認日が古い記事

## 手順

1. 各記事の一次情報を再取得し、差分を確認する。
2. 変わっていれば本文と比較表・確認日・再確認期限を更新する。
3. 更新責任者と次回再確認日を記録する。

## 完了条件

- [ ] 対象記事の確認日・再確認期限を更新した
- [ ] 変更点をPRにまとめた（`Closes #<番号>`）
