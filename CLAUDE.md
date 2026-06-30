# ポートフォリオサイト — 作業メモ

## プロジェクト概要

加藤慎輔（大同大学 情報デザイン学科 技術員・グリーンウッドワーカー）の個人ポートフォリオサイト。
ファイルは `index.html` 1枚構成。GitHub: `Shinsuke75/portfolio`（Public）
**公開URL：** https://shinsuke75.github.io/portfolio/

## 現在の状態（2026-06-29 更新）

### 完了済み
- 基本レイアウト・デザイン完成（PC・スマホ対応済み）
- GitHub Pages で公開済み
- ナビ：Works / About / Apps / Blog / Contact（全英語統一）
- Contact：Instagram（@katoushinsuke75）のみ
- フッター：© 2026 Shinsuke Kato
- Works カード：クリックでモーダルポップアップ表示
- Works 内容：生木のボウル／スプーンの連作／生木の椅子（実際の説明文に更新済み）
- About 本文：更新済み（「木の声を聞きながら」、3DCAD・生成AI の段落は「——」をやめ句点区切りに）
- Writing セクション → Blog セクションに変更
- **経歴セクション追加済み**（About 下の全幅・「経歴を見る」ボタンで開閉）
  - 元データは profile.md（ユーザー提供）。プロフィール・木工歴／職歴の2カラム（1:1）
  - 年表記は年のみ（月は載せない）。「任期満了」等の注記も載せない
  - 職歴は5件すべて掲載（勝手に省略しない）
- **タイポグラフィ調整済み**
  - 所属/学科/分野：ラベルを小さく薄く、値（大同大学など）を大きく太く（縦積み）
  - .section-title の em（「考える」「作品集」等）：font-weight 800 に
- 日本語折り返し：word-break/line-break の指定はやめてデフォルトに戻した（スマホはみ出し対策）
- **Apps セクション完成**：プレースホルダー2枚を削除し、実物の「geo-ball」カード1枚に差し替え
  - geo-ball = 正二十面体ベースのジオデシック球をブラウザで設計しSTL出力する単一HTMLのWebアプリ（Three.js / Manifold-3d WASM / Web Worker）
  - 公開URL：https://shinsuke75.github.io/geo-ball/ （別GitHubリポジトリ Shinsuke75/geo-ball）
  - カードはクリックで別タブ表示・バッジ「公開中」

- **サイトのコンセプト確立（2026-06-30）**：「素材と技術を越境する、木のものづくり」
  - 生木（グリーンウッドワーク）も乾燥材の現代木工も、伝統も3DCAD・生成AIも区別せず「地続きのものづくり」として捉える、という本人の思想
  - 狙い：「こんな仕事はどうだろう?」と面白い依頼が舞い込むサイトにする（便利屋ではなく、手仕事×デジタルを行き来できる希少性を前面に）
  - ヒーローにキャッチコピー追加：「素材と技術を越境する、木のものづくり。」（「越境」を緑emで強調）
  - About 3段落目を「地続きのものづくり」の思想に差し替え済み
  - Works リード文も「素材や技法を問わず」に更新
- **Blog を Blogger 連動に（2026-06-30）**：gwood-life.blogspot.com のフィードをJSONPで読み込み、最新4件を自動表示（サムネイル画像も自動取得）。投稿すれば自動でサイトに反映される
  - インスタは公式APIが閉じていて簡単な自動連動は不可。Contactリンクのまま据え置き（必要なら個別埋め込みか外部ウィジェット）

### デザイン仕様
- **フォント：** Outfit（見出し）+ DM Sans（本文）+ Noto Sans JP（日本語）
- **カラー：** ニュートラルグレー背景（#f7f7f5）、フォレストグリーン（#2d5a27）
- **参考サイト：** robin-wood.co.uk、barnthespoon.com

### 作業上の注意（ユーザーの好み）
- 提供された文章は勝手に書き換え・追記・省略しない（特に作品説明や経歴）
- 「ダサい」の原因はメリハリ：ラベルより内容を目立たせる方針
- 変更のたびにコミット＆プッシュ → 公開URLで確認してもらう流れ

## 次回やること（TODO）

- [ ] 写真：ヒーロー右側（作業風景・手元アップなど）← ユーザーが写真を探し中
- [ ] 写真：About セクションのポートレート
- [x] Apps：geo-ball に差し替え済み（2026-06-29 完了）
- [ ] Blog：実際の記事タイトル・カテゴリに差し替え（今は仮タイトル4枚。過去に書いたブログ記事を流用できるか検討中）

## 引き継ぎ方法

新しいセッションで「CLAUDE.mdを読んで続きをお願い」と言えばOK。

---

# mokusanアプリ — 作業メモ

## プロジェクト概要

木材値札OCR＋積算計算機 Webアプリ。
GitHub: `Shinsuke75/mokusan`（Public）
**公開URL：** https://mokusan.vercel.app
**ローカル：** `C:\Users\katou\OneDrive\Desktop\mokusan-fix\`

## 現在の状態（2026-06-11 更新）

### 完了済み
- Vercel デプロイ済み・本番稼働中
- Gemini OCR: gemini-2.5-flash (v1beta) で正常動作
- Google Sheets への記録機能: 動作確認済み
- Geolocation + Nominatim による位置自動取得: 動作中
- **都道府県フォールバック修正済み**（`address.state` → `address.province` → `display_name` 正規表現の順で取得。「愛知県」など正常表示を確認）
- **Gemini 503自動リトライ実装済み**（1s/2s/4s、最大3回）

### 技術スタック
- フロントエンド: HTML/CSS/JavaScript（バニラ）
- バックエンド: Vercel Serverless Functions（Node.js ESM）
- OCR: Google Gemini 2.5 Flash API（v1beta）、前払い2000円チャージ済み（1リクエスト約0.001〜0.003円）
- データ: Google Sheets API（サービスアカウント認証）
- 位置情報: Nominatim（OpenStreetMap、APIキー不要）

### Vercel 環境変数（設定済み）
- `GEMINI_API_KEY`
- `GOOGLE_SERVICE_ACCOUNT_EMAIL`
- `GOOGLE_SERVICE_ACCOUNT_PRIVATE_KEY`
- `GOOGLE_SPREADSHEET_ID`: `11vq4iYq31GggZ8mOKaujV80ooL0-3f8D6LMCD7YEmCg`
- `GOOGLE_SHEET_NAME`: `シート1`
- `NOMINATIM_CONTACT_EMAIL`

### スプレッドシートの列構成
日付 / 都道府県 / 市区町村 / 店舗名 / 樹種 / 幅mm / 高さmm / 長さmm / 価格円 / 本数 / 立米単価(円/m³) / 備考

## 次回やること（TODO）

- [ ] フェーズ2：積算計算機モード
  - 蓄積データから樹種・都道府県を選んで平均立米単価を自動入力
  - 寸法×本数を入力 → 金額計算
  - 材料リストに追加して合計を出す
