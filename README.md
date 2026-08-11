# entertainment-ai-lab

**毎週、エンタメ×AIのプロトタイプをひとつ公開する研究室です。**
ライブ、Vlog、生成AI。思いついたネタを小さく作って、すぐ公開します。
できたものは通し番号つきのプロトタイプとして、ここに一枚ずつ増えていきます。

🎫 ランディングページ: https://inai17ibar.github.io/entertainment-ai-lab/

---

## Prototypes

| # | プロトタイプ | 一言 | リンク |
|---|------------|------|--------|
| **#1** | **AFTERPOST** | ライブ終演後の感想からシェアカードを作り、X へ投稿できるファン向けツール | [GitHub](https://github.com/inai17ibar/after-post) |
| **#2** | **vlog-cockpit** | Vlogger のための企画→公開ワークフローツール。v0.1（カンバン＋投稿カレンダー）公開中 | [Live](https://vlog-cockpit.vercel.app) / [GitHub](https://github.com/inai17ibar/vlog-cockpit) |
| #3 | （NOW PRINTING） | 次の一枚は週次棚卸しから | [ネタ帳](neta/INDEX.md) |

---

## 研究室の回し方

```
💡 ネタ帳に貯める ──→ 🔧 週次で棚卸し ──→ 🎫 作って公開（Prototype #N）
```

- ネタは [`neta/INDEX.md`](neta/INDEX.md) でステータス別（idea → doing → published）に公開管理しています
- 週1回の棚卸しで「今週やるネタ」を決めて進めます
- `dev` カテゴリのネタが `published` になると、Prototype #N としてこの一覧と
  ランディングページに追加されます

## 活動カテゴリ

| カテゴリ | 内容 | ネタ置き場 |
|---------|------|-----------|
| 🛠 定期開発 (`dev`) | プロトタイプ（ツール・アプリ・MCP サーバーなど）の開発ネタ | `neta/dev/` |
| 📣 X 投稿 (`x-post`) | X (Twitter) で紹介する小ネタ・Tips・成果報告 | `neta/x-posts/` |
| 🎨 生成 AI 実験 (`gen-ai`) | 画像・音楽・動画などの生成 AI サービスを使った取り組み | `neta/gen-ai/` |

## 紹介チャネル

- **X (Twitter)** — [@sorajiro07062](https://x.com/sorajiro07062) 進捗・小ネタ・成果の投稿
- **note / ブログ** — 長文の解説記事
- **YouTube / 動画** — デモ・制作過程の紹介

## ディレクトリ構成

```
entertainment-ai-lab/
├── docs/              # 公開ランディングページ（GitHub Pages）
├── neta/              # ネタ管理の本体（INDEX.md がハブ）
├── AGENTS.md          # AI エージェント向けのルール・制約
├── ADR.md             # 意思決定の記録
├── CLAUDE.md          # Claude Code 設定・運用ルール
├── .claude/commands/  # /add-neta, /review-neta などのコマンド定義
└── .github/           # GitHub Copilot 向け設定
```

## リポジトリ運用

- 重要な決定は [`ADR.md`](ADR.md) に記録します（ADR-001: ネタ管理方式）
- AI エージェント向けのルールは [`AGENTS.md`](AGENTS.md) を参照してください
