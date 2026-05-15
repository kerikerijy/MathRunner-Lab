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

### GAS（Google Apps Script）でのフォーム連携
- GitHub Pages（静的サイト）からフォーム送信するバックエンドとしてGASが使える
- GAS WebアプリはCORSヘッダーを自分で設定できないため、fetch時は `mode: 'no-cors'` を使用
- opaqueレスポンスが返ればネットワーク的には成功と見なす（レスポンスbodyは読めない）
- `MailApp.sendEmail()` で通知メール、`SpreadsheetApp` でデータ蓄積
- デプロイ時「アクセスできるユーザー」を「全員」にしないと外部サイトから送信できない

### 複数ギャラリーのJS汎用化
- ギャラリースクリプトはIDハードコードではなく、`document.querySelectorAll('.screenshot-gallery').forEach(initGallery)` で汎用化すると、同一ページ内に複数ギャラリーを配置できる

