# 探検家スプライト

基準は [4面図](references/explorer_four_view_pixel_reference.png) の `8c95ae4` 版です。
記入シートの追加指定に従い、待機時はつるはしを腰の前で水平に、歩き・走りでは両手で胸の前に斜めに保持します。
ポーチなどの未指定の細部は基準画像に合わせて簡略化しています。

## 本番サイズのPNG

| 動作 | ファイル | 1方向の枚数 | シート寸法 | 初期fps |
| --- | --- | --- | --- | --- |
| 待機 | [explorer_idle.png](explorer_idle.png) | 4 | 192×384 px | 4 |
| 歩き | [explorer_walk.png](explorer_walk.png) | 8 | 384×384 px | 8 |
| 走り | [explorer_run.png](explorer_run.png) | 8 | 384×384 px | 12 |

- 1セル48×48 px、8方向、合計160コマ・24アニメーション。
- 横に時間順のコマ、縦に方向を配置。余白・間隔は0 px。
- 行順は `down`、`down_left`、`left`、`up_left`、`up`、`up_right`、`right`、`down_right`。
- 共通16色と透明色を使用。アルファは0または255で、ぼかしなし。
- 足元の地面基準はセル内 `(24, 42)`。走りの空中位相では足が少し上がります。
- 頭身は2頭身を基準とし、キャラクターは約36 px高。つるはしや髪もセル内に収めています。
- Godotでは最近傍フィルターを使い、`AnimatedSprite2D` の `centered = true`、`offset = Vector2(0, -18)` とします。
- 詳細な寸法・行順・パレット・fpsは [explorer_sprites.json](explorer_sprites.json) に記録しています。

## 確認用プレビュー

- 待機: [再生GIF](previews/explorer_idle.gif) ／ [全コマ一覧](previews/explorer_idle_contact.png)
- 歩き: [再生GIF](previews/explorer_walk.gif) ／ [全コマ一覧](previews/explorer_walk_contact.png)
- 走り: [再生GIF](previews/explorer_run.gif) ／ [全コマ一覧](previews/explorer_run_contact.png)

プレビューは4倍の最近傍拡大です。背景と方向名は確認用画像だけに含まれます。
GIFの時間単位に合わせて再生間隔を丸めているため、正確なfpsはJSONの値を使用してください。

## 制作・検証

画像生成後、人物の輪郭から各コマを抽出し、方向ごとに同じ倍率で縮小、共通パレットへの減色、透明部分のノイズ除去、腰と足元を基準にした位置合わせを行いました。歩きの左後ろと待機の右前は個別に再生成しています。

- PNGの寸法、セル数、16色、二値の透過、セル境界へのはみ出しがないことを検査済み。
- 方向ごとに待機4枚、歩き8枚、走り8枚の異なるコマがあることを確認済み。
- 全コマ一覧で方向と切り出しを目視確認済み。
- Godot 4.7で3枚のテクスチャを読み込み、160領域の切り出しを確認。
- 一時的な検証用SpriteFramesで全24アニメーションを再生し、全コマの通過と各2回以上のループを確認済み。

今回の成果物は素材です。ゲームシーンや永続的なSpriteFramesリソースには組み込んでいません。実際の移動速度に合わせた足運びの調整や、ゲーム画面での見た目は組み込み時に確認してください。
