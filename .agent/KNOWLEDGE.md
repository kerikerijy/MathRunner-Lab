# KNOWLEDGE - 学び・ナレッジ

一度ハマったことには二度とハマらない。そのための記録です。

---

## Astro / GitHub Pages

### ベースパスの設定
- `astro.config.mjs` の `base` と `site` を正しく設定しないと、GitHub Pagesでパスがずれる
- アセット参照は `/MathRunner-Lab/ファイル名` とする

### 動画のWeb最適化
- iPhoneで撮影した動画は HEVC（2732x2048, 120fps）で非常に重い
- Web配信用には H.264 + 1280px幅 + 30fps + 音声なし がベスト
- ffmpegコマンド例: `ffmpeg -i input.mp4 -vf "scale=1280:-2" -r 30 -c:v libx264 -preset medium -crf 23 -an output.mp4`
- 複数動画の結合: concat demuxer を使用（`-f concat -safe 0 -i list.txt -c copy`）
