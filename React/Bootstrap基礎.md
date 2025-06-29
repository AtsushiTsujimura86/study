# Bootstrap 5 基礎まとめ

## 📎 導入方法

HTMLの `<head>` 内に以下を追加します：

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-9ndCyUaIbzAi2FUVXJi0CjmCapSmO7SnpJef0486qhLnuZ2cdeRhO02iuK6FUUVM" crossorigin="anonymous">
```

---

## 🔧 よく使うユーティリティクラス

### レイアウト
| クラス名 | 説明 |
|----------|------|
| `container` | 固定幅＋中央寄せレイアウト用コンテナ |
| `container-fluid` | 幅100％のフルコンテナ（全画面） |
| `row`, `col` | グリッドレイアウト用行・列 |

---

### 余白・パディング
| クラス | 内容 | 備考 |
|--------|------|------|
| `m-n` | margin（0〜5）例：`m-0`, `m-3` |
| `p-n` | padding（0〜5）例：`p-2`, `pt-4`（t = top） |
| `mt-n`, `mb-n`, `ms-n`, `me-n` | 上・下・左・右方向に個別指定可能（s=start, e=end） |

---

### 色の指定（背景・文字・ボタンなど）
| 種類 | 例 |
|------|----|
| 背景色：`bg-〇〇` | `bg-primary`, `bg-secondary`, `bg-success`, `bg-danger`, `bg-white` |
| 文字色：`text-〇〇` | `text-primary`, `text-white`, `text-muted`, `text-danger` |
| ボタン色：`btn btn-〇〇` | `btn btn-primary`, `btn btn-outline-secondary` |

---

## 📄 フォーム要素

| クラス名 | 内容 |
|----------|------|
| `form-control` | 入力フィールドに適用（input, textarea） |
| `form-check-input` | チェックボックスやラジオボタン |
| `form-check-label` | チェックボックス横のラベル |

---

## 📚 コンポーネント系クラス

| コンポーネント | 主なクラス |
|----------------|-------------|
| ボタン | `btn btn-primary` など |
| アラート | `alert alert-success`, `alert-danger` など |
| カード | `card`, `card-header`, `card-body`, `card-footer` |
| リスト | `list-group`, `list-group-item` |
| テーブル | `table`, `table-striped`, `table-hover`, `table-dark`（※`thead-dark`はv5で非推奨） |

---

## 🧱 グリッドシステム（12分割）

Bootstrapの画面幅に応じたレスポンシブ対応グリッド。  
`col-`（自動）や `col-md-6`（中画面以上で幅6）などを指定。

```html
<div class="row">
  <div class="col-md-6">コンテンツ①</div>
  <div class="col-md-6">コンテンツ②</div>
</div>
```

---

## 🛠 グリッド内の余白問題と対策

### 📌 問題：
- `container`内で`row`と`col`を使うと、**自動でgutter（カラム間の余白）**が発生し、外側にはみ出すことがある。

### ✅ 解決策：

#### 解決策①：`row`に `g-0` を追加
```html
<div class="row g-0">
  <div class="col">…</div>
</div>
```

#### 解決策②：`container-fluid` を使う
```html
<div class="container-fluid">
  <div class="row">
    <div class="col">…</div>
  </div>
</div>
```

---

## 🔚 補足

- Bootstrapは**基本クラスの組み合わせ**だけで美しく整ったUIが作れます。
- 公式ドキュメント（https://getbootstrap.com/docs/5.3/getting-started/introduction/）も随時確認すると理解が深まります。

