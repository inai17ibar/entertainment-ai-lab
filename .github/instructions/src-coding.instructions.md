---
description: "Use when writing or editing neta files. Covers file naming, frontmatter schema, and document structure."
applyTo: "neta/**"
---
# ネタファイル規約

## 命名

- ファイル名: `YYYY-MM-DD-<slug>.md`（日付はネタ追加日、slug は内容を表す英語 kebab-case）
  - 例: `2026-08-11-suno-bgm-experiment.md`
- 配置: カテゴリに応じて `neta/dev/`（定期開発）/ `neta/x-posts/`（X投稿）/ `neta/gen-ai/`（生成AI実験）

## Frontmatter スキーマ

`neta/TEMPLATE.md` の frontmatter をそのまま使う。キーの追加・削除はしない。

| キー | 値 |
|------|-----|
| `title` | ネタのタイトル（日本語可） |
| `category` | `dev` \| `x-post` \| `gen-ai` |
| `status` | `idea` \| `doing` \| `published` \| `dropped` |
| `channels` | `x` / `note` / `youtube` の配列 |
| `created` | 追加日 `YYYY-MM-DD` |
| `published` | 公開日（公開後に記入） |
| `links` | 公開後の URL の配列 |

## 本文構成

`neta/TEMPLATE.md` の見出し（概要 / 狙い・見せ場 / メモ・進捗ログ / 投稿ドラフト）を維持する。
進捗は「メモ・進捗ログ」に日付付きで追記していく。

## 制約

- ネタ本文・投稿ドラフトをユーザー確認なしに削除・書き換えしない（`AGENTS.md` 参照）
- ネタの追加・ステータス変更時は `neta/INDEX.md` を必ず同時に更新する

## Verification

変更後は以下を確認する:
```sh
grep -rn '{{' --include='*.md' .   # プレースホルダーが残っていないこと
```
