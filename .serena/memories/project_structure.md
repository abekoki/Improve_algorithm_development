# プロジェクト構造

## ディレクトリ構成
```
drowsy_detection/
├── 00_requirements/                    # 要件定義
│   └── KPI.md                         # KPI定義
├── 01_algorithm_specification/         # アルゴリズム仕様書
│   └── AS_drowsy_detection.md         # 詳細仕様書
├── 02_specific_design/                 # 詳細設計書
│   ├── SD_drowsy_detection_python.md  # Python実装設計書
│   └── implementation_summary.md       # 実装概要
├── 03_source/                          # ソースコード
│   ├── __init__.py
│   ├── cli/                            # コマンドラインインターフェース
│   │   ├── __init__.py
│   │   └── main.py                     # CLI エントリポイント
│   ├── config/                         # 設定管理
│   │   ├── __init__.py
│   │   ├── config.py                   # 設定クラス
│   │   └── validators.py               # データ検証
│   ├── core/                           # コアアルゴリズム
│   │   ├── __init__.py
│   │   ├── drowsy_detector.py          # メインアルゴリズム
│   │   ├── eye_state.py                # 目の状態管理
│   │   └── timer.py                    # タイマー管理
│   └── utils/                          # ユーティリティ
│       ├── __init__.py
│       ├── data_processor.py           # データ前処理
│       └── logger.py                   # ログ機能
├── examples/                            # 使用例
│   ├── basic_usage.py                  # 基本的な使用方法
│   ├── video_processing.py             # 動画ストリーム処理例
│   └── README.md                       # 使用例説明
├── tests/                               # テストコード
│   ├── __init__.py
│   ├── test_config.py                  # 設定モジュールのテスト
│   ├── test_core.py                    # コアモジュールのテスト
│   ├── test_drowsy_detector.py         # メインアルゴリズムのテスト
│   └── test_integration.py             # 統合テスト
├── pyproject.toml                      # プロジェクト設定
├── uv.lock                             # 依存関係ロックファイル
├── README.md                           # プロジェクト概要
└── log.md                              # プロジェクト作業ログ
```

## モジュール依存関係
- **cli/main.py**: エントリポイント
- **core/drowsy_detector.py**: メインアルゴリズム（他の全モジュールに依存）
- **config/**: 設定管理とデータ検証
- **utils/**: ログ機能とデータ前処理
- **tests/**: 各モジュールのテスト

## パッケージ構造
- **メインパッケージ**: `03_source`
- **エントリポイント**: `03_source.cli.main:main`
- **ビルド対象**: `03_source` ディレクトリ