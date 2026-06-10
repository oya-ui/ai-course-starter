# Cursor セットアップガイド

このドキュメントは Cursor を初めて使う方向けの導入手順です。

---

## 1. Cursor をインストールする

1. [cursor.com](https://cursor.com) を開く
2. 「Download」からインストーラをダウンロード
3. インストール完了後、起動する

---

## 2. このリポジトリを開く

1. Cursor を起動
2. `File → Open Folder...` でクローンしたフォルダ（`ai-course-starter`）を選択
3. 「Trust Workspace」のダイアログが出たら「Yes, I trust the authors」を選ぶ

> **確認方法**: 左のファイルツリーに `.cursor/skills/` フォルダが見えていれば OK。

---

## 3. モデルを選ぶ

Cursor のチャット右上にモデル選択のドロップダウンがあります。

| 用途 | 推奨 |
|------|------|
| 普段のコーディング | Claude Sonnet（最新版）|
| 複雑な設計・考えながら書きたい | Auto または claude-opus 系 |
| 速さを優先 | claude-haiku 系 |

→ 迷ったら **Claude Sonnet の最新版** を選べば OK。

---

## 4. Cursor Pro の利用上限について

Cursor Pro プランには**月ごとのリクエスト上限**があります。

- **Premium リクエスト**: 月 500 回（Claude Sonnet / Opus を使うと消費）
- **無制限リクエスト**: 速度制限あり（claude-haiku 系など）

**リクエストを節約するコツ**

- 1回のチャットで「あれもこれも」聞かず、1つずつ解決する
- 長いチャット履歴は新しいチャットを開いてリセットする（コンテキストが重くなるため）
- エラーはターミナルのログをそのままコピーして貼る（説明文を省く）

---

## 5. スキルが動かないとき

スキルはチャット欄で `/スキル名` と打つか、「Step1」「MVP仮説」などのトリガー語を含む文を送ると起動します。

**それでも起動しない場合**

1. Cursor を再起動する（スキルは起動時に読み込まれる）
2. `.cursor/skills/` フォルダが存在するか確認する
3. チャットを新しく開いて再試行する

---

## 次のステップ

- Node.js のセットアップ → [NODE_SETUP.md](NODE_SETUP.md)
- Supabase のセットアップ → [SUPABASE_SETUP.md](SUPABASE_SETUP.md)
- Vercel のセットアップ → [VERCEL_SETUP.md](VERCEL_SETUP.md)
