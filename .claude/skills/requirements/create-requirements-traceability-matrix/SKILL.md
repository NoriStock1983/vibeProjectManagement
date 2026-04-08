---
name: create-requirements-traceability-matrix
description: PMBOK第8版準拠の要件トレーサビリティマトリクス（Requirements Traceability Matrix, RTM）を作成するスキル。「RTMを作って」「要件トレーサビリティマトリクスを作って」「requirements traceability matrix」「要件の追跡表を作って」と依頼されたとき、または要件定義Agentのステップ8として呼び出されたときに使う。
disable-model-invocation: false
---

# 要件トレーサビリティマトリクス作成スキル（PMBOK第8版準拠）

要件トレーサビリティマトリクス（Requirements Traceability Matrix: RTM）を作成し、Markdownファイルとして保存する。

## 目的

各要件がビジネス目的に対応しているかを追跡し、テストによる検証が完了しているかを確認するための文書。PMBOK第8版においてもスコープ管理と価値実現の追跡に必須とされている。

## 入力情報の収集

RTMを作成するには、以下の文書が必要。既に作成されている場合は参照する：

- 要件文書（requirements-documentation）— 要件IDと要件詳細
- ビジネスケース（business-case）— ビジネス目標
- プロジェクトスコープ記述書（project-scope-statement）— 成果物一覧

未作成の文書がある場合は、ユーザーに確認してから作成を進める。

以下の追加情報が必要な場合はユーザーに確認する：
1. 設計成果物との対応関係（画面仕様書・API仕様書・DB設計書などの文書名・ID）
2. テストケースとの対応関係（テストケースID・テスト計画書）
3. 実装モジュール・コンポーネントとの対応関係

## 出力形式

ファイル名：`requirements-traceability-matrix_[プロジェクト名].md`
保存先：`vibeProjectManagement/docs/requirements/`

テンプレートは [assets/template.md](assets/template.md) に定義されている。必ずこのファイルを読み込み、その構造に従って出力する。

## 作成の指針

- **要件文書の全要件を網羅する** — 要件の漏れがないようにすべての要件IDを含める
- **双方向トレーサビリティを確保する** — ビジネス目標→要件→設計→実装→テストの正方向と、テスト→要件→ビジネス目標の逆方向が追跡できること
- **ステータスを常に最新に保つ** — 設計・開発・テストの進捗に合わせて随時更新する
- 設計・テストが未実施の段階では「未定義」と記載し、進捗に合わせて埋めていく

## 作成後の処理

ファイル保存後、ユーザーに保存パスを伝え、「内容の確認・修正があればお知らせください」と案内する。
