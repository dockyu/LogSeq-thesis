tags:: #[[壓縮]]

- ## 簡介
  Terry A. Welch在1984發表[A Technique for High-Performance Data Compression](https://courses.cs.duke.edu/spring03/cps296.5/papers/welch_1984_technique_for.pdf)，提出**LZW**，改進**LZ78**
- ## 演算法
  原文: `a b b a b a b a c`
  dictionary裡已經初始化ASCII
  Dictionary:
  |index||
  |:-:|:-:|
  |0|`null`|
  |97|`a`|
  |98|`b`|
  |99|`c`|
  |255|`nbsp`|
- ### 壓縮
  ![HJAcKx4Fa.png](../assets/HJAcKx4Fa_1706121188555_0.png){:height 477, :width 780} 
  
  輸出(碼字流): `97 98 98 256 259 99`
- ### 解壓縮
  圖怪怪的，應該要在CW輸出解碼
  ![SyVJObVKp.png](../assets/SyVJObVKp_1706121202878_0.png)
- ## 參考
  
  [数据压缩——LZW 编解码算法实现与分析](https://blog.csdn.net/Bingyeshinvwang/article/details/124242848)