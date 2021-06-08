```uml
@startuml
loop 入力内容を確定するまで
ユーザー -> webサーバー : 住所入力
webサーバー --> ユーザー :入力された住所表示
end
webサーバー -> DBサーバー : 住所登録
DBサーバー --> DBサーバー : 登録処理


@enduml
```
