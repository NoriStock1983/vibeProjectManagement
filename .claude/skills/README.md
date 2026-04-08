# Skills 一覧

Claude Code のカスタムスキル集。会話の中でスキル名を呼びかけるか、`/` コマンドで実行する。

---

## common/

汎用スキル群。プロジェクト横断で使えるドキュメント生成系。

### [adr](common/adr/SKILL.md) — Architecture Decision Record 作成

プロジェクトの重要な技術・設計・運用上の意思決定を ADR として記録する。

| 項目 | 内容 |
|------|------|
| **実行コマンド** | `/adr` または「ADRを作って」「決定事項を記録して」と話しかける |
| **出力先** | `vibeProjectManagement/docs/adr/ADR-NNNN_タイトル.md` |
| **入力** | 決定内容のテキスト / ファイルパス / 口頭説明 |

**できること:**
- 採番ルールに従って ADR 番号を自動採番（ADR-0001 〜）
- 背景・選択肢・決定理由・影響を構造化して記録
- テンプレート ([assets/template.md](common/adr/assets/template.md)) に従ったフォーマットで出力

---

### [minutes](common/minutes/SKILL.md) — 議事録作成

録音・文字起こしテキストから構造化された議事録 Markdown を生成する。

| 項目 | 内容 |
|------|------|
| **実行コマンド** | `/minutes` または「議事録を作って」「文字起こしから議事録」と話しかける |
| **出力先** | `vibeProjectManagement/docs/minutes/YYYY-MM-DD_議題名.md` |
| **入力** | 文字起こしテキスト / `.txt` / `.md` ファイルパス |

**できること:**
- 参加者・日時・場所を整理してヘッダーに記載
- 議題ごとにサマリーと決定事項を抽出
- アクションアイテム（誰が・何を・いつまでに）を一覧化
- テンプレート ([assets/template.md](common/minutes/assets/template.md)) に従ったフォーマットで出力

---

### [weekly-report](common/weekly-report/SKILL.md) — 週次報告資料作成

WBSの進捗・課題リスク・品質情報を収集し、週次報告Markdownを生成する。

| 項目 | 内容 |
|------|------|
| **実行コマンド** | `/weekly-report` または「週次報告を作って」「週報を作成して」と話しかける |
| **出力先** | `vibeProjectManagement/docs/weekly-reports/YYYY-MM-DD_週次報告.md` |
| **入力** | 報告対象週 / WBS・課題・品質情報のファイルパス（省略時は `docs/` を自動探索） |

**できること:**

- WBSの完了・進行中・遅延タスクを一覧化し、達成率を算出
- 課題・リスクを深刻度・発生確率・影響度で整理し、対処方法を記載
- テスト実施状況・バグ管理状況・品質指標を表形式で報告
- テンプレート ([assets/template.md](common/weekly-report/assets/template.md)) に従ったフォーマットで出力

---

## requirements/

要件定義スキル群（PMBOK第8版準拠）。要件定義Agentから呼び出される各資料作成スキル。単独でも使用可能。

> **要件定義のオーケストレーションは Agent に移行済み。**  
> 「要件定義をやって」などと話しかけると `.claude/agents/requirements/agent.md` が自律的に起動し、以下のスキルを順番に呼び出す。

| スキル名 | 作成文書 | 実行コマンド |
| ------- | ------- | ---------- |
| [create-business-case](requirements/create-business-case/SKILL.md) | ビジネスケース | `/create-business-case` |
| [create-project-charter](requirements/create-project-charter/SKILL.md) | プロジェクト憲章 | `/create-project-charter` |
| [create-stakeholder-register](requirements/create-stakeholder-register/SKILL.md) | ステークホルダー登録簿 | `/create-stakeholder-register` |
| [create-requirements-management-plan](requirements/create-requirements-management-plan/SKILL.md) | 要件マネジメント計画書 | `/create-requirements-management-plan` |
| [create-assumption-log](requirements/create-assumption-log/SKILL.md) | 前提条件・制約条件ログ | `/create-assumption-log` |
| [create-requirements-documentation](requirements/create-requirements-documentation/SKILL.md) | 要件文書 | `/create-requirements-documentation` |
| [create-project-scope-statement](requirements/create-project-scope-statement/SKILL.md) | プロジェクトスコープ記述書 | `/create-project-scope-statement` |
| [create-requirements-traceability-matrix](requirements/create-requirements-traceability-matrix/SKILL.md) | 要件トレーサビリティマトリクス | `/create-requirements-traceability-matrix` |
| [create-wbs](requirements/create-wbs/SKILL.md) | WBS（作業分解構造図） | `/create-wbs` |

全文書の出力先：`vibeProjectManagement/docs/requirements/`

---

## 新しいスキルを追加するには

1. 用途に応じて `common/<skill-name>/` または `requirements/<skill-name>/` にフォルダを作成
2. `SKILL.md` を作成（frontmatter に `name` と `description` を記載）
3. 必要に応じて `assets/` にテンプレートなどを追加
4. このファイル（README.md）に項目を追記
