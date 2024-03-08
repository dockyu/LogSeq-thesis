tags:: #[[(1-d,1-vector)問題]]

- 題目
	- [[(1-d,1-vector)-問題定義]]
	- 給定 $d$
	- 給定 $c_{i}=t,t為一任意數$
- 解題
	- 將 $S$分為 $S_{l}=\left\lbrace s_1,s_2,\ldots,s_{i}\right\rbrace$以及 $S_{r}=\left\lbrace s_{i},s_{i+1},\ldots,s_{n}\right\rbrace$
	- 將 $S_{l}$反轉， $S_{l}^{^{\prime}}=\left\lbrace s_{i},s_{i-1,}s_{i-2},\ldots,s_2,s_1\right\rbrace$
	- 將問題變成兩個問題，使用 [[(1-d,1-vector)-給定起點]]裡的方法解題
		- 給定 $c_{i}=t$，求 $\min_{C_{l}^{^{\prime}}}E_{i,1}(C_{l}^{^{\prime}})$
		  logseq.order-list-type:: number
		- 給定 $c_{i}=t$，求 $\min_{C_{r}}E_{i,n}(C_{r})$
		  logseq.order-list-type:: number
-