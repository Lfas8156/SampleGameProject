# 開発ガイド

このリポジトリは Godot 4.7 を使用する 2D アクション RPG プロジェクトです。

## フォルダ構成

- `assets/player/`: プレイヤーの画像・アニメーション・音声素材。
- `assets/enemies/`: 敵の画像・アニメーション・音声素材。
- `assets/items/`: アイテムの画像などの素材。
- `scenes/player/`: プレイヤーのシーン。
- `scenes/enemies/`: 敵のシーン。
- `scenes/ui/`: HUD、メニュー、インベントリなどの UI シーン。
- `scripts/player/`: プレイヤーの操作・行動に関するスクリプト。
- `scripts/enemies/`: 敵の行動・AI に関するスクリプト。
- `scripts/systems/`: 戦闘、アイテム管理、セーブなどの共通システム。
- `data/`: ステータスやアイテム定義などのデータ・Resource。

## 実装ルール

- GDScript を基本とし、インデントにはタブを使用する。
- ファイル・フォルダ・変数・関数名には `snake_case`、`class_name` には `PascalCase` を使用する。
- Godot のリソース参照には `res://` を使用する。
- シーンとスクリプトは役割ごとに分割し、共通処理は `scripts/systems/` に置く。
- 素材を追加・作成する際は `ART_STYLE.md` を確認する。
- 空フォルダには `.gitkeep` を置く。実ファイルを追加したら、そのフォルダの `.gitkeep` を削除してよい。
- `.godot/` などの生成キャッシュはコミットしない。
- 既存の変更を保持し、依頼と無関係な変更は避ける。

## 動作確認

- Godot 4.7 でプロジェクトを開き、インポートやスクリプトのエラーを確認する。
- ヘッドレスでのインポート確認: `godot --headless --path . --editor --import`。
- `godot` が 4.7 を指すことを `godot --version` で確認する。
- このクラウド環境では `/workspace/tools/godot/4.7/Godot_v4.7-stable_linux.x86_64` を使用できる。
- メインシーンを作成・設定した後は、変更に関連する移動・攻撃・UI などを実際に確認する。
- 実行した確認と未確認の項目を区別して報告する。
