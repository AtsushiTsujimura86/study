## React Component

### コンポーネントの定義
コンポーネント名は必ず先頭を大文字に
```
function Component(){
  return JSX
}
```

### コンポーネントの呼び出し
```<Component/>```

### 引数propsの使い方
```
function Component(props){
  return <div className={props.alert}>
    <p>{props.name}</p>
    </div>
}

<Component alert="alert alert-primary" name="John Smith"/>
```

## コンポーネントのクラス
```
imoprt React, {Component} from "react"
class コンポーネント名 extends Component{
  constructor(props){
    super(props);
    コンストラクタの処理
  }
  render(){
    JSXの記述、実際に表示するもの
  }
}

extern default コンポーネント名
```

## イベントのバインド
コンポーネントでは単にonClickなどに関数を指定するだけではダメで以下の二つが必要
### onClickへの関数(メソッド)指定
コンポーネントクラスにあるメソッドをthis.メソッド名で指定する。
```
<button onClick={this.メソッド名}></button>
```
### メソッドのバインド
バインド：メソッド内のthisをクラスのインスタンスに固定する。  
バインドしないとイベントハンドラメソッドのthisがundefinedになる。  
__**バインド方法**__
1. constructorにバインド宣言
```
constructor(){
  super()
  this.doAction = this.doAction.bind(this);
・・・
<button onClick={this.doAction}></button>
```
3. メソッドをアロー関数を使って定義
```
doAction = () => {
  処理記述
}
```

### アロー関数とは
アロー関数はthis(呼び出し元を指定する参照)を持たず、定義時のスコープのthisをそのまま引き継ぐ。
