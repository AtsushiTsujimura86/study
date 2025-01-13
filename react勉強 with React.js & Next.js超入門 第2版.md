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

## JSX
JavaScriptに直接HTMLを記述することができる。babelというコンパイラを用いてJSXのタグをJavaScriptのコードに変換している。
babelは以下で読み込む
```
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```
また、実際にJSXを記述するscriptタグには``` <script type="text/babel">```  
```
<script type="text/babel">
...
let elm = (
  <div className="alert alert-primary">
    <h2>Hello JSX</h2>
    <p>this is new message</p>
  </div>
)
</script>
```
renderできるエレメントは一つだけなので、必ずdivタグで囲む。divタグ内にクラスを与えたい場合は、classではなくclassNameを使う。classはJSでは予約語になってるから。  

### styleをオブジェクト(JSON)として与える
```
const msg_sty = {]
  fontSize:"20px",
  color:"red",
  border:"1px solid blue"
}
let elm = (
  <div>
    <h2 style={msg_sty}>new message</h2>
  </div>
)
```

### 関数
```
let printMsg = function(msg, size, color){
...
  return <p style={style}>{msg}</p>
}
```
### JSX内の条件分岐
```
#trueなら表示、falseなら表示しない場合
{flag &&
  JSXを記述
}

#trueとfalseで表示内容が異なる場合、三項演算子の記述 [条件?trueの処理:falseの処理]
{flag ?
  trueの場合のJSXを記述
:
  falseの場合のJSXの記述
}
```

### mapメソッド
配列などのコレクションオブジェクトのメソッドで、中身をひとつづつ取り出す。JSXでは一つずつ要素を取り出して、それぞれのエレメントを作るのに使う。  
下の例では、配列の要素であるオブジェクトをひとつずつ取り出して、tableの行をそれぞれ作成している。
```
data = [
            {name:"James", mail:"james@gmail.com", age:41},
            {name:"Kobe", mail:"Kobe@gmail.com", age:45},
            {name:"Johdan", mail:"johdan@gmail.com", age:60}
        ]
let elm = (
    <div>
        <table className="table table-striped">
            <thead className="table-dark">
                <tr>
                    <th>name</th>
                    <th>email</th>
                    <th>age</th>
                </tr>
            </thead>
            <tbody>
            {data.map((value) => (
                <tr>
                    <td>{value.name}</td>
                    <td>{value.mail}</td>
                    <td>{value.age}</td>
                </tr>
            ))}
            </tbody>
        </table>
    </div>
)
```




