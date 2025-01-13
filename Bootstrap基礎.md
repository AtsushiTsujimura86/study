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
-alert alert-color
