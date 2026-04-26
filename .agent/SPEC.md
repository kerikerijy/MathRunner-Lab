# SPEC - サイト仕様

このドキュメントは MathRunner Lab サイトの確定済み仕様をまとめたものです。

---

## 1. サイト概要

- **サイト名**: MathRunner Lab
- **URL**: https://kerikerijy.github.io/MathRunner-Lab
- **目的**: 開発アプリのポートフォリオ＆ランディングページ
- **技術**: Astro v5 + GitHub Pages
- **リポジトリ**: https://github.com/kerikerijy/MathRunner-Lab

---

## 2. ページ構成

### トップページ (`/`)
- アプリ一覧（6本のアプリカード）
- お問い合わせフォーム（GAS連携）

### 座席ますたー マニュアル (`/seating-master-manual`)
- URL: `/MathRunner-Lab/seating-master-manual`
- テーマ: 黒板グリーン＆木目調ブラウン（アプリのブランディングに合わせた独自配色）
- アプリアイコン: `sm_app_icon.png`
- 背景画像: `bg_classroom_vivid_wide.png`

#### コンテンツ構成
1. **主な機能**（4セクション）
   - クラス＆生徒管理 — スクショギャラリー（5枚、横スクロール+矢印ナビ+ドット）
   - 座席表のレイアウト・履歴保存 — 動画 `sm_layout.mp4`
   - 席替え＆指名機能 — 動画 `sm_shuffle.mp4`, `sm_roulette.mp4`
   - 出欠管理・カレンダー・PDF出力 — 動画 `sm_attendance.mp4`
2. **プラン比較表**（無料 / PRO / ULTRA）
3. **教育機関(MDM)でのご利用**
4. **お問い合わせ**

#### メディアアセット
| ファイル | サイズ | 内容 |
|---|---|---|
| `sm_layout.mp4` | 2.1MB | レイアウト編 |
| `sm_shuffle.mp4` | 2.3MB | 席替え演出（2クリップ結合） |
| `sm_roulette.mp4` | 1.2MB | 指名演出 |
| `sm_attendance.mp4` | 3.5MB | 出欠管理（2クリップ結合） |
| `screenshot_class1〜5.png` | 各200KB前後 | クラス管理のスクリーンショット |

---

## 3. お問い合わせフォーム

- **バックエンド**: Google Apps Script（Webアプリ）
- **データ保存先**: Googleスプレッドシート「MathRunner Lab 問い合わせ」
- **通知**: Gmail（問い合わせ受信時に自動メール送信）
- **フォーム項目**:
  | 項目 | フィールド名 | 必須 |
  |---|---|---|
  | お名前 | `name` | 任意 |
  | メールアドレス | `email` | 必須 |
  | 対象アプリ | `app` | 必須 |
  | お問い合わせ種別 | `category` | 必須 |
  | お問い合わせ内容 | `message` | 必須 |
- **GASデプロイURL**: `https://script.google.com/macros/s/AKfycbw8.../exec`
- **技術詳細**: fetch (mode: no-cors) → GAS doPost → スプレッドシート追記 + MailApp.sendEmail

---

## 4. デプロイ設定

- **ブランチ**: `main`
- **ベースパス**: `/MathRunner-Lab`
- **CI/CD**: `.github/workflows/deploy.yml`（GitHub Actions）
- `main` へのpushで自動ビルド＆デプロイ
