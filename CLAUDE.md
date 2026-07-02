# ポートフォリオサイト — 作業メモ

## プロジェクト概要

加藤慎輔（大同大学 情報デザイン学科 技術員・グリーンウッドワーカー）の個人ポートフォリオサイト。
ファイルは `index.html` 1枚構成。GitHub: `Shinsuke75/portfolio`（Public）
**公開URL：** https://shinsuke75.github.io/portfolio/

## 現在の状態（2026-07-02 更新）

### 完了済み
- 基本レイアウト・デザイン完成（PC・スマホ対応済み）
- GitHub Pages で公開済み
- ナビ：Works / About / Blog / Contact（全英語統一。Appsは廃止しWorksに統合）
- Contact：問い合わせフォーム＋Instagram（@katoushinsuke75）
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
- **geo-ball を Works に統合（2026-06-30）**：コンセプト「越境」と矛盾するため Apps セクションを廃止し、Works グリッドに geo-ball カードを並べた
  - Works 見出しを「作品集」→「作品とツール」（ツールを緑emで強調）、リード文も「グリーンウッドワークからブラウザで動くツールまで」に更新
  - geo-ball = 正二十面体ベースのジオデシック球をブラウザで設計しSTL出力する単一HTMLのWebアプリ（Three.js / Manifold-3d WASM / Web Worker）
  - 公開URL：https://shinsuke75.github.io/geo-ball/ （別GitHubリポジトリ Shinsuke75/geo-ball）
  - 物理作品（ボウル等）はクリックでモーダル、geo-ball カードはクリックで別タブに実物が開く
  - Apps用CSS（.app-card 等）とナビの Apps リンクは削除済み

- **サイトのコンセプト確立（2026-06-30）**：「素材と技術を越境する、木のものづくり」
  - 生木（グリーンウッドワーク）も乾燥材の現代木工も、伝統も3DCAD・生成AIも区別せず「地続きのものづくり」として捉える、という本人の思想
  - 狙い：「こんな仕事はどうだろう?」と面白い依頼が舞い込むサイトにする（便利屋ではなく、手仕事×デジタルを行き来できる希少性を前面に）
  - ヒーローにキャッチコピー追加：「素材と技術を越境する、木のものづくり。」（「越境」を緑emで強調）
  - About 3段落目を「地続きのものづくり」の思想に差し替え済み
  - Works リード文も「素材や技法を問わず」に更新
- **Blog を Blogger 連動に（2026-06-30）**：gwood-life.blogspot.com のフィードをJSONPで読み込み、最新4件を自動表示（サムネイル画像も自動取得）。投稿すれば自動でサイトに反映される
  - インスタは公式APIが閉じていて簡単な自動連動は不可。Contactリンクのまま据え置き（必要なら個別埋め込みか外部ウィジェット）
- **Contact 文言＆問い合わせフォーム（2026-06-30）**
  - Contactリード文：「ワークショップのご依頼」→「『こんなことできる?』のご相談」（副業の建前で「仕事」の語は避ける）
  - 問い合わせフォーム追加（名前/メール/本文・AJAX送信・送信成否をその場表示）。インスタDMも代替として併記
  - 送信は FormSubmit（無料・登録不要）。メールアドレスは公開コードに載せず、エイリアス `https://formsubmit.co/ajax/b70abd8a69f30e0cd402c3247a5db9de` で送信（実体は katoushinsuke75@gmail.com）
  - 有効化はサンドボックスから不可（プロキシが formsubmit.co を遮断）→ 一時 activate.html を公開しユーザーのブラウザで有効化→済んだら削除。動作確認OK
  - サブミット件名は「ポートフォリオサイトからの問い合わせ」。今後は1問い合わせ＝1通
- **ヒーロー写真：AI生成トライ中断（2026-07-01）**
  - ChatGPTで「生木を削る手元」の写真を生成→3回プロンプト調整（握り方の不自然さ→修正、スプーン全体→くびれを削る場面）まで到達したが、サイトへの組み込み前に中断
  - 生成画像はチャットに貼られただけでファイルとして未保存（`/root/.claude/uploads/.../`には入っていない）→次回組み込むには**再度貼ってもらう**か**GitHubに直接アップロード**してもらう必要あり
  - Google Drive連携（MCP）がこのセッションで不安定（許可を押しても`requires approval`エラーが繰り返し発生）→ドライブ経由の受け渡しは今回断念。次回は素直にGitHub Web UIから`Add file→Upload files`でアップロードしてもらうのが確実
  - 最終的に採用したプロンプト（スプーンのくびれを削る場面）は下記「ヒーロー画像生成プロンプト」に保存
  - 本人は「実物を自分で撮影する」意向あり（AI画像はつなぎ利用の想定）。休みにボウル・スプーン・椅子の実物撮影も予定

- **デザインリデザイン反映（2026-07-02）**：ユーザー提供の design handoff zip（design_handoff_portfolio_redesign）を反映
  - ヘアライン罫線（--hairline: #d8d8d2）ベースの端正なスタイルに刷新。角丸・絵文字アイコン全廃（Instagram はインラインSVG）
  - セクション通し番号（01 Works〜04 Contact）、ヒーロー下に情報バー（Since 2002 / Daido University / Scroll）
  - Works は2列のエディトリアル調カード（3列時の空セル問題を解消）。死にリンク「すべて見る」削除
  - フォントは Outfit + Noto Sans JP に統一（DM Sans 削除）。明朝は検討の末不採用
  - モーダルのアクセシビリティ改善（role="dialog" / フォーカストラップ / Enter・Space・Esc）
  - 既存機能はすべて維持（Bloggerフィード・FormSubmitフォーム・モーダル・経歴開閉・フェードイン）。文章も原文のまま（検証済み）
  - **写真プレースホルダーは `<image-slot>` カスタム要素**（image-slot.js、デザインツール環境専用）。本番では空表示になるだけで無害
  - 写真が用意でき次第、各 `<image-slot id="...">` を `<img src="assets/〜.jpg" ...>` に置き換え、全部済んだら image-slot.js の script タグを削除（README のA案）
  - 必要な写真：hero-photo（縦長）／work-bowl・work-spoon・work-chair・work-geoball（4:3）／about-photo（3:4）／modal-bowl・modal-spoon・modal-chair（4:3）

### ヒーロー画像生成プロンプト（2026-07-01時点の最終版・スプーンのくびれ）

```
Close-up photograph of a greenwood carver's hands refining the neck of a
wooden spoon — the narrow curved transition where the rounded bowl meets
the slender handle — carved from fresh green wood, green bark still
visible on the edges. The right hand holds a small carving (sloyd) knife,
making a careful controlled cut right at the narrow waist of the spoon to
shape its graceful curve; a thin shaving peels off and curls into the air.
The bowl of the spoon is clearly visible at one end. Natural soft window
light from the side, shallow depth of field, warm authentic mood, pale
cream background with natural wood tones and a hint of forest green.
Documentary editorial style, realistic, high detail on wood grain and
blade. No face, hands only. Vertical composition, 50mm lens, f/2.0.
```

### デザイン仕様
- **フォント：** Outfit（見出し）+ DM Sans（本文）+ Noto Sans JP（日本語）
- **カラー：** ニュートラルグレー背景（#f7f7f5）、フォレストグリーン（#2d5a27）
- **参考サイト：** robin-wood.co.uk、barnthespoon.com

### 作業上の注意（ユーザーの好み）
- 提供された文章は勝手に書き換え・追記・省略しない（特に作品説明や経歴）
- 「ダサい」の原因はメリハリ：ラベルより内容を目立たせる方針
- 変更のたびにコミット＆プッシュ → 公開URLで確認してもらう流れ

## 次回やること（TODO）

- [ ] 写真：ヒーロー右側（作業風景・手元アップなど）← AI生成トライ中断。実物撮影 or 画像をGitHub直アップロードで再挑戦
- [ ] 写真：About セクションのポートレート
- [ ] 写真：Works（ボウル／スプーン／椅子）の実物写真 ← 本人が撮影予定
- [x] Apps：geo-ball に差し替え→Worksに統合済み（2026-06-30 完了）
- [x] Blog：Blogger（gwood-life）連動で自動表示に（2026-06-30 完了。仮タイトル差し替えは不要に）
- [ ] Works：「越境した仕事」をさらに追加できると新コンセプトが補強される

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
