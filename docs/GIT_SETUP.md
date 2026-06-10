# git / GitHub セットアップガイド

`git clone` と `git push` を使うために git と GitHub アカウントが必要です。

---

## 1. git をインストールする

### まず確認

ターミナルで以下を実行してください。

```bash
git --version
```

`git version 2.x.x` のように表示されれば**インストール済み**です。このセクションはスキップ OK。

---

### Mac の場合

コマンドを実行したとき「Xcode CLT をインストールしますか？」のダイアログが出る場合は「インストール」を押して待つ。

出ない場合は以下を実行：

```bash
xcode-select --install
```

インストール完了後、新しいターミナルタブを開いて `git --version` を確認。

---

### Windows の場合

1. [git-scm.com/download/win](https://git-scm.com/download/win) を開く
2. インストーラーをダウンロードして実行
3. 設定はすべてデフォルトのままで「Next」を押し続けて OK
4. インストール完了後、**PowerShell を新しく開く**
5. 確認：
   ```bash
   git --version
   ```

---

## 2. GitHub アカウントを作る

1. [github.com](https://github.com) を開く
2. 「Sign up」をクリック
3. メールアドレス・パスワード・ユーザー名を入力して登録
4. メール認証を完了させる

> すでにアカウントがあれば「Sign in」でログインするだけで OK。

---

## 3. my-mvp 用の GitHub リポジトリを作る

Step4 で `my-mvp/` を GitHub に push するための空リポジトリを作ります。

1. GitHub にログインした状態で [github.com/new](https://github.com/new) を開く
2. 以下を設定：
   - **Repository name**: `my-mvp`（自由に変えて OK）
   - **Public / Private**: どちらでも OK
   - 「Initialize this repository」系の**チェックはすべて外す**（README・.gitignore・license を追加しない）
3. 「Create repository」をクリック
4. 表示される URL（`https://github.com/<ユーザー名>/my-mvp.git`）をコピーしておく

---

## 4. my-mvp を GitHub に push する

Step4 スキルの「3. my-mvp を独立した GitHub リポジトリにする」の手順に戻る。

```bash
cd my-mvp
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/<ユーザー名>/my-mvp.git
git push -u origin main
```

`<ユーザー名>` と `my-mvp.git` は手順 3 でコピーした URL に置き換えてください。

---

## 確認

```bash
git --version   # git version 2.x.x が出ればOK
```

GitHub の `my-mvp` リポジトリのページを開いてファイルが表示されれば push 成功です。
