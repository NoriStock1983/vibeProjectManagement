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

## 新しいスキルを追加するには

1. `common/<skill-name>/SKILL.md` を作成（frontmatter に `name` と `description` を記載）
2. 必要に応じて `assets/` にテンプレートなどを追加
3. このファイル（README.md）に項目を追記
