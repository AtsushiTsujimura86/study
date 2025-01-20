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


