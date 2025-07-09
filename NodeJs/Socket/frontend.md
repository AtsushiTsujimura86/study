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
このコードは、React の useEffect フックを使って Socket.IO の "receive_message" イベントを監視し、受信したメッセージをチャットログに追加する処理を行っています。
useEffect の中で socket.on("receive_message", (data) => { ... }) を設定することで、サーバーから "receive_message" イベントが届いたときにコールバックが実行されます。コールバック内では、setLog を使って現在のログ配列に新しいメッセージ（data）を追加しています。これにより、リアルタイムでチャット画面が更新されます。
また、useEffect の戻り値としてクリーンアップ関数を返しています。socket.off("receive_message") により、コンポーネントがアンマウントされる際にイベントリスナーを解除し、不要なメモリ消費や二重登録を防いでいます。依存配列が空（[]）なので、この処理はコンポーネントのマウント時に一度だけ実行されます。
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

