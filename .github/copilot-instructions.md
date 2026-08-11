---
applyTo: "**"
---
# entertainment-ai-lab — Project Instructions

個人ラボ活動のネタ（定期的な開発・X の投稿・生成 AI サービスを使った取り組み）を管理し、
対外的に紹介できる状態に育てるための Markdown ドキュメント運用リポジトリ。

See [`AGENTS.md`](../AGENTS.md) for the full agent index and [`ADR.md`](../ADR.md) for architecture decisions.

## Non-negotiable constraints

- `neta/**` のネタ本文・投稿ドラフトをユーザー確認なしに削除・書き換えしない（追記・提案は可）
- `status: published` のネタ本文は公開記録 — 遡及的な変更禁止
- ネタの追加・ステータス変更時は `neta/INDEX.md` を必ず同時に更新する
- X・note 等への実際の投稿はユーザーが行う。AI は下書き・提案まで

## Source layout

- `docs/` — 公開ランディングページ（GitHub Pages）。`index.html` にプロトタイプ一覧
- `neta/` — ネタ管理の本体。`INDEX.md`（一覧ハブ）、`TEMPLATE.md`（雛形）、
  カテゴリ別ディレクトリ `dev/` `x-posts/` `gen-ai/`
- `AGENTS.md` / `ADR.md` / `CLAUDE.md` / `README.md` — ルール・決定・紹介ドキュメント
- `.claude/commands/` — `/add-neta` `/review-neta` などのコマンド定義

## Verification commands

```sh
# プレースホルダー残存チェック（何もヒットしなければ OK）
grep -rn '{{' --include='*.md' .
```

## Autonomous pipeline

All agent work flows through five lanes in order:

```
▶ [LANE:explore]   → ✓ [LANE:explore:complete]
▶ [LANE:plan]      → ✓ [LANE:plan:complete]
▶ [LANE:implement] → ✓ [LANE:implement:complete]
▶ [LANE:verify]    → ✓ [LANE:verify:complete]
▶ [LANE:review]    → ✓ [LANE:review:complete]
```

A `✗ [LANE:{name}:blocked]` event means the lane failed and requires attention before the pipeline can proceed.

## Agents available

| Agent | Purpose | Invoke |
|-------|---------|--------|
| `@Main` | Full autonomous pipeline (explore→plan→implement→verify→review) | High-level tasks |
| `@Plan` | Design a plan, wait for approval, handoff to Implementer | Complex changes |
| `@Explore` | Read-only research and Q&A | Questions about the repo |
| `@Implementer` | Execute an approved plan (handoff only) | Via Plan |
| `@Reviewer` | Consistency + quality audit | After changes |
| `@Verification` | Run consistency checks | Spot checks |

Prompt shortcuts in `.github/prompts/`:
- **Plan Change** — decompose a change request into an implementation plan
- **Implement Change** — run the full pipeline for a specific request
- **Verify Workspace** — run narrowest relevant verification
