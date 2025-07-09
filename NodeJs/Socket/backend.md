# Socket通信 backend
<br>

## 基本のプログラム
```javascript
const express = require('express');
const cors = require('cors');
const http = require('http');
const { Server } = require('socket.io');

const app = express();
const server = http.createServer(app);

const io = new Server(server, {
    cors:{
        origin: "*",
        methiods: ["GET", "POST"],
    }
})

app.use(cors());
app.use(express.json());


app.post('/post', (req, res) => {
  console.log('POST受信:', req.body);
  res.json({ message: '受け取りました', received: req.body });
});


io.on("connection",(socket)=>{
    console.log("client connected:", socket.id);

    socket.on("send_message", (data) => {
        console.log("受信メッセージ:", data);
        io.emit("receive_message", data);
    });
    
    socket.on("disconnect",()=>{
        console.log("client disconnected:", socket.id);
    })
})

server.listen(3000, () => {
    console.log('🚀 サーバー起動中：http://localhost:3000');
})
```
<br>

## 要素の解説

### Socket.ioインスタンスの生成
``` javascript
const io = new Server(server, {
    cors:{
        origin: "*",
        methiods: ["GET", "POST"],
    }
})
```
このコードは、Socket.IO サーバーのインスタンスを作成し、CORS（クロスオリジンリソースシェアリング）の設定を行っています。Server クラスのコンストラクタに HTTP サーバーオブジェクト（server）とオプションオブジェクトを渡しています。

オプションの cors プロパティでは、origin: "*" により、どのオリジン（ドメイン）からの接続も許可しています。methods: ["GET", "POST"] で、許可する HTTP メソッドを指定しています。この設定により、異なるドメインからの WebSocket や HTTP 通信が制限なく許可されるため、開発時や公開 API などで便利ですが、セキュリティ面では注意が必要です。
<br>
<br>


### Socket接続、通信
``` javascript
io.on("connection",(socket)=>{
    console.log("client connected:", socket.id);

    socket.on("send_message", (data) => {
        console.log("受信メッセージ:", data);
        io.emit("receive_message", data);
    });
    
    socket.on("disconnect",()=>{
        console.log("client disconnected:", socket.id);
    })
})
```
このコードは、Socket.IO サーバーでクライアントとの接続や通信イベントを処理する部分です。

io.on("connection", (socket) => { ... }) は、新しいクライアントがサーバーに接続したときに呼び出されます。コールバック関数の引数 socket は、そのクライアントとの通信に使うオブジェクトです。接続時にはクライアントの一意な ID（socket.id）をコンソールに表示しています。

socket.on("send_message", (data) => { ... }) は、クライアントから "send_message" イベントが送信されたときに実行されます。受信したデータ（data）をコンソールに表示し、io.emit("receive_message", data) で全クライアントに "receive_message" イベントとして同じデータを送信します。これにより、チャットのようなリアルタイムなメッセージ共有が実現できます。

最後に、socket.on("disconnect", () => { ... }) でクライアントが切断されたときの処理を行い、切断されたクライアントの ID をコンソールに表示しています。

この構造により、複数クライアント間でリアルタイムなメッセージのやり取りや接続・切断の管理が簡単に行えます。
<br>


```
```
<br>
