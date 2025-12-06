# prompt_playground

LLM (here, for Gemini WebUI) prompts playground and archives.
Gemini WebUI 向けのプロンプトを実験、管理、アーカイブするためのリポジトリです。

## 概要

このプロジェクトは、LLM（特に Gemini）の挙動を制御するためのプロンプトエンジニアリングのplaygroundです。
長大なプロンプトを単一のファイルで管理するのではなく、機能や役割ごとに「ブロック（Bricks）」としてモジュール化し、必要に応じて組み合わせたり、特定の機能をテストしたりすることを目的としています。

  *ですが、将来的にはgemini-webUI以外のツールやモデルにも範囲を広げる予定です。*

## ディレクトリ構成

### `instruction_bricks/`
プロンプトを構成する個々のモジュール（部品）を格納しています。
Gemini の制約に適応するため、口語的なスタイルで記述され、機能ごとに分割されています。
- `personality.md`: シニカルでウィットに富んだペルソナ定義。
- `search.md`: 検索と事実確認の手順。
- `strategistic_partner.md`: ユーザーとの対等なパートナーシップの定義。
- など

### `test_prompts/`
作成した Instruction（プロンプト）の挙動を評価するためのテストケース集です。
単純な知識問題から、論理的推論、曖昧性の処理、安全性の境界テストまで、多角的な評価項目が用意されています。
- `01_simple_question.md`: 基礎知識と対象読者への適応。
- `04_ambiguity_trap.md`: 曖昧な指示への対応。
- `06_logical_quagmire.md`: 論理的矛盾や誤りの指摘。
- など

### `meta_contents/`
プロンプト設計の背景にある意図、アイデアの断片、過去のプロンプトなどを格納しています。
- `meta_intent/`: プロジェクトの目的や制約事項（Knowns & Constraints）。
- `idea_snipet/`: 外部からのインスピレーションやトリック。

### `INSTRUCTION.md`
現在アクティブな、あるいは統合されたメインの指示書です。`instruction_bricks` の内容が統合されています。

## 特徴と設計思想

このプレイグラウンドで作成されるプロンプトは、以下の特徴を持つAIを目指しています：

*   **Cynical & Witty Persona**: 表面的な楽観主義を避け、知的でウィットに富んだ、少しシニカルな観察者として振る舞います。
*   **Strategic Partner**: 単なる従順なアシスタントではなく、ユーザーの思考に挑戦し、より良い解を導き出す戦略的パートナーです。
*   **Rigorous Fact-Checking**: 自身の知識と検索結果を厳密に区別し、情報の鮮度と正確性を重視します。
*   **Structured Explanation**: 導入、詳細、結論の3ステップで構造化された説明を行います。

## 使い方

1.  **プロンプトの構築**: `instruction_bricks/` 内のモジュールを参照し、目的に応じて組み合わせるか、`INSTRUCTION.md` をベースに使用します。
2.  **テスト**: `test_prompts/` 内のシナリオを LLM に入力し、意図した挙動（ペルソナ、論理的整合性、事実確認など）が達成されているか確認します。
