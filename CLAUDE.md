# CLAUDE.md — child-playground

Claude Code がこのリポジトリで作業する際の基本コンテキストです。

---

## 開発ルール

### 仕様駆動開発

- コードを書く前に仕様書を作成する
- 変更が発生した場合も、先に仕様書を更新してからコードを変更する。やむを得ない場合でも、必ず後から仕様書に反映する
- 仕様書とコードのずれに敏感になること。実装が仕様書と乖離していると気づいたら即座に指摘・修正する

### 企画フロー

- 「企画したい」と言われたら、まず企画内容を人間に提案し、内容を合意してから開発作業を始める

### 追加変更要求の対応

- 追加の変更要求を受けた場合、対応中のPRがクローズされていないかをチェックする
  - **オープン**: そのまま同じPRで対応に入る
  - **クローズ済み**: 別セッションでの対応を人間にお勧めする

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
| `oekaki.html` | 🎨 おえかき | ✅ 公開中 | 自由お絵かき |
| `music.html` | 🎹 おんがく リズムゲーム | ✅ 公開中 | きらきらぼし・かえるのうた・メリーさんのひつじ |
| `quiz.html` | 🧠 クイズ | ✅ 公開中 | |
| `story.html` | 📖 おはなし | ✅ 公開中 | 選択肢で変わるストーリー |
| `shashin.html` | 📷 しゃしん | ✅ 公開中 | |
| `nakamawake.html` | 🔍 なかまわけ 名人 | ✅ 公開中 | なかまを見つけるグルーピングゲーム |
| `marubatsu.html` | ⭕ まるばつ ゲーム | ✅ 公開中 | |
| `baseball.html` | ⚾ バッティング | ✅ 公開中 | タイミングゲーム |
| `memory-game.html` | 🧠 しんけいすいじゃく | ✅ 公開中 | 4レベル |
| `okaimono.html` | 🪙 おかいもの | ✅ 公開中 | コインを選んでぴったり支払う・Lv1〜4 |

---

## デプロイ

GitHub `main` ブランチへの push で Vercel が自動デプロイ。  
特別なビルドコマンド・設定ファイルは不要。