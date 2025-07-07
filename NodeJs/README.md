# Node.js 備忘録

## 🛠️ プロジェクト初期化

```bash
npm init -y
```

- `package.json` を自動生成
- スクリプトや依存パッケージの管理に使う
- -yはすべての質問にyesで答えるという意味

---

## 📦 パッケージのインストール

```bash
npm install [パッケージ名]
```

例：
```bash
npm install express
npm install socket.io
```

グローバルに入れるとき（あまり推奨されない）：
```bash
npm install -g nodemon
```

---

## 🚀 よく使うツール系パッケージ

| パッケージ名 | 説明 |
|--------------|------|
| `express` | Webサーバ構築の定番 |
| `socket.io` | WebSocket通信（リアルタイム） |
| `nodemon` | ソース変更を検知して自動再起動（開発効率UP） |
| `cors` | CORS（別ドメイン許可）設定に必要 |
| `dotenv` | `.env` から環境変数を読み込む |

---

## 🧪 実行

```bash
node index.js         # 通常実行
nodemon index.js      # 自動再起動（開発用）
```

---

## 🌐 HTTPサーバ + WebSocket（最低限構成）

```js
// index.js
const express = require('express');
const http = require('http');
const { Server } = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = new Server(server);

io.on('connection', (socket) => {
  console.log('クライアント接続:', socket.id);
  socket.emit('message', '接続完了');
});

server.listen(3000, () => {
  console.log('http://localhost:3000 で起動中');
});
```

---

## 📁 フォルダ構成例（API + WebSocket）

```
server/
├── index.js         ← エントリポイント
├── package.json
├── .env             ← 環境変数（任意）
└── node_modules/
```

---

## 📋 その他Tips

- `require()` はCommonJS形式。ES Modulesを使う場合は `type: "module"` を `package.json` に記述。
- `process.env.PORT` などで `.env` の変数を使用可能（`dotenv`が必要）。
- `console.log()` でログ確認。`chalk` で色分けもできる。

---

## 📌 よくあるトラブル

| 現象 | 対処法 |
|------|--------|
| `EADDRINUSE` | ポートが使用中 → 他のアプリが使ってないか確認 |
| `CORS` エラー | クライアントとサーバのポートが異なる → `cors` を使う |
| モジュールが見つからない | `npm install` を忘れてる or ディレクトリが違う |

---

## 🔚 補足

- Node.jsはサーバ常駐型。ログ受信やAPI提供などに向いている。
- Express + Socket.IO を組み合わせると、簡易サーバ〜リアルタイムアプリまで対応可能。

