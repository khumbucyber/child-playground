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
├── docs/specs/             # 各コンテンツの仕様書
├── specs/                  # 仕様書（一部）
│
└── public/                 # Vercel公開ディレクトリ
    ├── index.html          # メニュー画面（こどもランド）
    ├── bouken-meiro.html   # ぼうけん迷路
    ├── tashite-goal.html   # たしてゴール！
    ├── oekaki.html         # おえかき
    ├── music.html          # おんがく リズムゲーム
    ├── quiz.html           # クイズ
    ├── story.html          # おはなし
    ├── shashin.html        # しゃしん
    ├── nakamawake.html     # なかまわけ名人
    ├── marubatsu.html      # まるばつゲーム
    ├── baseball.html       # バッティング
    ├── memory-game.html    # しんけいすいじゃく
    └── okaimono.html       # おかいもの ゲーム
```

> 新しいコンテンツは `.html` ファイルを追加し、`index.html` のカードを更新するだけで拡充できます。

---

## 🎮 コンテンツ一覧

| ファイル | タイトル | 状態 | 対象年齢 |
|---|---|---|---|
| `bouken-meiro.html` | 🐶 ぼうけん めいろ | ✅ 公開中 | 4〜6歳 |
| `tashite-goal.html` | 🔢 たして ゴール！ | ✅ 公開中 | 5歳〜小1 |
| `oekaki.html` | 🎨 おえかき | ✅ 公開中 | 4〜6歳 |
| `music.html` | 🎹 おんがく リズムゲーム | ✅ 公開中 | 5歳〜小1 |
| `quiz.html` | 🧠 クイズ | ✅ 公開中 | 5歳〜小1 |
| `story.html` | 📖 おはなし | ✅ 公開中 | 4〜6歳 |
| `shashin.html` | 📷 しゃしん | ✅ 公開中 | 4〜6歳 |
| `nakamawake.html` | 🔍 なかまわけ 名人 | ✅ 公開中 | 4〜6歳 |
| `marubatsu.html` | ⭕ まるばつ ゲーム | ✅ 公開中 | 4〜6歳 |
| `baseball.html` | ⚾ バッティング | ✅ 公開中 | 5歳〜小1 |
| `memory-game.html` | 🧠 しんけいすいじゃく | ✅ 公開中 | 4〜6歳 |
| `okaimono.html` | 🪙 おかいもの ゲーム | ✅ 公開中 | 5歳〜小1 |

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