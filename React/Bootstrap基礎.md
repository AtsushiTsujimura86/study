## Bootstrapの基礎
以下のスクリプトをhtmlのhead内に入れる
```
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-9ndCyUaIbzAi2FUVXJi0CjmCapSmO7SnpJef0486qhLnuZ2cdeRhO02iuK6FUUVM" crossorigin="anonymous">
```

### よく使うやつ
- container
- bg-color
- text-color  
なお、colorにはprimary, secondary, success, danger, whiteなどがある  
- m-n: margin
マージンの指定、m-0から0-5まであり、m-0が余白ゼロ
- p-n: padding
マージンと同様
なお、mt-3などとすると、margin-top-3という意味  
-form-control
-form-check-input, type=checkbox
-btn btn-color
-list-group(ulに)
-list-group-item(liに)
-table table-striped 交互に色を変えたtable
-table-dark(theadに、公式ドキュメントではthead-darkって書いてあるがなぜかできない)
-alert alert-color
-card card-header card-body card-footer


### grid
画面が12分割されていて、rowの中でどれだけcolを使うかを指定する。ブレイクポイント(画面の大きさで表示を変更する境目)も指定する。
下の例ではコンテンツが半々に表示される。
```
<div class="row">
  <div class="col-md-6">コンテンツ</div>
  <div class="col-md-6">コンテンツ</div>
</div>
```

### container内のグリッド
contaienrクラス内にrow-colを入れると、グリッドの部分がcontainerの指定する余白からはみ出してしまう。  
- 原因：カラムの間に自動的に隙間(gutter)が作られる。そのため左右に-15のマージンができる。
- 解決策1：rowにg-0クラスを追加する。```<div row g-0>```
- 解決策2：サイトのcontainerをcontainer-fluidにして、全体をgridで(row-col)で設計する。container-fluidは常に100％になる。
