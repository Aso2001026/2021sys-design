```uml
@startuml

customer       |o-ri-o{     order
order          ||-ri-|{     order_detail
order_detail    }-do-||     items
items          }o-le-||     category![image](https://user-images.githubusercontent.com/83051005/124544333-e16ad100-de61-11eb-849f-670cd6eaaf94.png)

@enduml

```
