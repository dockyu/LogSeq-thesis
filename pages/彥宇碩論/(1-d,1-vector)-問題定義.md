tags:: #[[(1-d,1-vector)問題]]

- 原始序列  $S=\left\lbrace s_{1,}s_{2,}s_{3,}\ldots,s_{n}\right\rbrace$
- 壓縮序列  $C=\left\lbrace c_{1,}c_{2,}c_{3,}\ldots,c_{n}\right\rbrace$
- 誤差
	- $e_{i}=\lvert c_{i}-s_{i}\rvert$
	- $E_{i,j}=\sum_{i}^{j}e_{i}$
- 找到 $k$，使的 $c_{i}=c_{i-1}+k \text{ or } c_{i-1}-k$
- 求 $\min_{C}E_{1,n}(C)$
-
- 題目
	- 處理一維整數序列，並限制moving vector為正負**k**
	- Given a raw sequence R={r1, r2,…, rn} of n integers, where the moving vector from $r_i$ to $r_{i+1}$ is defined by $r_{i+1} - r_i$, the optimal d-element filter problem of R is to generate a new sequence P of n integers, such that
		- **P** consists 2 distinct moving vectors *k* and -*k*
		- **P** has the minimized $\sum_{i=1}^{n}|p_i - r_i|$
-