# データベース設計図

## d_purchase

|項目名|型|PK|NN|FK|
|-----|--|--|--|--|
|order_id|bigint(20)|○|○||
|customer_code|varchar(50)||○|○|
|purchase_date|date||○||
|total_price|int(11)||○||

## d_purchase_detail

|項目名|型|PK|NN|FK|
|-----|--|--|--|--|
|order_id|bigint(20) |○|○|○|
|item_code|int(11)|○|○|○|
|price|int(11)||○||
|num|int(11)||○||

## m_customers

|項目名|型|PK|NN|FK|
|-----|--|--|--|--|
|customer_code|varchar(50)|○|○||
|pass|varchar(50)||○||
|name|varchar(20)||○||
|postal_code|varchar(15)||○|| 
|address|varchar(100)||○||
|tel|varchar(20)||○||
|mail|varchar(100)||○||
|del_flag|int(1)||||
|reg_date|date||○||

## m_category

|項目名|型|PK|NN|FK|
|-----|--|--|--|--|
|category_id|int(11)|○|○||
|name|varchar(20)||○||
|reg_date|date||○||

## m_items

|項目名|型|PK|NN|FK|
|-----|--|--|--|--|
|item_code|int(11)|○|○||
|item_name|varchar(50)||○||
|price|int(11)||○||
|category_id|int(11)||○|○|
|image|varchar(200)||○||
|detail|varchar(500)||||
|del_flag|int(1)||○||
|reg_date|date||○||

## d_questions
|項目名|型|PK|NN|FK|
|-----|--|--|--|--|
|question_code|int(11)|○|○||
|name|varchar(20)||○||
|tel|varchar(20)||○||
|mail|varchar(100)||○||
|question|varchar(500)||○||
|solution_flag|int(1)||○||
|reg_date|date||○||

## d_answers
|項目名|型|PK|NN|FK|
|-----|--|--|--|--|
|question_code|int(11)|○|○|○|
|answer_code|int(11)|○|○||
|employee_code|int(11)||○|○|
|answer|varchar(500)||○||
|reg_date|date||○||

## m_enployees
|項目名|型|PK|NN|FK|
|-----|--|--|--|--|
|employee_code|int(11)|○|○||
|name|varchar(20)||○||
|reg_date|date||○||
