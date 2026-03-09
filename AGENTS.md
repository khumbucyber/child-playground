# AGENTS.md — マルチエージェント実装ガイド

Claude Code のサブエージェント機能を使って、3本のゲームを**並行実装**するための指示書です。

---

## アーキテクチャ

```
オーケストレーター（あなたが操作する Claude Code セッション）
│
├── サブエージェント A → oekaki.html を実装
├── サブエージェント B → quiz.html を実装
└── サブエージェント C → shashin.html を実装
          ↓ 全完了後
オーケストレーターが index.html を更新
```

各サブエージェントは**独立したファイルのみ**を触るので競合しません。

---

## 事前確認

```bash
# リポジトリのルートにいることを確認
ls
# → CLAUDE.md  README.md  index.html  bouken-meiro.html  specs/  AGENTS.md が見えること
```

---

## オーケストレーターへの指示（Claude Code に貼る）

以下をそのまま Claude Code のプロンプトに貼り付けてください。

```
以下の3つのタスクをサブエージェントで並行実行してください。

## タスク A — おえかき
specs/oekaki.md の仕様書を読み、oekaki.html を実装してください。
実装後、ファイルが正しく作成されたことを確認してください。

## タスク B — クイズ
specs/quiz.md の仕様書を読み、quiz.html を実装してください。
実装後、ファイルが正しく作成されたことを確認してください。

## タスク C — しゃしんきおくゲーム
specs/shashin.md の仕様書を読み、shashin.html を実装してください。
実装後、ファイルが正しく作成されたことを確認してください。

## 共通の制約（全エージェント共通）
- CLAUDE.md を必ず参照してスタイル・技術制約に従うこと
- HTML / CSS / Vanilla JS のみ（1ファイル完結）
- スマホ縦持ち最適化（100dvh・safe-area対応）
- タップターゲット最低44px
- 文字はひらがな中心

## 全タスク完了後（オーケストレーターが実施）
3ファイルの実装完了後、index.html の以下のカードを更新してください：
- 🎨 おえかき: soon → active、href="./oekaki.html"、badge を NEW に
- 🧠 クイズ:   soon → active、href="./quiz.html"、  badge を NEW に
- 📷 しゃしん: soon → active、href="./shashin.html"、badge を NEW に
  （index.html にしゃしんカードがない場合は card-draw の空きカードを流用して追加）
```

---

## 各サブエージェントの責任範囲

| エージェント | 触るファイル | 触らないファイル |
|---|---|---|
| A (おえかき) | `oekaki.html` のみ | 他すべて |
| B (クイズ) | `quiz.html` のみ | 他すべて |
| C (しゃしん) | `shashin.html` のみ | 他すべて |
| オーケストレーター | `index.html` のみ | 各ゲームHTML |

---

## 完了チェックリスト

サブエージェント完了後、オーケストレーターは以下を確認してください。

- [ ] `oekaki.html` が存在し、ブラウザで開ける
- [ ] `quiz.html` が存在し、ブラウザで開ける
- [ ] `shashin.html` が存在し、ブラウザで開ける
- [ ] `index.html` の3カードが active になっている
- [ ] `index.html` から各ゲームへのリンクが正しく動く

---

## GitHub へのコミット（全完了後）

```bash
git add oekaki.html quiz.html shashin.html index.html
git commit -m "feat: おえかき・クイズ・しゃしんを追加"
git push
```

Vercel が自動デプロイを開始します（1〜2分）。
