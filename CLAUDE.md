# Claude Code 設定 — entertainment-ai-lab

このリポジトリは **entertainment-ai-lab の看板 兼 活動ネタ管理リポジトリ** です。

- **看板（対外）**: 「毎週エンタメ×AI のプロトタイプを公開する研究室」として、README の
  Prototypes 一覧と `docs/index.html`（GitHub Pages ランディング）で制作物をシリーズとして見せる
- **ネタ管理（内部）**: 定期的な開発・X の投稿・生成 AI サービスを使った取り組みのネタを
  `neta/` で育て、公開までのステータスを管理する

コードではなくドキュメント運用が主体です。

---

## ディレクトリ構成

```
entertainment-ai-lab/
├── docs/                     # ★ 公開ランディングページ（GitHub Pages）
│   └── index.html            # プロトタイプ一覧（チケット型）
├── neta/                     # ★ ネタ管理の本体
│   ├── INDEX.md              # 全ネタ一覧（ステータス別・常に最新に保つ）
│   ├── TEMPLATE.md           # ネタファイルの雛形
│   ├── dev/                  # 定期開発ネタ
│   ├── x-posts/              # X 投稿ネタ
│   └── gen-ai/               # 生成 AI サービス実験ネタ
├── AGENTS.md                 # AI エージェント向け北極星（制約はここ）
├── ADR.md                    # 意思決定の記録（ADR-001: ネタ管理方式）
├── README.md                 # リポジトリ紹介
├── .claude/commands/         # スラッシュコマンド定義
└── .github/                  # Copilot 向け設定・エージェント定義
```

---

## スラッシュコマンド

| コマンド | 動作 |
|--------|------|
| `/add-neta <説明>` | ネタを `neta/` に追加し、INDEX.md を更新 |
| `/review-neta` | 週次棚卸し（整合チェック・サマリ・今週のネタ選定） |
| `/generate-adr` | ADR エントリを対話式で ADR.md に追記 |
| `/generate-agents-md` | プロジェクトを分析して AGENTS.md を更新 |

---

## ネタ運用ルール

- **1ネタ = 1ファイル**。`neta/<カテゴリ>/YYYY-MM-DD-<slug>.md`（日付は追加日、slug は英語 kebab-case）
- **カテゴリ**: `dev`（定期開発）→ `neta/dev/` / `x-post`（X投稿）→ `neta/x-posts/` / `gen-ai`（生成AI実験）→ `neta/gen-ai/`
- **ステータス**: `idea` → `doing` → `published`（見送りは `dropped`）
- ネタの追加・ステータス変更時は **必ず `neta/INDEX.md` も同時に更新**する
- `published` になったネタの本文は公開記録として原則変更しない。公開 URL は frontmatter の `links` に記録する
- **週次棚卸し**: 週1回 `/review-neta` を実行し、整合確認と「今週やるネタ」の選定を行う
- **プロトタイプ公開時**: `dev` ネタが `published` になったら、README の Prototypes 表と
  `docs/index.html` にも Prototype #N として追加する（3箇所を必ず同期させる）

---

## Claude への指示

- ネタ本文・投稿ドラフトはユーザーの創作物。**確認なしに削除・書き換えしない**（追記・提案は歓迎）
- X・note 等への**実際の投稿は行わない**。下書き・提案まで
- 検証コマンド: `grep -rn '{{' --include='*.md' .` が何もヒットしないこと（プレースホルダー残存チェック）
- そのほかの制約は `AGENTS.md` の「🚫 絶対守るべき制約」を参照
