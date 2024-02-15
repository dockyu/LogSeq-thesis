tags:: #[[壓縮]]

- ## 簡介
  Lempel–Ziv–Storer–Szymanski（LZSS）是一個無失真資料壓縮演算法，屬於LZ77的衍生，1982年由James Storer和Thomas Szymanski建立
- ## 演算法
  ![S1k5ierFp.png](../assets/S1k5ierFp_1706120928454_0.png)
- ![rJVooxHKa.png](../assets/rJVooxHKa_1706120935276_0.png)
- ### LZSS vs. LZ77
  LZ77遇到任何先前出現過的最長字串s都會將s編碼，但是當s很短時編碼反而會讓這個字串變長，所以設定一個MIN_LENGTH，如果s<MIN_LENGTH就不要編碼而是直接用原文
- ## 參考
  
  [LZSS算法学习](https://blog.csdn.net/allen_nmk/article/details/126171867)