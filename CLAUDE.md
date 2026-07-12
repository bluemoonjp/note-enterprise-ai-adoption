# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 本リポジトリの作業ルールは AGENTS.md が正本

運用ルール（目的・出典必須・確認日・Issue駆動フロー・ディレクトリの意味・Codex
レビューの回し方・よく使うコマンド）は [AGENTS.md](AGENTS.md) に集約している。
**まず AGENTS.md を読むこと。** 本ファイルは Claude Code 固有の補足のみを記載し、
運用ルールを二重に持たない（変更は AGENTS.md 側に加える）。

## このリポジトリの性質

- コードベースではなく、**日本語の調査ドキュメント（Markdown）プロジェクト**。
  ビルド・テスト・lint の対象となるアプリケーションコードはない。
- 「作業＝Issueに紐づく記事の執筆・改稿、または基盤（規約・テンプレート）の整備」。
- 想定読者は非IT中小企業の情シス／社内SE部門。詳細は
  [research/00-overview.md](research/00-overview.md)。

## Claude Code 固有の補足

- **必ず日本語**で執筆・コミット・Issue記載を行う（AGENTS.md のルール4）。
- 事実主張には一次情報リンクと確認日を必ず付ける（AGENTS.md のルール1・2）。
  Web 調査時は `WebSearch` / `WebFetch` を使い、参照した公式ページを記事末尾の
  「参考文献」に残す。
- 課題管理は GitHub Issues。ローカルに独自TODOファイルを作らない。作業の区切りは
  `gh issue` / `gh pr` を使う。
- Codex レビュー・ループは `codex exec "<依頼＋対象パス>"` で回し、各回を
  `docs/reviews/codex-review-round-N.md` に記録する（最大5回）。
- 記事を書く前に [docs/style-guide.md](docs/style-guide.md) と
  [docs/glossary.md](docs/glossary.md) を確認する。

## よく使うコマンド

コマンド一覧は [AGENTS.md の「よく使うコマンド」](AGENTS.md) を参照。lint/build/test は
存在しない。品質確認は「内部リンク切れ・出典と確認日・用語整合」の目視レビューで行う。
