# 中小企業向け AI・AIエージェント 社内導入 調査プロジェクト

非IT中小企業（100〜500人規模）の**情シス／社内SE部門**を想定読者に、
「AI・AIエージェントを、まずIT部門に小規模導入して効果を最大化する」ための
**意思決定根拠**を、出典付きの社内向け調査ドキュメントとして体系的にまとめるプロジェクトです。

> ⚠️ 本リポジトリは調査・整理を目的とした一般的な情報提供であり、法務・税務・
> 投資・セキュリティに関する最終判断は各分野の専門家・公式ドキュメントの確認が必要です。

## 想定環境

- 大企業ではなく非IT中小企業（100〜500人規模）。
- 社内SE部門があり5〜15名程度。小規模開発は行うがモダンな開発手法は未導入。部署全体は
  開発主体ではなく情シス寄り。
- 全社導入はハードルが高いため、まずIT部門で小規模導入し効果を最大化したい。
- Claude 導入を主に想定（記事では Codex／OpenAI も同等に扱う）。

詳細は [research/00-overview.md](research/00-overview.md)。

## このリポジトリの構成

| パス | 内容 |
| --- | --- |
| [research/](research/) | 調査記事（Markdown、`00`〜`09` の連番） |
| [research/README.md](research/README.md) | 記事インデックス（各記事のステータス一覧） |
| [docs/style-guide.md](docs/style-guide.md) | 執筆・出典規約 |
| [docs/glossary.md](docs/glossary.md) | 用語集 |
| [docs/reviews/](docs/reviews/) | Codex 独立プラン・レビュー各回の記録 |
| [AGENTS.md](AGENTS.md) | 作業ルールの**正本**（Codex / Claude Code 共通） |
| [CLAUDE.md](CLAUDE.md) | Claude Code 固有の補足（AGENTS.md を参照） |
| [CONTRIBUTING.md](CONTRIBUTING.md) | 貢献・執筆フロー |

## 調査トピック（予定）

各トピックは GitHub Issues で管理し、記事として `research/` に整備します。進捗は
[記事インデックス](research/README.md) と [Issues](../../issues) を参照してください。
構成は Codex の独立プラン（[docs/reviews/codex-plan.md](docs/reviews/codex-plan.md)）を取り込んで再編しています。

00. エグゼクティブサマリ・想定環境
01. 導入判断とユースケース選定（不導入リスクを含む）
02. ビジネスケース・費用・ROI（TCO／投資か費用か／原価か販管費か）
03. 効果を出す条件・DX・業務再設計
04. ガバナンス・社内規程・責任分担
05. セキュリティ・プライバシー・法務・調達
06. 製品・プラン別統制機能比較（Team / Enterprise / API）
07. 提供方式・アーキテクチャ・出口戦略（SaaS vs Bedrock vs Foundry）
08. IT部門向けAIエージェント（限界と権限越境リスク）
09. コーディングエージェント
10. パイロット運営・教育・効果測定
11. 段階導入ロードマップと判断ゲート
- 付録: 実務テンプレート集（稟議書・利用規程・評価票 等）

## 課題管理・貢献

- 課題管理は **GitHub Issues** で行います（ローカルにTODOファイルは置きません）。
- 作業フローは [CONTRIBUTING.md](CONTRIBUTING.md) を参照してください。
- Claude Code / Codex いずれからでも作業できます。作業前に [AGENTS.md](AGENTS.md) を読んでください。

## ライセンス

ドキュメントは [CC BY 4.0](LICENSE)（予定）。詳細は LICENSE を参照。
