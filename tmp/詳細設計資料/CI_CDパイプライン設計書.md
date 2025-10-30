# CI/CDパイプライン設計書

> 現状（2025-08-20）: 本設計に対応するCI/CD実装（`.github/workflows/`）は未作成です。ローカル実行はWindows + uv（`.venv`固定）を前提に整備中で、CIは`drowsy_detection`のテスト実行から段階導入します。

## 📋 概要

CI/CDパイプラインは、コードの変更を自動的に検知し、評価・分析・改善提案を自動実行するシステムです。

## 🎯 機能要件

### 主要機能
1. **自動トリガー**: Git Push時の自動実行
2. **評価実行**: アルゴリズムの自動評価
3. **AI分析**: 評価結果の自動分析
4. **改善提案**: AIによる改善案の自動生成
5. **結果通知**: 開発者への結果通知

### 実行フロー
```
Git Push → 自動評価実行 → AI分析 → 改善提案生成 → 結果通知
```

## 🏗️ システム構成

### 使用技術
- **CI/CD**: GitHub Actions / GitLab CI（現状は未実装）
- **パッケージ管理**: uv（ローカルは`.venv`固定）
- **コンテナ**: Docker（将来導入）
- **実行環境**: Python 3.10+
- **通知**: Slack / Email / Webhook（将来導入）
- **セルフホストランナー**: ローカル環境での評価実行（将来導入）

### パイプライン構成
```
.github/workflows/
├── evaluation.yml        # 評価実行パイプライン
├── analysis.yml         # AI分析パイプライン
├── notification.yml     # 通知パイプライン
└── templates/
    ├── evaluation.yml   # 評価テンプレート
    └── analysis.yml     # 分析テンプレート
```

## 🔄 パイプライン詳細

### 1. 評価実行パイプライン

#### トリガー条件
- プルリクエスト作成時
- メインブランチへのマージ時
- 手動実行（workflow_dispatch）

#### 実行ステップ
```yaml
name: Algorithm Evaluation
on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  evaluate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.9'
      - name: Install uv
        run: |
          curl -LsSf https://astral.sh/uv/install.sh | sh
      - name: Sync dependencies (uv)
        run: |
          uv venv .venv
          uv sync
      - name: Run evaluation
        run: |
          python evaluation_engine.py
      - name: Upload results
        uses: actions/upload-artifact@v3
        with:
          name: evaluation-results
          path: results/
```

### 2. AI分析パイプライン

#### 実行条件
- 評価実行完了後
- 評価結果の存在確認

#### 実行ステップ
```yaml
name: AI Analysis
needs: evaluate
runs-on: ubuntu-latest
steps:
  - uses: actions/checkout@v3
  - name: Download evaluation results
    uses: actions/download-artifact@v3
    with:
      name: evaluation-results
  - name: Run AI analysis (placeholder)
    run: |
      echo "AI analysis engine is not yet implemented."
  - name: Generate report
    run: |
      python report_generator.py
  - name: Upload analysis report
    uses: actions/upload-artifact@v3
    with:
      name: analysis-report
      path: reports/
```

### 3. 通知パイプライン

#### 実行条件
- AI分析完了後
- 改善提案の生成完了

#### 通知内容
- 評価結果のサマリ
- 主要課題の要約
- 改善提案の一覧
- レポートへのリンク

#### 通知内容例
```json
{
  "status": "success",
  "timestamp": "2024-07-25T10:30:00Z",
  "pipeline": "algorithm-evaluation",
  "results": {
    "accuracy": 85.2,
    "speed": 120,
    "robustness": 92.1
  },
  "improvements": [
    "処理速度を15ms改善",
    "エラーハンドリング強化"
  ],
  "details": {
    "evaluation_count": 20,
    "test_duration": "45 minutes",
    "memory_usage": "512MB",
    "cpu_usage": "75%"
  },
  "next_steps": [
    "人間による改善提案確認",
    "優先度判断・対策対象選択",
    "課題管理システムでの追跡開始"
  ]
}
```

## 📊 評価実行エンジン

### 評価項目
1. **精度評価**
   - Precision, Recall, F1-score
   - 混同行列
   - ROC曲線・PR曲線

2. **性能評価**
   - 処理速度
   - メモリ使用量
   - CPU使用率

3. **品質評価**
   - エラー率
   - 安定性
   - ロバスト性

### 評価データ
- **テストデータ**: 4人×5回のタスクデータ
- **評価指標**: 標準的な機械学習指標
- **出力形式**: JSON / CSV

## 🤖 AI分析エンジン

### 分析内容
1. **結果分析**
   - 評価結果の詳細分析
   - 課題の特定
   - 改善点の抽出

2. **改善提案**
   - 具体的な改善案
   - 優先度の設定
   - 実装方法の提案

3. **レポート生成**
   - Jupyter Notebook形式
   - 可視化チャート
   - 詳細な分析結果

## 📈 結果管理

### アーティファクト管理
- **評価結果**: 実行日時付きで保存（原則 `DataWareHouse/` 配下）
- **分析レポート**: Jupyter Notebook形式（原則 `DataWareHouse/` 配下）
- **改善提案**: JSON形式で構造化（原則 `DataWareHouse/` 配下）

### 履歴管理
- **実行履歴**: 全実行の履歴を `DataWareHouse/` に集約保存
- **結果比較**: 修正前後の比較を `DataWareHouse/` 配下のバージョン別ディレクトリで保持
- **トレンド分析**: 長期的な改善傾向を `DataWareHouse/` 配下の `reports/` 等に集積

## 🔧 設定項目

### 環境変数
```yaml
# セキュリティ設定
SECURITY_SCAN_ENABLED: true
VULNERABILITY_CHECK: true
SECRET_SCANNING: true

# 通知設定
SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
EMAIL_NOTIFICATION: ${{ secrets.EMAIL_NOTIFICATION }}

# AI分析設定
OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
ANALYSIS_DEPTH: "detailed"
IMPROVEMENT_COUNT: 10
```
env:
  OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
  SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
  EVALUATION_DATA_PATH: ./data/
  REPORT_OUTPUT_PATH: ./reports/
```

### 実行条件
- **評価実行**: コード変更時
- **AI分析**: 評価結果の変化時
- **通知**: 重要な改善提案がある時

### カスタマイズ項目
- 評価項目の追加・削除
- 分析深度の調整
- 通知条件の変更
- 実行スケジュールの設定

## 📱 通知システム

### 通知チャネル
1. **Slack**
   - リアルタイム通知
   - チャンネル別の通知設定
   - リッチなメッセージ形式

2. **Email**
   - 日次サマリレポート
   - 重要な改善提案の通知
   - 管理者向けレポート

3. **Webhook**
   - 外部システムとの連携
   - カスタム通知の実装
   - API連携

### 通知内容
```json
{
  "evaluation_summary": {
    "precision": 0.85,
    "recall": 0.78,
    "f1_score": 0.81
  },
  "key_issues": [
    {
      "id": "ISSUE-001",
      "priority": "High",
      "description": "パフォーマンス改善が必要"
    }
  ],
  "improvement_suggestions": [
    {
      "id": "SUGGESTION-001",
      "impact": "High",
      "effort": "Medium",
      "description": "アルゴリズムの最適化"
    }
  ],
  "report_url": "https://github.com/.../reports/analysis_20250724.ipynb"
}
```

## 🔒 セキュリティ

### アクセス制御
- **シークレット管理**: GitHub Secrets / GitLab Variables
- **権限管理**: 最小権限の原則
- **監査ログ**: 実行履歴の記録

### データ保護
- **個人情報**: 評価データからの除外
- **暗号化**: 機密データの暗号化
- **アクセス制限**: 結果へのアクセス制御

## 📝 運用ルール

### 実行ルール
1. **自動実行**: コード変更時の自動実行
2. **手動実行**: 必要に応じて手動実行可能
3. **スケジュール実行**: 定期実行の設定

### エラーハンドリング
1. **再実行**: 一時的エラーの自動再実行
2. **通知**: エラー発生時の通知
3. **ロールバック**: 問題発生時のロールバック

### 監視・メンテナンス
1. **実行状況監視**: パイプラインの実行状況
2. **性能監視**: 実行時間・リソース使用量
3. **定期メンテナンス**: 依存関係の更新

## 📝 更新履歴

- **2025-07-25**: 初版作成
- **バージョン**: 1.0 