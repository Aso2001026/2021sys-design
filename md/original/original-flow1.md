画像が途切れて表示される場合があります。
原因は、画像（png）変換時の負荷のようです。
ビットマップ（png）ではなく、
ベクター画像（svg）なら、変換の負荷が下がります。
たとえば PrantUMLserverでも、
「view as png」では失敗しても、
「view as SVG」なら、ちゃんと見えます。
そこで、PegmatiteのサーバーURLの設定を、
png変換からSVG変換へ変更していただけるとご覧になることができます。

 

Chromeの拡張機能一覧からPegmatiteの詳細を選んで、
「拡張機能のオプション」のBae URLを
https://www.plantuml.com/plantuml/svg/
というふうに、末尾をsvgに書き替えてください。
そして途中で切れていたPrantUML画像を再表示したら、svgで表示されるはずです。

```uml
@startuml
opt アカウントを持っていない
ユーザー -> webサーバー : アカウント登録処理(メールアドレス必須)
webサーバー -> メールサーバー: アカウント登録処理(メールアドレス必須)
メールサーバー -> ユーザー :本人確認メール送付(確認url付き)
ユーザー -> webサーバー : 本人確認処理
webサーバー -> DBサーバー: アカウント情報登録処理
DBサーバー --> DBサーバー : アカウント情報登録処理
DBサーバー --> webサーバー: 処理結果表示
webサーバー -> ユーザー :処理結果表示
end
ユーザー -> webサーバー : ログイン処理
webサーバー -> DBサーバー: ログイン処理
DBサーバー --> DBサーバー : ログイン処理
DBサーバー --> webサーバー: 結果表示
webサーバー -> ユーザー :結果表示
loop 購入する商品が決まるまで

alt 商品を検索してカートに入れる場合
ユーザー -> webサーバー : 買いたいものを検索
webサーバー -> DBサーバー: 検索処理
DBサーバー --> DBサーバー : 検索処理
DBサーバー --> webサーバー: 検索結果
webサーバー -> ユーザー :検索結果
ユーザー -> webサーバー : 詳細表示
webサーバー -> DBサーバー: 詳細検索
DBサーバー --> DBサーバー : 詳細検索
DBサーバー --> webサーバー: 検索結果
webサーバー -> ユーザー :検索結果
ユーザー -> webサーバー : カートに入れるボタンを押す
webサーバー -> DBサーバー: カートに商品を追加する
DBサーバー --> DBサーバー : カートに商品を追加する

else 一覧ページからカートに入れる場合
ユーザー -> webサーバー : 詳細表示
webサーバー -> DBサーバー: 詳細検索
DBサーバー --> DBサーバー : 詳細検索
DBサーバー --> webサーバー: 検索結果
webサーバー -> ユーザー :検索結果
ユーザー -> webサーバー : カートに入れるボタンを押す
webサーバー -> DBサーバー: カートに商品を追加する
DBサーバー --> DBサーバー : カートに商品を追加する

else カートの中の商品を表示する
ユーザー -> webサーバー : カートのボタンを押す
webサーバー -> DBサーバー: カートの中身を検索
DBサーバー --> DBサーバー : カートの中身を検索
DBサーバー --> webサーバー: 検索結果
loop カート内の商品の個数回
webサーバー -> webサーバー :商品の値段を合計金額に足し、カート内の次の商品を読みこむ
end
webサーバー -> ユーザー :検索結果,合計金額表示
opt カートの中身を削除したい場合
ユーザー -> webサーバー : 削除ボタンを押す
webサーバー -> DBサーバー: カートから削除する処理
DBサーバー --> DBサーバー : カートから削除する処理
DBサーバー --> DBサーバー : 削除後のカートの中を検索
DBサーバー --> webサーバー: 検索結果
loop カート内の商品の個数回
webサーバー -> webサーバー :商品の値段を合計金額に足し、カート内の次の商品を読みこむ
end
webサーバー -> ユーザー :検索結果
end
end

end


ユーザー -> webサーバー : 購入処理
webサーバー -> DBサーバー: 購入処理
DBサーバー --> DBサーバー : 購入処理,在庫数を減らす処理
DBサーバー --> webサーバー: 結果表示
webサーバー -> ユーザー : 結果表示
opt 在庫が規定量より少なくなった
DBサーバー -> メールサーバー : 在庫補充処理
alt 手動発注
メールサーバー -> 発注責任者 : 発注確認メール送信
発注責任者 -> 取引先相手 : 発注メール送信
else 自動発注
メールサーバー -> 取引先相手 : 発注メール送信
メールサーバー -> 発注責任者 : 発注完了メール送信
end
end
@enduml
```
