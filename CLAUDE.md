# CLAUDE.md — child-playground

Claude Code がこのリポジトリで作業する際の基本コンテキストです。

---

## プロジェクト概要

**child-playground** は、子ども向けインタラクティブコンテンツを集めたウェブサイトです。  
Vercel（Hobby プラン）でホスティングし、スマホからすぐ遊べることを最優先にしています。

- **対象ユーザー**: 5歳前後の子ども（保護者がスマホで渡す想定）
- **URL**: https://child-playground.vercel.app

---

## リポジトリ構成

```
child-playground/
├── CLAUDE.md               # このファイル（非公開）
├── README.md               # リポジトリ説明（非公開）
├── vercel-deploy-guide.md  # デプロイ手順（非公開）
├── vercel.json             # Vercel設定（outputDirectory: public）
└── public/                 # ← ここだけVercelに公開される
    ├── index.html          # メニュー画面（こどもランド）
    └── bouken-meiro.html   # ぼうけん迷路（公開中）
```

`public/` 以外のファイルはVercelにデプロイされない（ホワイトリスト方式）。
コンテンツが10本を超えたら `public/games/` サブフォルダへの整理を検討。

---

## 技術スタック・制約

- **HTML / CSS / Vanilla JS のみ**。フレームワーク・ビルドツール・npm は使わない
- **外部CDN は可**（Google Fonts など）。ただし子どもが使うため表示速度を優先し最小限に
- **1コンテンツ = 1ファイル**（HTML に CSS・JS をすべてインライン）
- サーバーサイド処理なし。静的ファイルのみで完結させる

---

## デザイン・UX の原則

### 必須要件
- **スマホ縦持ち最優先**（`viewport` 設定・`100dvh` 使用）
- **iPhoneのセーフエリア対応**（`env(safe-area-inset-bottom)` を padding に適用）
- **タップターゲットは最低44px**
- 文字はひらがな中心。漢字を使う場合はルビを振る
- `touch-action: manipulation` でダブルタップズームを無効化

### スタイル方針
- 明るく・カラフルで・楽しい雰囲気
- アニメーションで生き生きとした印象を出す（CSS animation 推奨）
- フォント: `Hiragino Maru Gothic Pro` > `BIZ UDPGothic` > `Kosugi Maru`（Google Fonts可）

---

## コンテンツ追加の手順

1. `xxx.html` を作成（CSS・JS はインライン）
2. `index.html` の該当カードを `soon` → `active` に変更し、`href` を設定
3. `README.md` のコンテンツ一覧テーブルを更新

### index.html のカード切り替え

```html
<!-- BEFORE: 準備中 -->
<div class="card card-quiz soon">
  <span class="badge-soon">SOON</span>
  ...
</div>

<!-- AFTER: 公開 -->
<a href="./quiz.html" class="card card-quiz active">
  <span class="badge-new">NEW</span>
  ...
</a>
```

---

## コンテンツ一覧

| ファイル | タイトル | 状態 | 備考 |
|---|---|---|---|
| `bouken-meiro.html` | 🐶 ぼうけん めいろ | ✅ 公開中 | DFS迷路・チェックポイントで仲間を救出 |
| `tashite-goal.html` | 🔢 たして ゴール！ | ✅ 公開中 | 数字を選んでゴールの数に合わせる・Lv1〜4 |
| — | 🎨 おえかき | 🔜 準備中 | |
| `music.html` | 🎹 おんがく リズムゲーム | ✅ 公開中 | きらきらぼし・かえるのうた・メリーさんのひつじ |
| — | 🧠 クイズ | 🔜 準備中 | |
| — | 📖 おはなし | 🔜 準備中 | |

---

## デプロイ

GitHub `main` ブランチへの push で Vercel が自動デプロイ。  
特別なビルドコマンド・設定ファイルは不要。