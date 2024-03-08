tags:: #[[(1-d,1-vector)問題]]

- 猜想
	- [[(1-d,1-vector)-問題定義]]
	- [[(1-d,1-vector)問題]]的最佳解之一 $C$，其中的某一個 $c_{i}$會等於(對齊)其中一個 $s_{j}$
- 驗證猜想
	- 做實驗觀察(成功)
	  logseq.order-list-type:: number
		- 暴力解實驗: 確實一定會對齊
	- 證明 [[(1-d,1-vector)-給定變化序列]]的解都會對齊
	  logseq.order-list-type:: number
	- 推導(成功)
	  logseq.order-list-type:: number
		- 當目前的壓縮序列 $C$還沒對齊時，一定可以透過 [[(1-d,1-vector)-平移特性]]裡的平移規則平移1單位使 $E$不變或變小，直到對齊
-
-