```uml
@startuml

customer       |o-ri-o{     order
order          ||-ri-|{     order_detail
order_detail    }-do-||     items
items          }o-le-||     category

entity "顧客マスタ" as customer <m_customers>
<<M,MASTER_MASK_COLOR>>{
+ customer_code[PK]
--
pass
name
address
tel
mail
del_flag
reg_date
}
@enduml

```
