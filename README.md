# 🎪 child-playground

子ども向けのインタラクティブコンテンツを集めたウェブサイトです。  
Vercel でホスティングし、スマホからいつでも遊べます。

🔗 **サイト**: https://child-playground.vercel.app

---

## 📂 ファイル構成

```
child-playground/
│
├── vercel.json             # Vercel設定（outputDirectory: public）
├── README.md
├── CLAUDE.md
│
└── public/                 # Vercel公開ディレクトリ
    ├── index.html          # メニュー画面（こどもランド）
    ├── bouken-meiro.html   # ぼうけん迷路
    ├── tashite-goal.html   # たしてゴール！
    └── music.html          # おんがく リズムゲーム
```

> 新しいコンテンツは `.html` ファイルを追加し、`index.html` のカードを更新するだけで拡充できます。

---

## 🎮 コンテンツ一覧

| ファイル | タイトル | 状態 | 対象年齢 |
|---|---|---|---|
| `bouken-meiro.html` | 🐶 ぼうけん めいろ | ✅ 公開中 | 4〜6歳 |
| `tashite-goal.html` | 🔢 たして ゴール！ | ✅ 公開中 | 5歳〜小1 |
| *(未作成)* | 🎨 おえかき | 🔜 準備中 | — |
| `music.html` | 🎹 おんがく | ✅ 公開中 | 5歳〜小1 |
| *(未作成)* | 🧠 クイズ | 🔜 準備中 | — |
| *(未作成)* | 📖 おはなし | 🔜 準備中 | — |

---

## 🚀 新しいコンテンツの追加手順

1. `.html` ファイルをリポジトリに追加する（例: `quiz.html`）
2. `index.html` の `<main>` 内にある `soon` カードを以下のように更新する：

```html
<!-- BEFORE（準備中） -->
<div class="card card-quiz soon">
  <span class="badge-soon">SOON</span>
  ...
</div>

<!-- AFTER（公開） -->
<a href="./quiz.html" class="card card-quiz active">
  <span class="badge-new">NEW</span>
  ...
</a>
```

3. GitHub にコミット → Vercel が自動デプロイ ✅

---

## 🛠 技術スタック

- **HTML / CSS / Vanilla JS** のみ（フレームワーク不使用）
- **Vercel** でホスティング（Hobby プラン・無料）
- 外部依存なし・オフライン動作可

---

## 📝 ライセンス

家族利用のプライベートプロジェクトです。