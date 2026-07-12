# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

> 上記は Claude Code が読み込む定型ヘッダ（変更不可）。以降の本文はすべて日本語で記述する。

## まず AGENTS.md を読む（運用ルールの正本）

本リポジトリの作業ルール（目的・出典必須・確認日・更新責任者・Issue駆動フロー・
ディレクトリの意味・ステータス遷移・比較表ルール・Codexレビューの回し方・よく使う
コマンド・品質チェック）はすべて [AGENTS.md](AGENTS.md) に集約している。
**作業前に AGENTS.md を読むこと。** ルールの変更は AGENTS.md 側に加える。

このファイルには**共通ルールを再掲しない**（正本との乖離を防ぐため）。以下は Claude Code
固有のツール利用上の補足のみ。

## Claude Code 固有の補足

- このリポジトリはアプリケーションコードではなく**日本語の調査ドキュメント（Markdown）**。
  ビルド・テスト・lint は存在しない（AGENTS.md の品質チェックに従う）。
- Web 調査には `WebSearch` / `WebFetch` を使い、参照した一次情報を記事末尾の「参考文献」に残す。
- Codex レビュー・ループは `codex exec "<依頼＋対象パス>"` で回し、各回を
  `docs/reviews/codex-review-round-N.md` に記録する（最大5回）。詳細な運用は AGENTS.md。
