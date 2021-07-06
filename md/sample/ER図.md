```uml
@startuml

skinparam class {
    '図の背景
    BackgroundColor Snow
    '図の枠
    BorderColor Black
    'リレーションの色
    ArrowColor Black
}

!define MASTER_MARK_COLOR Orange 
!define TRANSACTION_MARK_COLOR DeepSkyBlue

package "ECサイト" as target_system {
    /'
      マスターテーブルを M、トランザクションを T などで表記
      １文字なら "主" とか "従" まど日本語でも記載可能
     '/

    entity "顧客マスタ" as customer <m_customers> <<M,MASTER_MARK_COLOR>> {
        + customer_code [PK]
        --
        pass
        name
        address
        tel
        mail
        del_flag
        reg_date
    }
    
    entity "購入テーブル" as purchase <d_purchase> <<T,TRANSACTION_MARK_COLOR>> {
        + customer_code [PK]
        --
        order_id
        ustomer_code
        purchase_date
        total_price
        mail
        del_flag
        reg_date
    }
    
    entity "購入詳細テーブル" as customer <m_customers> <<T,TRANSACTION_MARK_COLOR>> {
        + customer_code [PK]
        --
        pass
        name
        address
        tel
        mail
        del_flag
        reg_date
    }
    
    entity "商品マスタ" as customer <m_customers> <<M,MASTER_MARK_COLOR>> {
        + customer_code [PK]
        --
        pass
        name
        address
        tel
        mail
        del_flag
        reg_date
    }
    
    entity "カテゴリマスタ" as customer <m_customers> <<M,MASTER_MARK_COLOR>> {
        + customer_code [PK]
        --
        pass
        name
        address
        tel
        mail
        del_flag
        reg_date
    }
  }
@enduml
```
