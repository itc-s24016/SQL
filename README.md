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
as ... 別名をつける  
    
    select 出金額 as PAY from 家計簿 as MONEYBOOK
    
