# 🚀 ぼうけん めいろ — Vercel デプロイ手順

> **前提**: GitHub アカウント・Vercel Hobby プラン登録済み

---

## STEP 1 — GitHubにリポジトリを作る

1. [github.com](https://github.com) を開き **「New repository」** をクリック
2. 設定：
   - Repository name: `bouken-meiro`（なんでもOK）
   - Public / Private: どちらでも可
   - ✅ **Add a README file** にチェック
3. **「Create repository」** をクリック

---

## STEP 2 — HTMLファイルをアップロードする

1. 作成したリポジトリのページを開く
2. **「Add file」→「Upload files」** をクリック
3. ダウンロードした `bouken-meiro.html` をドラッグ＆ドロップ
4. ファイル名を **`index.html`** に変更する
   - アップロード後、ファイル名の横の鉛筆アイコン ✏️ から変更できます
5. **「Commit changes」** をクリック

---

## STEP 3 — VercelにGitHubを連携してデプロイ

1. [vercel.com](https://vercel.com) にログイン
2. ダッシュボードの **「Add New… → Project」** をクリック
3. **「Import Git Repository」** で `bouken-meiro` を選び **「Import」**
4. 設定画面はそのまま何も変えず **「Deploy」** をクリック
5. 🎉 1〜2分でデプロイ完了！

---

## STEP 4 — URLを確認してスマホで開く

- デプロイ完了後、`https://bouken-meiro-xxxx.vercel.app` のようなURLが表示されます
- そのURLをスマホで開けばすぐ遊べます
- **QRコードを作る場合**: [qr.io](https://qr.io) などに貼り付けるだけでOK

---

## 更新方法（HTMLを修正したとき）

GitHubのリポジトリで `index.html` を開き、✏️ 鉛筆アイコンで編集 → **「Commit changes」** するだけで、**Vercelが自動的に再デプロイ**します。

---

## 独自ドメインを使いたい場合（任意）

1. Vercel のプロジェクトページ → **「Settings」→「Domains」**
2. 取得済みのドメインを入力して **「Add」**
3. 表示されるDNSレコードをドメイン会社の管理画面に設定すれば完了

---

*Hobby プランは商用利用不可ですが、個人・家族で楽しむ用途は完全無料です。*