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

_distinct_ ... 重複行を削除

    select distinct 費目 from 家計簿 
    
_is null_ ... NULLの判定をする

    select * from 家計簿 where 出金額 is null

    select * from 家計簿 where 給料 is not null

_like_ ... パターンマッチング
           (_...任意の一文字, %...任意の0文字以上)

    select * from 家計簿 where メモ like '%購入'

    select * from 家計簿 where メモ like '%100$%' escape '$'

_between_ ... 範囲判定(以上、以下の範囲)

    select * from 家計簿 where 出金額 between 500 and 1000

_in / not in_ ... 一致、不一致の判定

    select * from 家計簿 where 費目 in ('食費', '交通費')

    select * from 家計簿 where 費目 not in ('食費', '交通費')

_any / all_ ... 複数の値と比較

    select * from 家計簿 where 1000 < any (1000, 2000, 3000)

    select * from 家計簿 where 1000 > all (1500, 2000, 3000)

_and / or / not_ ... 論理演算子

    select * from 家計簿 where 入金額 < 20000 and 光熱費 < 3000

    select * from 家計簿 where 費目 = 外食費 or 費目 = 食費

    select * from 家計簿 where 費目 not 娯楽費

_count_ ... 検索結果の行数をカウント

    select count(*) as 娯楽費の行数 from 家計簿 where 費目 = 娯楽費

    select count(distinct 費目) from 家計簿

_sum / max / min / avg_ ... 集計関数

    select sum(出金額) as 合計 from 家計簿 where 出金額 > 0
    
    select max(出金額) as 散財 from 家計簿 where 出金額 > 0
    
    select min(出金額) as 少額の支払い from 家計簿 where 出金額 > 0
    
    seleect avg(出金額) as 平均値 from 家計簿 where 出金額 > 0

_group by_ ... グループ化

    select 費目,  sum(出金額) as 出金額 from 家計簿 group by 費目

_having_ ... group byに対して絞り込む

    select 費目,  sum(出金額) as 出金額 from 家計簿 group by 費目 having sum(出金額) > 0
