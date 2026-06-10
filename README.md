# ai-course-starter

Cursor を使って web アプリを作るコースのスターターキットです。  
このリポジトリをクローンすると、Cursor のチャットから AI スキルを呼び出せるようになります。

---

## 受講開始までの手順

### Step 0: 準備する（5つ）

| # | やること | ガイド |
|---|---------|--------|
| 1 | このリポジトリをクローンする | 下記参照 |
| 2 | git / GitHub アカウントを準備する | [docs/GIT_SETUP.md](docs/GIT_SETUP.md) |
| 3 | Cursor をインストール・設定する | [docs/SETUP.md](docs/SETUP.md) |
| 4 | Node.js / npm をインストールする | [docs/NODE_SETUP.md](docs/NODE_SETUP.md) |
| 5 | Supabase / Vercel のアカウントを作っておく | [docs/SUPABASE_SETUP.md](docs/SUPABASE_SETUP.md) / [docs/VERCEL_SETUP.md](docs/VERCEL_SETUP.md) |

### クローン方法

```bash
git clone https://github.com/oya-ui/ai-course-starter.git
cd ai-course-starter
```

クローン後、**Cursor でこのフォルダを開く**（`File → Open Folder...`）。

> スキルは Cursor でフォルダを開いたときに自動で読み込まれます。  
> 認識されない場合は Cursor を再起動してください。

---

## アプリを作る流れ（Step 1〜4）

```
Step 1: 何を作るかを決める（MVP仮説）
  ↓  /course-mvp-step1-hypothesis
Step 2: 画面とスコープを整理する
  ↓  /course-mvp-step2-story-scope
Step 3: UI モックを作って確認する
  ↓  /course-mvp-step3-ui-mock
Step 4: 実装して Vercel に公開する
     /course-mvp-step4-implement-host
```

各ステップで **Cursor のチャット欄にスキル名を入力**すると AI が対話しながら進めてくれます。

---

## スキル一覧

### `course-mvp-step1-hypothesis` — MVP の仮説を固める

「何を作るか」を対話形式で整理するスキル。  
誰のどんな課題を解決するか、実現難易度（緑/黄/赤）を確認しながら絞り込みます。  
完了すると `mvp/STEP1.md` が作成されます。

呼び出し方: `/course-mvp-step1-hypothesis`、「Step1」、「MVP仮説」、「何を作るか」

---

### `course-mvp-step2-story-scope` — 画面とスコープを整理する

Step1 の仮説をもとに、ユーザーストーリー・画面一覧・スコープ（段 A〜D）を整理します。  
完了すると `mvp/STEP2.md` が作成されます。

呼び出し方: `/course-mvp-step2-story-scope`、「Step2」、「ストーリー」、「スコープ」、「画面整理」

---

### `course-mvp-step3-ui-mock` — UI モックを作って磨く

Step2 の画面一覧をもとに静的 HTML モック（`mvp/STEP3_UI_MOCK.html`）を作ります。  
フィードバックを繰り返して（最大 5 往復）「これでいい」と言えるまで一緒に磨きます。

呼び出し方: `/course-mvp-step3-ui-mock`、「Step3」、「モック」、「UI」、「画面を作る」

---

### `course-mvp-step4-implement-host` — 実装して本番公開する

モック了承後、`my-mvp/` に Next.js アプリを作り、Supabase + Vercel でデプロイするまで伴走します。  
**Cursor はこのフォルダ（ai-course-starter）を開いたまま**作業します。

呼び出し方: `/course-mvp-step4-implement-host`、「Step4」、「実装」、「デプロイ」、「本番公開」

---

## Cursor Pro の使い方の心得

- **1メッセージ1テーマ**: あれもこれも一度に頼まず、1つ解決してから次へ
- **エラーはログをそのままコピペ**: 説明せずターミナルのエラーをそのまま貼る
- **長くなったら新しいチャットを開く**: コンテキストが重くなると精度が下がる
- **成果物はこまめに確認**: `mvp/` フォルダのファイルが更新されているか都度確認する

---

## うまくいかないとき

| 症状 | 対処 |
|------|------|
| スキルが起動しない | Cursor を再起動 → チャットを新しく開く |
| `git: command not found` | [docs/GIT_SETUP.md](docs/GIT_SETUP.md) を確認 |
| `npm: command not found` | [docs/NODE_SETUP.md](docs/NODE_SETUP.md) を確認 |
| Vercel ビルドエラー | `cd my-mvp && npm run build` してエラーを確認 |
| Supabase のデータが出ない | RLS 設定と環境変数のキー名を確認 |
| 3 回試してもダメ | メンターに相談する |

---

## ディレクトリ構成

```
ai-course-starter/        ← Cursor でここを開き続ける（Step1〜4 すべて）
├── README.md
├── .gitignore
├── docs/
│   ├── GIT_SETUP.md      ← git / GitHub のセットアップ手順
│   ├── SETUP.md          ← Cursor の設定・モデル選び・Pro 上限
│   ├── NODE_SETUP.md     ← Node.js のインストール手順
│   ├── SUPABASE_SETUP.md ← Supabase のアカウント作成〜API キー取得
│   └── VERCEL_SETUP.md   ← Vercel へのデプロイ手順
├── mvp/                  ← Step1〜4 の成果物ドキュメント（自動作成）
│   ├── STEP1.md
│   ├── STEP2.md
│   ├── STEP3_UI_MOCK.html
│   └── STEP4.md
├── my-mvp/               ← Step4 で作る Next.js アプリ（独立リポジトリ）
│   ├── app/
│   ├── package.json
│   └── .env.local
└── .cursor/
    └── skills/
        ├── course-mvp-step1-hypothesis/SKILL.md
        ├── course-mvp-step2-story-scope/SKILL.md
        ├── course-mvp-step3-ui-mock/SKILL.md
        └── course-mvp-step4-implement-host/SKILL.md
```

> `.cursor/` フォルダはスキルの本体です。削除しないでください。  
> `my-mvp/` は別の GitHub リポジトリとして管理し、Vercel はそちらを接続します。
