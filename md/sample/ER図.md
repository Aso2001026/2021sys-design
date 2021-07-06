```startuml
@stratuml
customer       |o-ri-o{     order
order          ||-ri-|{     order_detail
order_detail    }-do-||     items
items          }o-le-||     category
@enduml
```
