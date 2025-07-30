# アルゴリズム開発効率化プロジェクト - 実施者向けTODO

## 📋 プロジェクト概要
- **期間**: 6週間（Phase 1-4）
- **担当者**: 開発チーム
- **目標**: AI活用によるアルゴリズム開発効率化システムの構築

## 📦 プロジェクト成果物一覧

### Phase 1: 基盤構築（Week 1-2）
- **ディレクトリ構造設計書** (`docs/directory_structure.md`)
- **4人×5回の評価データセット** (`Personal_Data/videos/`, `Personal_Data/processed_data/`)
- **基本評価ツール** (`projects/04_評価ツール/evaluation_tool.py`)
- **Git submodules設定** (`.gitmodules`)

### Phase 2: AI統合（Week 3-4）
- **AI分析エンジン** (`projects/05_検証実験/ai_analysis_engine.ipynb`)
- **CI/CDパイプライン設定** (`.github/workflows/`, `.gitlab-ci.yml`)
- **改善提案システム** (`projects/05_検証実験/improvement_suggestor.py`)
- **課題管理システム** (`projects/05_検証実験/issue_management_system.py`)
- **自動化ワークフロー設定** (`config/automation_config.json`)
- **詳細設計資料** (`projects/詳細設計資料/`)

### Phase 3: 検証実験（Week 5）
- **検証実験レポート** (`docs/verification_report.md`)
- **課題発見精度測定結果** (`results/accuracy_measurement.json`)
- **改善提案妥当性評価結果** (`results/improvement_validation.json`)
- **システム性能評価書** (`docs/system_performance_evaluation.md`)

### Phase 4: 本格運用（Week 6）
- **運用ルール・ガイドライン** (`docs/operation_guidelines.md`)
- **技術ドキュメント一式** (`docs/technical_docs/`)
- **他プロジェクト適用事例** (`docs/application_examples.md`)
- **最終プロジェクトレポート** (`docs/final_project_report.md`)

## 🗂️ ディレクトリ構造
```
Improve_algorithm_development/
├── projects/
│   ├── 01_データセット作成/
│   ├── 02_仕様書テンプレート/
│   ├── 03_実装ルール/
│   ├── 04_評価ツール/
│   ├── 05_検証実験/
│   └── 詳細設計資料/
│       ├── AI分析エンジン設計書.md
│       ├── 課題管理システム設計書.md
│       ├── CI_CDパイプライン設計書.md
│       └── システムシーケンス図.md
├── external/                           # Git submodules
├── config/
├── utils/
└── Personal_Data/                      # 別フォルダ（個人情報分離）

```

## 📅 Phase 1: 基盤構築（Week 1-2）

### Week 1: プロジェクト構造構築

#### Day 1-2: 環境セットアップ
- [ ] **Gitリポジトリの初期化**
  - 担当: プロジェクトリーダー
  - 期限: Day 1
  - 詳細: 
    ```bash
    git init
    git remote add origin <repository-url>
    ```
  - 依存: なし
  - **成果物**: 初期化されたGitリポジトリ

- [ ] **ディレクトリ構造の作成**
  - 担当: 全員
  - 期限: Day 1
  - 詳細:
    ```bash
    mkdir -p projects/{01_データセット作成,02_仕様書テンプレート,03_実装ルール,04_評価ツール,05_検証実験,詳細設計資料}
    mkdir -p external config utils
    mkdir -p ../Personal_Data/{videos,processed_data/{csv,annotations}}
    ```
  - 依存: Gitリポジトリ初期化
  - **成果物**: プロジェクトディレクトリ構造

- [ ] **Git Submodules設定**
  - 担当: プロジェクトリーダー
  - 期限: Day 2
  - 詳細:
    ```bash
    git submodule add https://github.com/your-org/eye-detection-algorithm.git external/eye_detection_algorithm
    git submodule add https://github.com/your-org/evaluation-tools.git external/evaluation_tools
    ```
  - 依存: ディレクトリ構造作成
  - **成果物**: `.gitmodules`ファイル、外部リポジトリ連携

#### Day 3-4: 設定ファイル作成
- [ ] **パス設定ファイル作成**
  - 担当: 開発者A
  - 期限: Day 3
  - 詳細: `config/paths.json`の作成
  - 依存: ディレクトリ構造作成
  - **成果物**: `config/paths.json`設定ファイル

- [ ] **.gitignore設定**
  - 担当: 開発者A
  - 期限: Day 3
  - 詳細: 個人情報と一時ファイルの除外設定
  - 依存: ディレクトリ構造作成
  - **成果物**: `.gitignore`ファイル

- [ ] **環境変数設定**
  - 担当: 開発者A
  - 期限: Day 4
  - 詳細: `.env`ファイルの作成（Git管理外）
  - 依存: パス設定ファイル作成
  - **成果物**: `.env`ファイル（テンプレート含む）

#### Day 5: 基本ツール作成
- [ ] **パス管理クラス作成**
  - 担当: 開発者A
  - 期限: Day 5
  - 詳細: `utils/path_manager.py`の実装
  - 依存: 設定ファイル作成
  - **成果物**: `utils/path_manager.py`クラス

### Week 2: データセット作成

#### Day 1-3: 評価データセット撮影
- [ ] **撮影環境セットアップ**
  - 担当: 開発者B
  - 期限: Day 1
  - 詳細: カメラ、照明、撮影台の準備
  - 依存: なし
  - **成果物**: 撮影環境セットアップ完了

- [ ] **被験者募集・調整**
  - 担当: プロジェクトリーダー
  - 期限: Day 1
  - 詳細: 4名の被験者確保
  - 依存: なし
  - **成果物**: 被験者スケジュール調整完了

- [ ] **撮影実行**
  - 担当: 開発者B
  - 期限: Day 2-3
  - 詳細: 各被験者で3s閉眼×2s開眼×5回のタスク撮影
  - 依存: 撮影環境セットアップ、被験者調整
  - **成果物**: 4人×5回の動画データ（`Personal_Data/videos/`）

#### Day 4-5: 前処理・タグ作成
- [ ] **dlib前処理スクリプト作成**
  - 担当: 開発者C
  - 期限: Day 4
  - 詳細: `projects/01_データセット作成/preprocessing_scripts/process_videos.py`
  - 依存: 撮影完了
  - **成果物**: 前処理スクリプト（`process_videos.py`）

- [ ] **開眼度・信頼度算出**
  - 担当: 開発者C
  - 期限: Day 4-5
  - 詳細: 全動画のdlib処理とCSV出力
  - 依存: 前処理スクリプト作成
  - **成果物**: 開眼度・信頼度CSVデータ（`Personal_Data/processed_data/csv/`）

- [ ] **タグデータ作成**
  - 担当: 開発者B
  - 期限: Day 5
  - 詳細: 閉眼区間の手動タグ付け
  - 依存: 前処理完了
  - **成果物**: 閉眼区間タグデータ（`Personal_Data/processed_data/annotations/`）

## 📅 Phase 2: AI統合（Week 3-4）

### Week 3: 評価ツール開発

#### Day 1-2: 基本評価フレームワーク
- [ ] **評価指標定義**
  - 担当: 開発者A
  - 期限: Day 1
  - 詳細: Precision, Recall, F1-score等の定義
  - 依存: タグデータ作成
  - **成果物**: 評価指標定義書（`docs/evaluation_metrics.md`）

- [ ] **評価ツール基本構造**
  - 担当: 開発者A
  - 期限: Day 2
  - 詳細: `projects/04_評価ツール/evaluation_framework/`の作成
  - 依存: 評価指標定義
  - **成果物**: 評価ツール基本構造（`projects/04_評価ツール/evaluation_framework/`）

#### Day 3-5: 評価ロジック実装
- [ ] **正解率計算機能**
  - 担当: 開発者A
  - 期限: Day 3
  - 詳細: アルゴリズム出力とタグの比較機能
  - 依存: 評価ツール基本構造
  - **成果物**: 正解率計算モジュール（`evaluation_framework/accuracy_calculator.py`）

- [ ] **詳細評価機能**
  - 担当: 開発者A
  - 期限: Day 4-5
  - 詳細: 時系列分析、エラー分析機能
  - 依存: 正解率計算機能
  - **成果物**: 詳細評価モジュール（`evaluation_framework/detailed_analyzer.py`）

### Week 4: AI分析システム開発

#### Day 1-2: AI分析エンジン
- [ ] **AI分析クラス作成**
  - 担当: 開発者C
  - 期限: Day 1
  - 詳細: `utils/ai_analyzer.py`の実装
  - 依存: 評価ツール完成
  - **成果物**: AI分析クラス（`utils/ai_analyzer.py`）

- [ ] **分析プロンプト設計**
  - 担当: 開発者C
  - 期限: Day 2
  - 詳細: 評価結果を分析するためのプロンプト設計
  - 依存: AI分析クラス作成
  - **成果物**: 分析プロンプトテンプレート（`config/analysis_prompts.json`）

#### Day 3-4: 改善提案システム・課題管理システム
- [ ] **改善提案エンジン**
  - 担当: 開発者C
  - 期限: Day 3
  - 詳細: `utils/improvement_suggester.py`の実装
  - 依存: AI分析エンジン
  - **成果物**: 改善提案エンジン（`utils/improvement_suggester.py`）

- [ ] **課題管理システム**
  - 担当: 開発者B
  - 期限: Day 3-4
  - 詳細: `utils/issue_management_system.py`の実装
  - 依存: 改善提案エンジン
  - **成果物**: 課題管理システム（`utils/issue_management_system.py`）

- [ ] **人間介入UI作成**
  - 担当: 開発者B
  - 期限: Day 4
  - 詳細: 優先度判断・対策対象選択のUI
  - 依存: 課題管理システム
  - **成果物**: 人間介入UI（`utils/priority_selector.py`）

#### Day 5: 自動化パイプライン
- [ ] **CI/CD設定**
  - 担当: プロジェクトリーダー
  - 期限: Day 5
  - 詳細: GitHub Actions / GitLab CIの設定
  - 依存: 全システム完成
  - **成果物**: CI/CD設定ファイル（`.github/workflows/`, `.gitlab-ci.yml`）

## 📅 Phase 3: 検証実験（Week 5）

### Day 1-3: サンプルアルゴリズム設計・実装
- [ ] **仕様書テンプレート作成**
  - 担当: 開発者A
  - 期限: Day 1
  - 詳細: `projects/02_仕様書テンプレート/algorithm_template.md`
  - 依存: なし
  - **成果物**: アルゴリズム仕様書テンプレート（`projects/02_仕様書テンプレート/algorithm_template.md`）

- [ ] **実装ルール作成**
  - 担当: 開発者A
  - 期限: Day 1
  - 詳細: `projects/03_実装ルール/coding_standards.md`
  - 依存: なし
  - **成果物**: 実装ルール・コーディング規約（`projects/03_実装ルール/coding_standards.md`）

- [ ] **サンプルアルゴリズム設計**
  - 担当: 開発者B
  - 期限: Day 2
  - 詳細: 閉眼検出アルゴリズムの詳細設計（意図的に課題を含む設計）
  - 依存: 仕様書テンプレート、実装ルール
  - **成果物**: サンプルアルゴリズム設計書（`projects/05_検証実験/sample_algorithm_design.md`）

- [ ] **サンプルアルゴリズム実装**
  - 担当: 開発者B
  - 期限: Day 3
  - 詳細: 設計書に基づくアルゴリズム実装（意図的に課題を含む実装）
  - 依存: サンプルアルゴリズム設計
  - **成果物**: サンプルアルゴリズム（`projects/05_検証実験/sample_algorithm.py`）

### Day 3-4: 検証実験実行
- [ ] **自動評価実行**
  - 担当: 全員
  - 期限: Day 3
  - 詳細: サンプルアルゴリズムの評価実行
  - 依存: サンプルアルゴリズム実装
  - **成果物**: 評価実行結果（`results/evaluation_results.json`）

- [ ] **AI分析実行**
  - 担当: 開発者C
  - 期限: Day 3-4
  - 詳細: 評価結果のAI分析
  - 依存: 自動評価実行
  - **成果物**: AI分析レポート（`results/ai_analysis_report.ipynb`）

- [ ] **改善提案生成**
  - 担当: 開発者C
  - 期限: Day 4
  - 詳細: AIによる改善案提案
  - 依存: AI分析実行
  - **成果物**: 改善提案レポート（`results/improvement_suggestions.md`）

### Day 5: 結果評価
- [ ] **課題発見精度測定**
  - 担当: プロジェクトリーダー
  - 期限: Day 5
  - 詳細: 仕込んだ課題の何%を発見できたか測定
  - 依存: 改善提案生成
  - **成果物**: 課題発見精度測定結果（`results/accuracy_measurement.json`）

- [ ] **改善提案妥当性評価**
  - 担当: 全員
  - 期限: Day 5
  - 詳細: 提案された改善案の実装可能性評価
  - 依存: 改善提案生成
  - **成果物**: 改善提案妥当性評価結果（`results/improvement_validation.json`）

## 📅 Phase 4: 本格運用（Week 6）

### Day 1-2: 運用準備
- [ ] **運用ルール作成**
  - 担当: プロジェクトリーダー
  - 期限: Day 1
  - 詳細: 日常運用のルール・手順書作成
  - 依存: 検証実験完了
  - **成果物**: 運用ルール・ガイドライン（`docs/operation_guidelines.md`）

- [ ] **ドキュメント整備**
  - 担当: 全員
  - 期限: Day 2
  - 詳細: README、API仕様書、運用マニュアル
  - 依存: 運用ルール作成
  - **成果物**: 技術ドキュメント一式（`docs/technical_docs/`）

### Day 3-5: 他プロジェクト適用
- [ ] **他アルゴリズムプロジェクト選定**
  - 担当: プロジェクトリーダー
  - 期限: Day 3
  - 詳細: 適用対象プロジェクトの選定
  - 依存: ドキュメント整備

- [ ] **適用実験**
  - 担当: 全員
  - 期限: Day 4-5
  - 詳細: 選定プロジェクトでの適用実験
  - 依存: 他プロジェクト選定

## 🎯 成功指標チェックリスト

### 技術指標
- [ ] 課題発見精度: 90%以上
- [ ] 改善提案妥当性: 70%以上
- [ ] 処理時間: 評価結果生成まで30分以内
- [ ] システム稼働率: 99%以上
- [ ] 課題管理効率: 75%削減（人間判断は維持）

### 運用指標
- [ ] 開発者満足度: 80%以上
- [ ] 導入プロジェクト数: 2以上
- [ ] ドキュメント完成度: 100%
- [ ] セキュリティ要件: 100%達成

## 🔧 技術的注意事項

### 個人情報管理
- 動画データは必ず`Personal_Data/`フォルダに保存
- `.gitignore`で個人情報を確実に除外
- アクセス権限の適切な設定

### コード品質
- 全てのコードに日本語コメントを記載
- モジュール化を徹底（再利用性を考慮）
- エラーハンドリングの実装

### AI分析の最適化
- コンテキストウィンドウ制限への対応
- 分析結果の構造化
- プロンプトの継続的改善

### 人間介入ポイント
- **改善提案確認**: 改善提案レポートの確認・必要に応じて介入
- **生成課題確認**: AI生成課題の確認・必要に応じて調整
- **優先度判断**: 抽出された課題の優先度判断
- **対策対象選択**: どの課題を対策対象とするかの選択
- **修正実装**: 実際のコード修正
- **課題クローズ**: 効果測定後の課題完了判断

### 自動処理範囲
- **評価・分析**: 完全自動化（人間介入不要）
- **改善提案以降**: 人間の確認・介入が必要
- **夜間処理**: 評価・分析までは自動で処理を継続

## 📞 連絡体制

### 定例会議
- **日次**: 15分の進捗確認（毎日17:00）
- **週次**: 1時間の詳細レビュー（毎週金曜日14:00）
- **月次**: 成果報告・次月計画（月末）

### 緊急連絡
- **技術的問題**: 開発者C（AI関連）、開発者A（システム関連）
- **スケジュール調整**: プロジェクトリーダー
- **外部連絡**: プロジェクトリーダー

## 📝 ログ記録

### 記録項目
- 作業内容と結果
- 発生した問題と解決方法
- 改善点・アイデア
- 次回への引き継ぎ事項

### 記録方法
- `log.md`に日付付きで記録
- 重要な決定事項は別途ドキュメント化
- コード変更はGitコミットメッセージで詳細記録

---

**最終更新**: 2024-07-25
**作成者**: プロジェクトチーム
**承認者**: プロジェクトリーダー
**バージョン**: 1.0 