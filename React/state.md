## stateまとめ
- プロパティ：クラスに値を保存しておくもの
- 属性(props)：コンポーネントの属性をまとめて保存するもの、read only
- ステート：コンポーネントの状態を表す値を保管するもの、ステートの値を変えるとコンポーネントの状態を変えれる

**プロパティは変更しても、ReactDOM.render()しないと表示が変更されない。ステートは値が変更されると自動的に表示が更新される**

### 使い方
stateはオブジェクト形式で書ける。setStateでステートの変更ができる。なおsetState内に記述していないステートは変更されない。
また、コンポーネントクラス内で記述する場合は、this.stateやthis.setStateのように記述する。
```
state={
  msg: "Hello State",
  name: "Kawai",
  count: 0
}
setState({
  count: state.count+1
})
```
