# 推奨コマンド

## 開発環境セットアップ
```bash
# 仮想環境作成・アクティベート
uv venv
uv pip install -e .

# 開発依存関係インストール
uv pip install -e ".[dev]"
```

## テスト実行
```bash
# 全テスト実行
pytest tests/

# 特定のテストファイル実行
pytest tests/test_drowsy_detector.py

# カバレッジ付きテスト
pytest tests/ --cov=03_source

# 詳細出力
pytest tests/ -v
```

## コード品質チェック
```bash
# コードフォーマット
black 03_source/ tests/ examples/

# import整理
isort 03_source/ tests/ examples/

# lintチェック
flake8 03_source/ tests/ examples/

# 型チェック
mypy 03_source/
```

## パッケージ管理
```bash
# 依存関係更新
uv pip install --upgrade package_name

# パッケージビルド
uv build

# パッケージインストール
uv pip install .
```

## 実行・テスト
```bash
# 基本使用例実行
python examples/basic_usage.py

# CLI実行
python -m 03_source.cli.main --input test_input.json

# サンプルファイル生成
python -m 03_source.cli.main --create-sample-config config.json
python -m 03_source.cli.main --create-sample-input input.json --frames 100
```

## 開発・デバッグ
```bash
# ログレベル変更
export PYTHONPATH=.

# 対話的テスト
python -c "from 03_source.core.drowsy_detector import DrowsyDetector; print('Import successful')"

# パフォーマンスプロファイリング
python -m cProfile -o profile.stats examples/basic_usage.py
```

## Git操作
```bash
# 変更確認
git status
git diff

# コミット
git add .
git commit -m "feat: 新機能追加"

# プッシュ
git push origin main
```

## システムコマンド（Windows）
```bash
# ディレクトリ一覧
dir
dir /s

# ファイル検索
findstr "pattern" *.py

# パス設定
set PYTHONPATH=%PYTHONPATH%;.

# プロセス確認
tasklist | findstr python
```