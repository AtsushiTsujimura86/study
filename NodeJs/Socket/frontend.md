# Socket フロントエンド
<br>

## 基本のプログラム（簡易チャット）
``` javascript
import React from 'react';
import { useState, useEffect } from 'react';
import io from 'socket.io-client';

const socket = io('http://localhost:3000');

function Chat() {
    const [message, setMessage] = useState('');
    const [log, setLog] = useState([]);
    
    const handleSendMessage = ()=>{
        if(message.trim() === "")return;
        socket.emit("send_message",message);
        setMessage('');
    }

    useEffect(() =>{
        socket.on("receive_message", (data)=>{
            setLog((preLog) => [...preLog, data])
        })
        // Clean up the socket connection when the component unmounts
        return () => {
            socket.off("receive_message");
        }
    }, [])

    return(
        <div>
            <h2>Socket Chat</h2>
            <input type="text" value={message} onChange={(e)=>setMessage(e.target.value)} placeholder="Type your message here..." />
            <button onClick={handleSendMessage}>Send</button>

            <ul>
                {log.map((msg, i) => (
                    <li key={i}>{msg}</li>
                ))}
            </ul>
        </div>
    )
}

export default Chat;
```
<br>

## 要素の解説
<br>

### Socketオブジェクトの生成
``` javascript
const socket = io('http://localhost:3000');
```
このコードは、クライアント側（ブラウザなど）で Socket.IO を使ってサーバーへ接続するためのものです。
io('http://localhost:3000') は、localhost のポート 3000 で動作している Socket.IO サーバーに接続します。これにより、socket というオブジェクトが作成され、サーバーとのリアルタイムな通信（イベントの送受信）が可能になります。
この socket オブジェクトを使って、メッセージの送信や受信、接続・切断イベントの監視など、リアルタイム機能を実装できます。
<br>
<br>

### メッセージの送信
``` javascript
const handleSendMessage = ()=>{
    if(message.trim() === "")return;
    socket.emit("send_message",message);
    setMessage('');
}
```
この関数 handleSendMessage は、チャットメッセージの送信処理を担当しています。
まず、message.trim() === "" でメッセージが空白のみ、または空の場合は何もせずに処理を終了します。これにより、空のメッセージが送信されるのを防いでいます。
次に、socket.emit("send_message", message) で、現在のメッセージ内容を "send_message" イベントとしてサーバーに送信します。これにより、サーバー側で他のクライアントにもメッセージが配信される仕組みです。
最後に、setMessage('') で入力欄をリセットし、次のメッセージ入力ができるようにしています。
<br>
<br>

### メッセージの受信
``` javascript
useEffect(() =>{
        socket.on("receive_message", (data)=>{
            setLog((preLog) => [...preLog, data])
        })
        // Clean up the socket connection when the component unmounts
        return () => {
            socket.off("receive_message");
        }
}, [])
```
初回レンダリング時（,[] 依存配列が空だから）に、Socket.ioの"receive_message"イベントをsocket.on()でsocketオブジェクトに登録している⇒addEventListenerみたいな感じ。これにより、socketでメッセージが送られてきたときには、その下に記述した```setLog()...```が呼び出される。また、最後に```socket.off()```でソケットのクリーンアップをすることにより、重複してsocket.onされないようにしている。なお、socket.off()は、コンポーネントが**画面から消えたとき（アンマウント時）**に、登録したリスナーを解除してメモリリークや多重登録を防ぐ。
<br>
<br>

### 
``` javascript
```
<br>

### 
```
```
<br>

