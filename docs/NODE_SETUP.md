# Node.js セットアップガイド

Step4（実装）に進む前に Node.js / npm をインストールします。

---

## まず確認

ターミナル（Cursor 内の Terminal タブ）で以下を実行してください。

```bash
node -v
```

`v20.x.x` のように表示されれば**インストール済み**です。このドキュメントはスキップして OK。

エラーが出たり、コマンドが見つからない場合は以下のどちらかでインストールしてください。

---

## Mac の場合

### Homebrew 経由（推奨）

1. ターミナルアプリを開く
2. Homebrew をインストール（すでに入っていればスキップ）
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
3. nvm（Node バージョン管理ツール）をインストール
   ```bash
   brew install nvm
   ```
4. nvm を使って Node をインストール
   ```bash
   nvm install --lts
   nvm use --lts
   ```
5. 確認
   ```bash
   node -v   # v20.x.x のように表示されれば OK
   npm -v    # 10.x.x のように表示されれば OK
   ```

---

## Windows の場合

1. [nodejs.org](https://nodejs.org/ja/) を開く
2. 「LTS（推奨版）」をクリックしてダウンロード
3. ダウンロードした `.msi` ファイルを実行してインストール
4. インストール完了後、**PowerShell または コマンドプロンプトを新しく開く**
5. 確認
   ```bash
   node -v
   npm -v
   ```

> WSL（Windows Subsystem for Linux）を使っている場合は Mac の手順に従ってください。

---

## インストール後の確認

```bash
node -v   # v20 以上であれば OK
npm -v    # v9 以上であれば OK
```

確認できたら Step4 の実装に戻ってください。
