# VibePM

Claude Code にプロジェクトマネジメント作業を委譲するプロジェクト。  
仕様書・議事録・WBS・週次報告などの定型的な作業を Claude に担わせることで、人間が価値創造に集中できる環境を目指す。

---

## フォルダ構成

```text
vibeProjectManagement/
├── CLAUDE.md               # Claude Code 向け作業ガイド
├── docs/
│   ├── project/            # プロジェクト基盤情報
│   ├── adr/                # Architecture Decision Records
│   ├── minutes/            # 議事録
│   ├── requirements/       # 要件定義文書
│   ├── weekly-reports/     # 週次報告
│   └── wbs/                # WBS（作業分解構造図）
├── src/
│   └── backend/            # バックエンド実装（C# / .NET）
└── .claude/
    ├── rules/              # Claude コーディング規約
    ├── skills/             # Claude スキル定義
    └── agents/             # Claude エージェント定義
```

---

## 各フォルダの目的

### `docs/project/`

プロジェクト全体を理解するための基盤情報。人間同士のコミュニケーションでも参照する。  
Claude がドキュメントを生成する際にも参照するため、常に最新の状態を保つこと。

| ファイル | 内容 |
| --- | --- |
| `overview.md` | プロジェクト概要・目的・フェーズ・スコープ |
| `stakeholders.md` | ステークスホルダー一覧・役割・連絡先 |
| `schedule.md` | マイルストーン・スケジュール |
| `architecture.md` | システム構成・技術スタック・設計方針 |

### `docs/adr/`

プロジェクトの重要な意思決定を記録した Architecture Decision Records。  
技術選定・設計方針・運用ルールなど、「なぜその決定をしたか」を残す。

### `docs/minutes/`

会議の議事録。Claude の `/minutes` スキルで文字起こしから自動生成される。

### `docs/requirements/`

PMBOK 第8版準拠の要件定義文書一式。Claude の要件定義 Agent によって生成される。  
（ビジネスケース・プロジェクト憲章・要件文書・トレーサビリティマトリクスなど）

### `docs/weekly-reports/`

週次報告資料。Claude の `/weekly-report` スキルで WBS・課題情報から自動生成される。

### `docs/wbs/`

WBS（作業分解構造図）。Claude の `/create-wbs` スキルで生成・更新される。

### `src/backend/`

バックエンド実装。C# / .NET で構築される Web API。

---

## Claude Code を使う場合

このプロジェクトは Claude Code による作業委譲を前提としている。

| ファイル / フォルダ | 役割 |
| --- | --- |
| `CLAUDE.md` | Claude への作業指示・参照ファイルの案内 |
| `.claude/rules/` | 言語別コーディング規約（Go・C#） |
| `.claude/skills/` | ドキュメント生成・レビュースキル定義 |
| `.claude/agents/` | 複数スキルを束ねるエージェント定義 |

利用可能なスキルの一覧は [`.claude/skills/README.md`](.claude/skills/README.md) を参照。
