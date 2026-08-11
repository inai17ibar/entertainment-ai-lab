# /add-neta — 新しいネタを追加する

ユーザーの説明から新しいネタを `neta/` に登録してください。

引数（ネタの説明）: $ARGUMENTS

## 手順

1. 説明からカテゴリを判定する: `dev`（定期開発）/ `x-post`（X投稿）/ `gen-ai`（生成AIサービス実験）。
   判断がつかない場合のみユーザーに確認する。
2. `neta/TEMPLATE.md` をベースに `neta/<カテゴリのディレクトリ>/YYYY-MM-DD-<slug>.md` を作成する。
   - 日付は今日（`date +%Y-%m-%d` で取得）
   - slug は内容を表す英語 kebab-case（例: `suno-bgm-experiment`）
   - カテゴリのディレクトリ: dev → `neta/dev/`、x-post → `neta/x-posts/`、gen-ai → `neta/gen-ai/`
3. frontmatter を埋める: `status: idea`、`channels` はユーザーの意向（不明なら空のまま）、`created` は今日。
4. 「概要」「狙い・見せ場」を説明から書けるところまで埋める。書けない項目は空欄のまま残す（勝手に創作しない）。
5. `neta/INDEX.md` の「💡 アイデア」表に行を追加する（プレースホルダー行「まだありません」が残っていれば削除）。
6. 作成したファイルパスと内容の要約を報告する。
