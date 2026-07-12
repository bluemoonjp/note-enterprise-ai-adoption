# 00 エグゼクティブサマリ・想定環境

> ステータス: 初稿
> 対象読者: **上層（経営層・意思決定者）が最初に読む入口**。詳細な実務判断は情シス部門内向けの各記事へ。
> この記事が答える問い: 何を・なぜ・どの順で導入すべきか（1ページ相当の結論）
> 対象範囲: プロジェクト全体像・想定環境・各記事の結論集約 ／ 対象外: 各論の詳細（各記事へ）
> 確認日: 2026-07-13 ／ 再確認期限: 2026-10-31 ／ 更新責任者: （未定）
> 関連Issue: #1

## 要約（結論先出し・1ページ相当）

**結論**: 情シス部門限定で、法人プラン（Claude Team等）を使ったAI・AIエージェントの
パイロット導入を承認してほしい。全社展開ではなく、まず情シス自身が使い、3〜6ヶ月後に
実測データでEnterprise化・Bedrock/Foundry等への投資判断を行う。

**なぜ今か**: すでに個人アカウントでのAI利用（シャドーAI）が社内で起きている可能性が高い。
これは「導入するかどうか」の議論を待ってくれない、**現在進行形のリスク**である
（[01](01-adoption-criteria.md)）。業界的にも、AI・AIエージェントは「使うかどうか」の段階を
超えて基盤化が進んでいる（2節）。

**推奨案**: 情シス部門（想定5〜15名）限定で、Claude Team等の法人プランを正式導入する
（[06](06-vendor-plans.md)）。対象は文章・調査・整形・コードなど汎用作業から開始し、
個人情報・機密データを扱う業務は対象外とする（[01](01-adoption-criteria.md)、[05](05-security-legal-procurement.md)）。

**主要リスクと対策**:
- 社外へのデータ送信リスク → 情報区分に基づく入力可否ルールとマスキング運用で管理（[05](05-security-legal-procurement.md)）。
- エージェント固有の権限越境リスク → コネクタ許可制・最小権限設計で管理（[08](08-it-dept-agents.md)）。
- 「導入すれば自動的に儲かる」わけではない → 測定指標を先に決め、Hold/Stopの判断基準もあらかじめ用意する（[11](11-rollout-gates.md)）。
- ただでさえ忙しい情シスに運用の余裕があるのか → 希望者からの段階的開始とし、教育・運用工数は
  Enterprise展開時にも必要になる先行投資として位置づける（[02](02-cost.md)3節、[10](10-pilot-operations.md)1.4節）。
- 教育・運用が定着せず利用率が上がらないリスク → 利用率低迷を明示的な停止条件の一つとする（[10](10-pilot-operations.md)1.3節）。

**概算費用**: 情シス部門10名がClaude Team Standardを利用した場合、月額はおおむね**3万円程度**
（座席単価 約3,000円 × 10名の概算例。自社の実際の座席数・為替レートで再計算が必要、試算方法は
[02](02-cost.md)4.3節）。座席あたり月1人時程度の効果があれば費用は回収できる計算になる
（[02](02-cost.md)4節）。**この試算は文章・調査等の一般用途が対象で、コーディングエージェント
（[09](09-coding-agents.md)、別トラック・別予算）の費用は含まない**（上位プランが必要になる場合がある、
[06](06-vendor-plans.md)2.3節）。

**次の90日**: 30日で初期設定・教育を完了し、60〜90日でパイロットの5指標（[10](10-pilot-operations.md)、
[11](11-rollout-gates.md)3節）のベースラインを計測する。3〜6ヶ月後、その実測データをもって
次の投資判断（Enterprise化／Bedrock・Foundry検討／現状維持／中止）を行うことを、
**この提案の時点であらかじめ約束する**。

## 1. 想定読者と環境

- 非IT中小企業（100〜500人）。社内SE部門5〜15名、情シス寄りで開発主体ではない。
- 全社導入はハードルが高く、まずIT部門で小規模導入して効果を最大化したい。
- Claude 導入を主に想定（Codex/OpenAI も同等に扱う）。

## 2. なぜ今、AI・AIエージェントなのか（業界の潮流）

これは自社の判断根拠そのものではなく、**「なぜ今議論する価値があるか」の背景**として押さえる
参考情報である（判断根拠は自社のパイロット実測値を優先する、[02](02-cost.md)4.4節）。

- Microsoft CEOのSatya Nadella氏は、2026年6月のMicrosoft Build基調講演で、
  「本当の意味でのプラットフォームシフトが起きている。OSやアプリ向けデバイスを作ることから、
  エージェントへと移行している」という趣旨の発言をしている
  （[Microsoft "The Source" Build Keynote Transcript][ref-nadella-build2026]、確認日: 2026-07-13）。
- Gartnerは、2026年末までに**エンタープライズアプリの40%がタスク特化型AIエージェントを
  搭載する**と予測している（未満5%からの急増、[Gartner「Gartner Predicts 40% of Enterprise Apps
  Will Feature Task-Specific AI Agents by 2026」][ref-gartner-40pct]、2025-08-26付、確認日: 2026-07-13）。
- 一方で同社は、**エージェント型AIプロジェクトの40%超が2027年末までに中止される**とも予測しており
  （[Gartner「...Agentic AI Projects Will Be Canceled by End of 2027」][ref-gartner-cancel]、確認日: 2026-07-13）、
  「導入すれば自動的にうまくいく」わけではないことも同時に示されている。本プロジェクトが
  小規模パイロット・測定先行の進め方を推奨するのは、この失敗パターンを避けるためである
  （[02](02-cost.md)4.4節、[11](11-rollout-gates.md)）。

## 3. 本プロジェクトの立場

- 論点は「導入 vs 不導入」ではなく「**無管理の利用 vs 管理された利用**」（→ [01](01-adoption-criteria.md)）。
  すでに個人アカウントでの利用（シャドーAI）が起きているなら、不導入という選択肢は
  実質的に「無管理のまま放置する」ことを意味する。
- 「学習しない法人プラン」でも**社外送信そのもの**は残る。ポリシーは後者基準（→ [05](05-security-legal-procurement.md)）。
- IT部門が触っていないのに、エージェントの提案・設計・リスク評価はできない。まず情シス限定で
  導入し知見を上げ、次段階（Enterprise / Bedrock / Foundry）を判断ゲートで決める（→ [11](11-rollout-gates.md)）。

## 4. 反論への回答（想定される質問）

| 想定される反論 | 回答 |
| --- | --- |
| 社内情報を外部AIに出すのは危険では | 学習利用と社外送信は別問題。法人プランは学習に使わない前提で、他のクラウドサービスと同じ基準（開示リスク）で管理可能（[01](01-adoption-criteria.md)2.1節、[05](05-security-legal-procurement.md)） |
| 精度が不安・誤りが混ざるのでは | 下書き・レビュー前提の用途から始め、無検証で使わない運用にする（[01](01-adoption-criteria.md)2.2節） |
| うちの業務は特殊でAIが向かないのでは | 汎用作業（文章・調査・コード）は業種非依存で効果が出やすく、そこから着手する（[01](01-adoption-criteria.md)1.3節） |
| 費用に見合うのか | 座席あたり月1人時程度の削減で費用は回収できる試算。自社の実測値で3〜6ヶ月後に検証する（[02](02-cost.md)） |
| 情シス限定は中途半端では | 妥協ではなく、Enterprise/Bedrock投資判断に必要な知見を集める情報収集フェーズという設計（[06](06-vendor-plans.md)3節、[11](11-rollout-gates.md)1節） |
| どうせ全社のシャドーAIは解決しないのでは | その通りで、情シス限定導入だけでは解決しない。全社的な統制は別途必要（[01](01-adoption-criteria.md)3.3節、[04](04-governance.md)）。ただしまず情シスが統制の実務知見を持つことが前提になる |
| ただでさえ忙しい情シスに、教育・運用・測定までやる余裕があるのか | 強制利用ではなく希望者から開始し、運用工数（教育・例外対応・月次測定）はEnterprise展開時にも必要になる知見を先取りする投資と位置づける（[02](02-cost.md)3節、[10](10-pilot-operations.md)1.4節） |
| 教育・運用が定着せず利用率が上がらないのでは | 利用率低迷を明示的な停止条件の一つとしてあらかじめ定義する（[10](10-pilot-operations.md)1.3節） |

## 5. 記事マップ

| 段 | 記事 |
| --- | --- |
| 判断 | [01 導入判断](01-adoption-criteria.md) / [02 費用・ROI](02-cost.md) / [03 効果・DX](03-effectiveness-dx.md) |
| 統制 | [04 ガバナンス](04-governance.md) / [05 セキュリティ・法務・調達](05-security-legal-procurement.md) |
| 製品 | [06 プラン比較](06-vendor-plans.md) / [07 提供方式・出口戦略](07-delivery-architecture-exit.md) |
| 応用 | [08 IT部門エージェント](08-it-dept-agents.md) / [09 コーディングエージェント](09-coding-agents.md) |
| 実施 | [10 パイロット運営](10-pilot-operations.md) / [11 ロードマップ・判断ゲート](11-rollout-gates.md) |
| 実務 | [付録 テンプレート集](appendix/README.md) |

## 留意点・免責

- 一般的な整理であり、法務・税務・セキュリティの最終判断は専門家・公式情報の確認が必要。
- 費用試算・タイムラインは自社の状況に応じて置き換えること（[02](02-cost.md)、[11](11-rollout-gates.md)）。

## 参考文献

[ref-nadella-build2026]: https://msthesource.thesourcemediaassets.com/2026/06/06022026_Nadella_TRANSCRIPT_Build-Keynote.pdf "Microsoft \"The Source\" — Satya Nadella Build 2026 Keynote Transcript（確認日: 2026-07-13）"
[ref-gartner-40pct]: https://www.gartner.com/en/newsroom/press-releases/2025-08-26-gartner-predicts-40-percent-of-enterprise-apps-will-feature-task-specific-ai-agents-by-2026-up-from-less-than-5-percent-in-2025 "Gartner — Gartner Predicts 40% of Enterprise Apps Will Feature Task-Specific AI Agents by 2026（確認日: 2026-07-13）"
[ref-gartner-cancel]: https://www.gartner.com/en/newsroom/press-releases/2025-06-25-gartner-predicts-over-40-percent-of-agentic-ai-projects-will-be-canceled-by-end-of-2027 "Gartner — Gartner Predicts Over 40% of Agentic AI Projects Will Be Canceled by End of 2027（確認日: 2026-07-13）"
