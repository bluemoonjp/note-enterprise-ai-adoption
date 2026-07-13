# 貢献ガイド（CONTRIBUTING）

本リポジトリは日本語の調査ドキュメントプロジェクトです。作業の共通ルールの正本は
[AGENTS.md](AGENTS.md) にあります。このファイルは**貢献フロー**に絞って説明します。

## 前提ツール

- `git`
- `gh`（GitHub CLI、認証済み）
- 任意: `codex`（Codex CLI）／Claude Code — どちらからでも作業可能

## 作業フロー（Issue駆動）

1. **Issueを選ぶ / 立てる**
   - 既存Issue: `gh issue list` で確認。
   - 新規: `gh issue create` でテンプレート（調査記事 / 基盤タスク）に沿って起票。
2. **ブランチを切る**（`main` から）
   - 記事: `article/<番号>-<slug>`（例 `article/05-vendor-plans`）
   - 基盤: `infra/<slug>`（例 `infra/style-guide`）
   - レビュー記録: `review/round-<N>`
3. **書く**
   - [docs/style-guide.md](docs/style-guide.md) と [docs/glossary.md](docs/glossary.md) に従う。
   - 事実・数値・各社仕様には**一次情報リンク＋確認日**を付け、末尾「参考文献」にも列挙。
4. **コミット**（日本語、末尾にIssue番号）
   - 例: `05: 各社プラン比較の初稿 (#12)`
5. **Pull Request**
   - `gh pr create --fill` 。本文に `Closes #<番号>` を記載。
   - 記事PRは Codex レビュー（下記）を通す。
6. **レビュー反映 → マージ**
   - 「大きな指摘」が解消したらマージ。

## 記事の受入基準（Definition of Done）

- [ ] 先頭にステータス・確認日・再確認期限がある。
- [ ] 主要な主張それぞれに、本文中の一次情報リンクがある。
- [ ] 末尾に「参考文献」節があり、本文の出典と対応している。
- [ ] 各社仕様など変化する情報に確認日が併記されている。
- [ ] 事実と本プロジェクトの解釈・推奨が区別されている。
- [ ] 法務・税務・投資に関わる箇所に免責がある。
- [ ] 用語が `docs/glossary.md` と整合している。
- [ ] Markdown の内部リンク切れがない。
- [ ] `research/README.md` のインデックスを更新した。

## Codex レビュー・ループ

- 実行: `codex exec "<レビュー依頼＋対象パス>"`（非対話）。
- 記録: `docs/reviews/codex-review-round-N.md` に対象・指摘・対応を残す。
- 終了条件: 大きな指摘がなくなれば完了。**5回**到達は反復の打切りに限り、残る大きな指摘は
  Issue化して当該成果物の「公開可」移行を保留する（詳細は [AGENTS.md](AGENTS.md)）。

## コミットメッセージ規約

- 日本語。先頭に対象（記事番号 or `infra:` / `docs:` / `review:`）。
- 末尾に関連Issue番号 `(#N)`。
- 例: `docs: スタイルガイドに確認日ルールを追加 (#3)`
