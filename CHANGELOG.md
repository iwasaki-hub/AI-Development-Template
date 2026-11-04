# 変更履歴

本ファイルは共通開発テンプレートの変更を記録します。導入先プロジェクトの開発履歴は、そのプロジェクトで管理します。

## 1.2.0 — CI保護と検証証跡の強化

- Gate 0〜7を補強し、CIトリガー・責務・必須チェックの発行元、保護設定と権限、最新Headに対応する結果の確認を明確化。
- テスト導入・CI統合・必須化・保護動作実証を段階化。承認された検証専用PRで正常→失敗→ブロック→復旧を確認し、未マージ終了後に結果だけを履歴へ反映する運用を追加。
- Artifactの生成・保存・存在・内容確認・Viewer解析を区別し、実行ID/attempt、対象SHA、期限、確認者・確認深度を記録。
- PR Head、CI checkout、マージ、公開対象のSHAは単純一致ではなく対応する参照・変更内容で追跡。CI再実行・環境対処とコード修正ループも区別。
- プロファイルにCI・E2E隔離環境・保護設定・Artifact・証跡・SHA追跡欄を追加し、READMEに新規導入とv1.1.0からの更新方法を記載。
- v1.1.0のGate番号、文書名、人間承認・再承認、安全規則、同一課題最大3回を維持。既存プロファイル欄を保持し、特定サービスやツールを必須化しない。

### 改善の根拠

[TodoアプリPR #13](https://github.com/iwasaki-hub/todo-app/pull/13)（ローカルE2E）、[PR #14](https://github.com/iwasaki-hub/todo-app/pull/14)（CI統合）、[PR #15](https://github.com/iwasaki-hub/todo-app/pull/15)（保護動作検証・Closed / Unmerged）、[PR #16](https://github.com/iwasaki-hub/todo-app/pull/16)（履歴記録）と、[Phase 5履歴](https://github.com/iwasaki-hub/todo-app/blob/f957fdec3dbc6e80f5203fb2c38b15fa878b7c93/docs/development-history/phase-05-development-log.md)を根拠とする。

Phase 5では恒常CIの単体等55件・E2E9件成功、必須2チェック、検証PRでの意図的失敗によるブロック・Artifact保存・復旧を記録した。検証PRのE2E10件とmainの9件を区別し、Trace Viewer対話再生等の未実施範囲も維持する。今回の文書更新ではTodoアプリのテストを再実行していない。Phase 6〜7の未実証事項は後続版の検討対象とする。

この節は改善内容を記録する。マージ・Gitタグ・GitHub Releaseの状態はGitHub上の対応する履歴を参照する。

## 1.1.0 — 自動テスト運用ルールの強化

- 自動テスト品質の標準化：単体・結合・UI・E2E・実機の責任範囲、ローカル/CI/人間の確認、未導入・未実施・成功・失敗を区別。
- 導入前の安定版・ランタイム・依存要件・フレームワーク・lockfile・CI互換性確認を追加。強制解決を禁止。
- 状態分離、モック等の復元、後片付け、非同期待機、順序変更・固定seedによる再現性確認と修正ループの証跡を明確化。
- カバレッジの実測指標、対象・除外、分子・分母、未テスト領域の記録を追加。一律の数値目標は設けない。
- 既存データ契約との照合、開発/本番依存の警告の影響・互換性・未解消事項の記録を強化。
- プロファイルに上記の設定欄を整理し、READMEに改善点とメジャー1系のファイル命名方針を記載。Gate 0〜7、承認条件、同一課題最大3回の上限、安全規則は維持。

### 改善の根拠

[TodoアプリPR #6](https://github.com/iwasaki-hub/todo-app/pull/6)、[履歴更新PR #7](https://github.com/iwasaki-hub/todo-app/pull/7)、[P3開発履歴](https://github.com/iwasaki-hub/todo-app/blob/main/docs/development-history/phase-03-development-log.md)に記録された次の知見を一般化した。以下はP3の作業記録に基づくもので、このテンプレート更新で再実行した検証ではない。

- 安定版・engines・peer依存を照合し、強制解決なしで導入。CI実行は未実施で、追加のランタイム要件を引き継いだ。
- 状態分離・復元・後片付けを構成し、55件のローカルテストと固定seedでの順序シャッフルが成功。修正ループは0回だった。
- 計測対象7ファイルに限る100%の実測値と分子・分母を記録し、対象外と実ブラウザIME等の未検証範囲を明示した。
- 依頼と保存キーの表記差を記録して既存互換性を維持。開発依存moderate 12件・本番依存0件を区別し、警告は未解消として記録した。

この節はv1.1.0の改善内容を記録する。マージ・Gitタグ・GitHub Releaseの状態はGitHub上の対応する履歴を参照する。

## 1.0.0 — 2026-11-04

### 初期構成

- 既存の [共通開発標準](AI_Development_Standard_v1.md) と [プロファイルテンプレート](project-profile-template.md) を基盤として採用。
- [AGENTS.md](AGENTS.md) に標準の読み込み、既存ルールの尊重、安全なGit運用、承認条件、完了報告を記載。
- [README.md](README.md) に目的、構成、導入手順、ChatGPT・Codex・人間の役割分担、検証方針を記載。
- 特定サービスの必須化、プロジェクト固有設定、依存関係の追加を伴わない文書テンプレートとして整備。

この記録は初期構成の変更履歴であり、PRのマージ・Gitタグ・リリースの作成を示すものではありません。
