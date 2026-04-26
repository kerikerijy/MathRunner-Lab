---
description: 開発時の基本ルール（毎回必ず確認すること）
---

# 開発ルール（MathRunner Lab 固有）

**共通ルールに加えて、このプロジェクト固有のルールを遵守すること。**

---

## 技術スタック
- **フレームワーク**: Astro v5
- **ホスティング**: GitHub Pages (`kerikerijy.github.io/MathRunner-Lab`)
- **CI/CD**: GitHub Actions (`.github/workflows/deploy.yml`)
- **ベースパス**: `/MathRunner-Lab`

## ✅ 守ること

### アセットのパス
- 画像・動画等のアセットは `public/` に配置する
- HTML/Astro内のパス参照は `/MathRunner-Lab/ファイル名` とする（ベースパス付き）

### デプロイ
- `main` ブランチへのpushで自動デプロイされる
- dev serverの確認は `npm run dev` で行う

### メディア最適化
- 動画は H.264 + 1280px幅 + 30fps を基準とする
- 重い動画変換は1本ずつ処理する（共通ルール参照）
