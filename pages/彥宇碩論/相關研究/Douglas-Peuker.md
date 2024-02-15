tags:: #[[壓縮]], #[[路徑壓縮]]

- ## 簡介
  道格拉斯-普克演算法（Douglas–Peucker algorithm），是GIS系統中用於簡化曲線的一種常用演算法，1972年被提出
- ## 演算法
  
  recurrsion(A,B)
  1. 在AB兩點間連接直線
  2. 找離此線最遠點C，計算C到直線的距離d
  3. 判斷
    + d < threshold: 刪除C點，return
    + d >= threshold: 保留C點
        + recurrsion(A,C)
        + recurrsion(C,B)