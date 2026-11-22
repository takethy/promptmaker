# 個人用フォーク計画（プロンプト組み立て専用）

上流: Kisahime/promptmaker v6.5.0（MIT）。このフォークは個人用に分離し、
上流の更新追随はしない（必要になったら手動で取り込む）。

## 役割分担
- PromptMaker（このフォーク）: プロンプトの組み立て・推敲・採点・部品管理専用
- 画像/動画の生成実行: 既存の ComfyUI ワークフロー群が正。ここでは生成しない

## 残す機能
- Create / Builder（プリセットチップ組み立て）/ Refine / Score / Analyse
- Templates / Batch / History / Favourites / Library（パック管理）
- Characters（人物・衣装・LoRA・トリガー語のセット管理）
- Model profiles（JSON 編集）
- Providers: LM Studio 連携（ローカル LLM）

## 落とす機能（無効化または削除）
- Video maker（Wan2GP 前提のため対象外）
- Face Swap 一式（faceswap / faceblend / faceseg、opencv・onnxruntime 依存ごと）
- Wallpaper mode
- Civitai browser / import（civitai 系）
- LoRA training（kohya 連携。学習は ai-toolkit 側が正）
- Community packs の外部取得
- Live sketch / Inpaint & Regions（生成連携側の機能）
- Forge / AUTOMATIC1111 連携（ComfyUI 送信のみ残すか要判断）

## 自作で足すもの
- 検証済み語彙パック（packs/takethy-photo.json 予定）
  - カメラ3軸（写る範囲 / 高さ・傾き / 方向）＋画面占有率の数値指定
  - ポーズは印象語でなく体の部位・重心で書く部品集
  - 視線・表情の部品、撮影機材スロット（フィルム/一眼/デジカメ等）
- Qwen-Image-2.1 用モデルプロファイル（profiles 追加）
  - 自家スタック（INT8 変換モデル）向け: 自然文1段落、トリガー語の扱い、
    ネガティブは ConditioningZeroOut 前提、推奨設定 CFG 1 / 25 steps
- Characters に hrkwmn を登録（トリガー hrkwmn、LoRA hrkwmn.safetensors、推奨 0.85）

## 導入メモ
- install.bat は venv 作成 + PyPI からの依存導入のみで構成されていることを確認済み
  （PySide6 / keyring / PyYAML / opencv-headless / onnxruntime。Face Swap を落とせば後二者は不要）
- 実行は本人のタイミングで PC 側で行う
