# 技術スタック

## プログラミング言語
- **Python**: 3.10以上
- **将来計画**: C++移植（Eigen + OpenCV使用予定）

## 主要ライブラリ・フレームワーク
- **データ処理**: NumPy >= 1.21.0
- **データ検証**: Pydantic >= 1.10.0
- **画像処理**: OpenCV (opencv-python)
- **顔検出**: dlib

## 開発・テストツール
- **パッケージ管理**: uv
- **テスト**: pytest >= 7.0.0, pytest-cov >= 4.0.0
- **コード品質**: 
  - Black >= 22.0.0 (フォーマット)
  - isort >= 5.10.0 (import整理)
  - flake8 >= 5.0.0 (lint)
  - mypy >= 1.0.0 (型チェック)

## ビルドシステム
- **ビルドバックエンド**: hatchling
- **パッケージ形式**: wheel

## 設定・ログ
- **設定管理**: Pydantic BaseModel
- **ログ**: Python標準logging
- **設定ファイル**: JSON形式

## パフォーマンス要件
- **処理速度**: 30fps以上（33ms以下）
- **メモリ使用量**: 100MB以下
- **CPU使用率**: Raspberry Pi 4で20%以下