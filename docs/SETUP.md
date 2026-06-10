# Cursor セットアップガイド

このドキュメントは Cursor を初めて使う方向けの導入手順です。

> **事前準備**: git と GitHub アカウントが必要です。まだの場合は先に [GIT_SETUP.md](GIT_SETUP.md) を参照してください。

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

### ステップ別モデルの選び方

チャット右上のドロップダウンでモデルを切り替えられます。ステップに合わせて使い分けると Premium 消費を抑えられます。

| ステップ | 推奨モデル | 理由 |
|---------|-----------|------|
| Step1（仮説インタビュー） | haiku 系（無制限） | テキスト整理なので軽量で十分 |
| Step2（ストーリー整理） | haiku 系（無制限） | 同上 |
| Step3（HTML モック生成） | Claude Sonnet | 画面の品質に直結するため |
| Step4（実装・デプロイ） | Claude Sonnet | コード生成の精度が重要なため |

> **各ステップを始める前にモデルを確認してください。**

### リクエストを節約するコツ

- **各ステップごとに新しいチャットを開く**（前のステップの履歴を引きずらない）
- 1回のチャットで「あれもこれも」聞かず、1つずつ解決する
- エラーはターミナルのログをそのままコピーして貼る（説明文を省く）
- Step3 は 5 往復で必ず終わらせる（長引かせない）

### リクエスト残数の確認方法

Cursor の左下のアカウントアイコン → 「Manage Subscription」から月の使用状況が確認できます。月初にリセットされます。

---

## 5. スキルが動かないとき

スキルはチャット欄で `/スキル名` と打つか、「Step1」「MVP仮説」などのトリガー語を含む文を送ると起動します。

**それでも起動しない場合**

1. Cursor を再起動する（スキルは起動時に読み込まれる）
2. `.cursor/skills/` フォルダが存在するか確認する
3. チャットを新しく開いて再試行する

---

## 次のステップ

- git / GitHub → [GIT_SETUP.md](GIT_SETUP.md)
- Node.js のセットアップ → [NODE_SETUP.md](NODE_SETUP.md)
- Supabase のセットアップ → [SUPABASE_SETUP.md](SUPABASE_SETUP.md)
- Vercel のセットアップ → [VERCEL_SETUP.md](VERCEL_SETUP.md)
