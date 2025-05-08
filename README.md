# SQLメモ

## 4大命令
* _SELECT_  
* _UPDATE_  
* _DELETE_  
* _INSERT_

【 使用例 】  

    select 費用 from 家計簿

    update 家計簿 set 入金額 = 1500

    delete from 家計簿 where 日付 = 2025-05-08

    insert into 家計簿 (費目, 日付, 出金額) values ('通信費', '2025-12-25', 5000)
    

## その他
_as_ ... 別名をつける  
    
    select 出金額 as PAY from 家計簿 as MONEYBOOK
          
_is null_ ... NULLの判定をする

    select * from 家計簿 where 出金額 is null

    select * from 家計簿 where 給料 is not null

_like_ ... パターンマッチング
           (_...任意の一文字, %...任意の0文字以上)

    select * from 家計簿 where メモ like '%購入'

    select * from 家計簿 where メモ like '%100$%' escape '$'

_between_ ... 範囲判定(以上、以下の範囲)

    select * from 家計簿 where 出金額 between 500 and 1000
