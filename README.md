# to-81-web
to-81の公式ページのつもりでしたが、現状、対局カードを作成するサイトになっています。

# 要件
以下の条件で入力されたメンバー同士で総当たり戦をするための対局カードを作る。
* 参加者は2人以上とする
* 回ごとに同時に対局をスタートする(参加者が奇数の場合、回ごとに1人は観戦)
* 各参加者は全員と1回ずつ対局する(同じ参加者と2回対局しない)

# 仕様
## 考えた経緯
-- 以下の方法でいけるのかと思ったら、参加者が10人になった時点で破綻
-- n = 0
-- (n + 1)回戦の時は、先頭の人を末尾からn番目とマッチング 
-- nが残りの参加者数に満たない場合、(n - 1)%2番目の人とマッチング

## メモ
- 8人の時
-- 18 27 36 45 //234567 3456 末尾から0番目 末尾から0番目 末尾から0番目
-- 17 26 35 48 //234568 3458 末尾から1番目 末尾から1番目 末尾から1番目
-- 16 25 34 78 //234578 3478 末尾から2番目 末尾から2番目 末尾から2番目
-- 15 24 38 67 //234678 3678 末尾から3番目 末尾から3番目 末尾から0番目
-- 14 23 57 68 //235678 5678 末尾から4番目 末尾から4番目 末尾から1番目 
-- 13 28 47 56 //245678 4567 末尾から5番目 末尾から0番目 末尾から0番目
-- 12 37 46 58 //345678 4568 末尾から6番目 末尾から1番目 末尾から1番目

- 7人の時(奇数の場合は、1つ増やした数でマッチングし、末尾の番号と当たった場合は休み)
-- 18 27 36 45 //234567 3456 末尾から0番目 末尾から0番目 末尾から0番目(1が休み)
-- 17 26 35 48 //234568 3458 末尾から1番目 末尾から1番目 末尾から1番目(4が休み)
-- 16 25 34 78 //234578 3478 末尾から2番目 末尾から2番目 末尾から2番目(7が休み)
-- 15 24 38 67 //234678 3678 末尾から3番目 末尾から3番目 末尾から0番目(3が休み)
-- 14 23 57 68 //235678 5678 末尾から4番目 末尾から4番目 末尾から1番目(6が休み)
-- 13 28 47 56 //245678 4567 末尾から5番目 末尾から0番目 末尾から0番目(2が休み)
-- 12 37 46 58 //345678 4568 末尾から6番目 末尾から1番目 末尾から1番目(5が休み)

- 6人の時
-- 16 25 34 // 2345 末尾から0番目 末尾から0番目
-- 15 24 36 // 2346 末尾から1番目 末尾から1番目
-- 14 23 56 // 2356 末尾から2番目 末尾から2番目
-- 13 26 45 // 2456 末尾から3番目 末尾から0番目
-- 12 35 46 // 3456 末尾から4番目 末尾から1番目

- 5人の時(奇数の場合は、1つ増やした数でマッチングし、末尾の番号と当たった場合は休み)
-- 16 25 34 // 2345 末尾から0番目 末尾から0番目(1が休み)
-- 15 24 36 // 2346 末尾から1番目 末尾から1番目(3が休み)
-- 14 23 56 // 2356 末尾から2番目 末尾から2番目(5が休み)
-- 13 26 45 // 2456 末尾から3番目 末尾から0番目(2が休み)
-- 12 35 46 // 3456 末尾から4番目 末尾から1番目(6が休み)

## 今後の展望
サッカー界ではcircle methodとよばれる方法があるらしい
でも今のところ最大参加者数が6なので、現状でも使えない訳ではない
もう少し考えたい

