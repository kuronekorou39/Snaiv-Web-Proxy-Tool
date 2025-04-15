
# 🛠 VSCode + Git + Electron 開発環境セットアップ手順書（Windows向け）

---

## ✅ 1. Visual Studio Code（VSCode）のインストール

1. 公式サイトからダウンロード  
   👉 https://code.visualstudio.com/

2. インストーラーを実行し、以下にチェックを入れてインストール  
   - 「Add to PATH」にチェック
   - 「右クリックメニューに 'Open with Code' を追加」にチェック

3. インストール後、コマンドプロンプトで確認：

```bash
code --version
```

---

## ✅ 2. Git のインストールと設定

1. Git公式からインストーラをダウンロード  
   👉 https://git-scm.com/

2. 基本的にデフォルト設定でOK（Git Bash も同時に入る）

3. インストール後の確認：

```bash
git --version
```

4. 初期設定（名前とメールアドレス）：

```bash
git config --global user.name "Your Name"
git config --global user.email "your@example.com"
```

---

## ✅ 3. Node.js（npm含む）のインストール

1. Node.js公式サイトからLTS版をインストール  
   👉 https://nodejs.org/

2. インストール後の確認：

```bash
node -v
npm -v
```

---

## ✅ 4. Electron の準備（プロジェクト作成）

1. 任意のフォルダで新しいプロジェクト作成：

```bash
mkdir my-electron-app
cd my-electron-app
npm init -y
```

2. Electronをインストール：

```bash
npm install electron --save-dev
```

3. `package.json` を編集して、`scripts` に以下を追加：

```json
"scripts": {
  "start": "electron ."
}
```

4. `main.js` を作成（最小構成）：

```js
const { app, BrowserWindow } = require('electron');
const path = require('path');

function createWindow () {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js')
    }
  });
  win.loadFile('index.html');
}

app.whenReady().then(() => {
  createWindow();
});
```

5. `index.html` を作成：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Hello Electron</title>
  </head>
  <body>
    <h1>Hello from Electron!</h1>
  </body>
</html>
```

6. 起動テスト：

```bash
npm start
```

---

## ✅ 5. Gitでバージョン管理（初回だけ）

```bash
git init
echo "node_modules/" > .gitignore
git add .
git commit -m "Initial Electron app"
```

---

## 🎉 完了！

これで VSCode + Git + Electron の開発環境が整いました！
以降は VSCode 上でコード編集・Git 管理・Electron 起動がすべてできるようになります。
