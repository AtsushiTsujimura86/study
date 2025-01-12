# React勉強

### Reactプロジェクトの作り方
以下のコマンドでreact_appというフォルダ、プロジェクトが作られる。エラーが出るが気にせずに
```
npx create-react-app react_app
```
その後、以下のコマンドで開発用サーバプログラムを起動し、そこでwebアプリを公開しアクセスできる。
```
npm start
```
そうすると、web-vitalsというのがないとエラーが出るので
```
npm install web-vitals
```
プロジェクトのビルド
プロジェクトはアプリケーションそのものではなく、開発するために必要なものをまとめたもの。アプリケーションとして必要なファイルはビルドして作り、webサーバに置く。
```
npm run build
```
___


### エレメントの作成
```
React.createElement(タグ名、属性、中身)
React.createElement(p, {}, 'Hello React!')
```

### レンダリング
レンダリングとはオブジェクトを具体的に目に見えるような形にする
```
ReactDOM.render(element, DOM)
```

### 型を見る
```
console.log(typeof elm)
```

### cssのcursor
マウスポインターが要素の上にいるときに表示されるマウスカーソルを設定します。
```
cursor: poinster;
cursor: wait
```
### DOMのエレメントとノード　　
エレメント≒タグ、ノードは開始タグ、中身、終了タグなどの細かい単位　　
``` <p>hello world</p> ```はエレメント```<p>```, ```hello world```, ```</p>```はそれぞれノード。また、改行やインデントの半角スペースもノードである点に注意





