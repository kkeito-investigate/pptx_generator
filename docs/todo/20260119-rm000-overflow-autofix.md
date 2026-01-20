---
目標: テキスト溢れ時の自動対処ルールを適用して超過行を抑制する
関連ブランチ: feat/overflow-autofix
関連Issue: #542
roadmap_item: RM-000 例: RMなしIssue C
---

- [x] ブランチ作成・初期コミット・push
  - メモ: ブランチ名: feat/overflow-autofix / 初期コミット: docs(todo): add rm000 overflow autofix / push: 済み
    - 必ず main からブランチを切る
- [x] 計画策定（スコープ・前提の整理）
  - メモ: 承認済み Plan をそのまま転記する。以下の項目を含めること
    - 対象スコープ: MappingStep で body 超過時に自動短縮し末尾に "..." を付与
    - 対象ファイル: src/pptx_generator/pipeline/mapping/processor.py, tests/pipeline/mapping/test_mapping_step_layout_assignment.py
    - 前提: max_lines は layout の text_hint を使用
    - ドキュメント／コード修正方針: body を短縮し warnings に記録
    - 確認・共有方法: ToDo 更新、Issue コメント
    - 想定影響ファイル: generate_ready.json の body 出力
    - リスク: 内容の末尾が削られる
    - テスト方針: PYTHONPATH=src python -m pytest tests/pipeline/mapping/test_mapping_step_layout_assignment.py
    - ロールバック方針: 追加処理を revert
    - 承認メッセージ ID／リンク: ユーザー OK
- [x] 設計・実装方針の確定
  - メモ: max_lines 超過時に body を短縮し、末尾行へ "..." を付与する
  - [x] 設計・実装方針メモの共有（不要）
  - [x] 方針メモを更新するまで以降の stage へ進まないこと
- [x] 実装
  - メモ: src/pptx_generator/pipeline/mapping/processor.py, tests/pipeline/mapping/test_mapping_step_layout_assignment.py
- [x] テスト・検証
  - メモ: PYTHONPATH=src python -m pytest -n 0 tests/pipeline/mapping/test_mapping_step_layout_assignment.py / 10 passed / coverage.xml / diff-cover: python -m diff_cover.diff_cover_tool coverage.xml --compare-branch origin/main / Coverage 100%（26 lines）
- [x] ドキュメント更新
  - メモ: docs/todo/20260119-rm000-overflow-autofix.md, C:\PPT_test_textyabai\実施事項概要.md
  - メモ: 対象外: docs/roadmap 配下, docs/requirements 配下, docs/design 配下, docs/runbook 配下, README.md / AGENTS.md
  - [x] docs/roadmap 配下
  - [x] docs/requirements 配下（実装結果との整合を確認）
  - [x] docs/design 配下（実装結果との整合を確認）
  - [x] docs/runbook 配下
  - [x] README.md / AGENTS.md
- [x] 関連Issue 行動更新
  - メモ: 関連Issue: #542
- [ ] チェックリスト整合確認
  - メモ: 子タスク完了時に親タスクが未チェックになっていないか確認し、必要に応じて `[x]` へ更新する。親タスクのメモに完了内容を残す
- [ ] PR 作成
  - メモ: PR 番号と URL を記録。ワークフローが未動作の場合のみ原因を記載する。todo-auto-complete が自動更新するため手動でチェックしない

## メモ
- 連続性メモ（短文で上書き）
  - 前提/制約: max_lines は layout の text_hint を使用
  - 決定と根拠: 超過時は末尾行に "..." を付けて短縮
  - リスク(UNCONFIRMED): 内容の末尾が削られる
  - Now/Next: Now=PR 作成 / Next=レビュー対応
  - テスト実績/抜け: PYTHONPATH=src python -m pytest -n 0 tests/pipeline/mapping/test_mapping_step_layout_assignment.py / 10 passed / diff-cover 100%
  - テスト実績/抜け:
- 計画のみで完了する場合は、判断者・判断日・次アクション条件を記載する
