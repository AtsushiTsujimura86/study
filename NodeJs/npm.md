# Node.js開発における npm / npx / nodemon の整理

## ✅ npmとは？
- **Node.jsパッケージマネージャ**
- ライブラリやツール（例：Express, nodemonなど）をインストールするためのコマンド

## ✅ パッケージのインストール
```bash
npm install <パッケージ名>
```


## ✅ ローカルとグローバルインストールの違い

| 種類 | 説明 | 実行方法 |
|------|------|----------|
| ローカルインストール | プロジェクト内の `node_modules` に入る | `npx` または `npm run` 経由で使う |
| グローバルインストール | OS共通のPATHに入る | どこでも直接コマンドで実行できる |

```bash
# ローカル
npm install nodemon           # プロジェクト内だけで使う
npm install --save-dev nodemon

# グローバル
npm install -g nodemon        # どの場所でも使えるCLIツール
```

---

## ✅ nodemonとは？
- **Node.jsアプリを自動再起動してくれる便利ツール**
- 通常はコード変更 → 手動で `node xxx.js` を再実行
- `nodemon` なら保存するだけで自動再実行される

---

## ✅ なぜ「nodemon が使えない」となるのか？

```
'nodemon' は認識されません
```

これは：
- `nodemon` がローカルにしか入っていない
- そのため、**ターミナルのPATHに含まれず実行できない**

---

## ✅ 解決策3パターン

### ✅ 方法①：npxを使う

```bash
npx nodemon index.js
```

- ローカルの `.bin/nodemon` を一時的に実行
- 最も簡単で、学習用におすすめ

---

### ✅ 方法②：npmスクリプトに登録して実行

`package.json` に以下を追加：

```json
"scripts": {
  "dev": "nodemon index.js"
}
```

実行方法：

```bash
npm run dev
```

---

### ✅ 方法③：グローバルにインストール

```bash
npm install -g nodemon
```

- これでどの場所でも `nodemon index.js` が使えるようになる

---

