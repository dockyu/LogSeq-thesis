tags:: #[[(1-d,1-vector)問題]]

- 題目
	- [[(1-d,1-vector)-問題定義]]
	- 給定 $k$
	- 給定 $c_{1}=t,t為一任意數$
- 解題
	- $\text{table }D$
		- $定義D_{i,j}如下，其中i=1,2,\ldots,n且j=-n,\ldots,-1,0,1,\ldots,n:$
		- $D_{i,j}\quad\text{對於所有的}\quad i\in\{1,2,\ldots,n\}\quad\text{和}\quad j\in\{-n,\ldots,-1,0,1,\ldots,n\}$
		- $D_{i,j}代表在c_{i}=c_1+\left(k\cdot j\right)時的最小E_{1,i}$
	- DP公式
		- $D_{i,j}=\min\left\lbrace D_{i-1,j+1},D_{i-1,j-1}\right\rbrace+\lvert c_1+\left(k\cdot j\right)-s_{i}\rvert$
-
-