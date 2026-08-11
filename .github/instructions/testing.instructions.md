---
description: "Use when verifying repository consistency. Covers integrity checks between neta files and INDEX.md."
applyTo: "**"
---
# 検証規約

このリポジトリにコード・自動テストはない。「検証」はドキュメントの整合性チェックを指す。

## チェック項目

- `neta/**/*.md`（TEMPLATE.md を除く）の frontmatter と `neta/INDEX.md` の表が一致している
  （ステータス・カテゴリ・チャネル・リンク）
- `status: published` のネタに `published` 日付と `links` が入っている
- ファイル名が `YYYY-MM-DD-<slug>.md` 形式で、カテゴリと配置ディレクトリが一致している
- 本文が `neta/TEMPLATE.md` の見出し構成（概要 / 狙い・見せ場 / メモ・進捗ログ / 投稿ドラフト）に従っている
- プレースホルダー `{{...}}` が残っていない

## Commands

```sh
grep -rn '{{' --include='*.md' .   # 何もヒットしなければ OK
```

Claude Code では `/review-neta`（週次棚卸し）が上記チェックを含む。

## Anti-Patterns

- INDEX.md だけ更新してネタファイルの frontmatter を更新し忘れる（またはその逆）
- published のネタ本文を後から書き換える
- TEMPLATE.md を直接編集してネタを書き始める（必ずコピーして使う）
