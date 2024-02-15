tags:: #[[永興學長的研究]]

- 題目
	- 處理一維整數序列，並限制moving vector為正負**k**
	- Given a raw sequence R={r1, r2,…, rn} of n integers, where the moving vector from $r_i$ to $r_{i+1}$ is defined by $r_{i+1} - r_i$, the optimal d-element filter problem of R is to generate a new sequence P of n integers, such that
		- **P** consists 2 distinct moving vectors *k* and -*k*
		- **P** has the minimized $\sum_{i=1}^{n}|p_i - r_i|$
-
-
- 考慮所有情況
	- 數字遞增、遞減
		- 理想情況: 原始序列的間距都差不多
		- 有一個間距特別大(小)
		- 一半的間距超小，另一半超大
	- 數字上下跳動
-
- 方法
	- 找最大間距以及最小間距，目標k一定在這之間
	  logseq.order-list-type:: number