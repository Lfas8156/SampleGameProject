# 探検家スプライト

[4面図](references/explorer_four_view_pixel_reference.png)を基準にした、前・後ろ・左・右の4方向の素材です。金に近い緑のポニーテール、額のゴーグル、口のない顔、革のリュック、探検家の服を共通にしています。待機時のつるはしは腰の前で水平、歩き・走りでは両手で胸の前に斜めに持ちます。

| 動作 | ファイル | 列×行 | シート寸法 | 再生速度 |
| --- | --- | --- | --- | --- |
| 待機 | [explorer_idle.png](explorer_idle.png) | 4×4 | 256×256 px | 4 fps |
| 歩き | [explorer_walk.png](explorer_walk.png) | 8×4 | 512×256 px | 8 fps |
| 走り | [explorer_run.png](explorer_run.png) | 8×4 | 512×256 px | 12 fps |

- 1セル64×64 px。行順は `down`（前）、`up`（後ろ）、`left`、`right`。列は時間順で、余白はありません。斜め方向の素材は含みません。
- 計80コマ・12アニメーション。色は共通22色と透明色で、アルファは0か255です。
- 足元の地面基準はセル内 `(32, 57)`。歩行・走行は左右の足が交互に出る8コマのループです。
- Godotでは最近傍フィルターを使い、`AnimatedSprite2D` の `centered = true`、`offset = Vector2(0, -25)` とします。
- 寸法・行順・パレット・再生速度は [explorer_sprites.json](explorer_sprites.json) に記録しています。

プレビューは、[待機](previews/explorer_idle_contact.png)・[歩き](previews/explorer_walk_contact.png)・[走り](previews/explorer_run_contact.png)の全コマ一覧と、各動作の再生GIF（[待機](previews/explorer_idle.gif)・[歩き](previews/explorer_walk.gif)・[走り](previews/explorer_run.gif)）です。背景と方向名はプレビューのみに含まれます。

歩き・走りは4面図を参照して作り直し、人物を抽出してから減色・位置合わせを行いました。透過画像の縁に残る色の点を除去し、64×64 pxのコマに収めています。ゲームシーンや永続的な `SpriteFrames` リソースへの組み込みは別作業です。
