tags:: #[[壓縮]]

- ## 簡介
  同時使用 [[LZ77]] 與[霍夫曼編碼](/5XeCWS5HQgamFqCcCFqKDA)的無損壓縮
- ## 結構
  
  由一連串block組成，每個block儲存同樣類型的資料，總共有三種資料
  1. No compression
  2. Compressed with fixed Huffman codes
  3. Compressed with dynamic Huffman codes
  
  每個block都有3 bits(bit(0~2))的Header，其他部分是Data
  | bit (0) 的值 | 描述                                 |
  |--------------|--------------------------------------|
  | 0            | 這是數據流的最後一個塊。                 |
  | 1            | 在這個塊之後還有更多塊。                 |
  
  | bit (0) 的值 | 描述                                        |
  |--------------|---------------------------------------------|
  | 00           | 無壓縮。原始數據存儲，長度從 0 到 65535 字節。用於不可壓縮的數據。 |
  | 01           | 使用固定霍夫曼碼壓縮。它使用了在 Deflate RFC 中定義的預定義/預先同意的霍夫曼樹。這種類型用於短消息，其中使用預定義的霍夫曼樹比使用自定義的霍夫曼樹節省更多空間。 |
  | 10           | 使用動態霍夫曼碼壓縮。將會定義包含的霍夫曼樹。     |
  | 11           | 此文件是保留的，請勿使用。                      |
  
  ![HJseiLYKp.png](../assets/HJseiLYKp_1706163653889_0.png){:height 34, :width 136}
- ## 動態block
- ### 定義Huffman tree的特性
  Deflate tree: 最斜的那一顆，只需要知道每個leaf的長度就能重建出來，由左到右ex:`1, 2, 3, 3`，並以同樣順序紀錄對應的字符(稱為code)ex: `3, 4, 5, 6`
  ![SJyg80ut6.png](../assets/SJyg80ut6_1706163669433_0.png) 
  因為我們會先知道有哪些code會被編碼(之後會說)，所以可以用一個序列表示這顆Huffman tree
  
  碼字：     0、0、1、2、3、3、0、0、0、0、0、………
  對應code： 1、2、3、4、5、6、7、8、9、10、11、……
- ### distance壓縮
  distance會被做成一顆Huffman tree，為了不要讓樹太大，所以distance只有30個可能，用這30個code出現的頻率建立一顆Huffman tree
  假設今天我的distance是19，所以會被編碼為code `8`，但是因為code `8`有8種可能，所以我需要**馬上**接著3 bits的extra bits，例如17->`000` 18->`001` 19->`010`，之所以要馬上是因為Huffman編碼的長度是不固定的，所以要直接接在後面，這樣才知道這是他的extra bits
  ! ![HkvwlDtKT.png](../assets/HkvwlDtKT_1706163686252_0.png)
- ### literal和length的壓縮
  literal和length總共有286個可能，分別對應到一個code
  + code `0`~`255`是一個literal(未加密的字)
  + code `256`是block的結束
  + code `257`~`285`是一個length的區間，因為是區間，所以讀到length的時候還要接著讀extra bits來正確取得區間
  ![By3zPwYt6.png](../assets/By3zPwYt6_1706163696628_0.png)
- ### 壓縮步驟
- #### 1. LZ77編碼
  + 輸入: 原文的stream
  + 輸出: literal跟(length,distance)的序列
  + ex: `h, (7,2), y, u, (20,6), (3,3)`
- #### 2. Huffman編碼1 (編碼literal & length)
  + 輸入: LZ77編碼的輸出序列
  + 輸出: Huffman **tree1** & 碼字流(**LIT bits**)
  + ex: `104, 261, {2}, 121, 117, 269[01], {6}, 257, {3}`
    + `[]`是extra bits, `()`是還沒編碼的distance，數字是用**tree1**編碼的Huffman code
- #### 3. Huffman編碼2 (編碼distance)
  + 輸入: Huffman編碼1的輸出碼字流(LIT bits)
  + 輸出:Huffman **tree2** & 碼字流(**DIST bits**)
  + ex: `104, 261, {1}, 121, 117, 269[01], {4}[1], 257, {2}`
    + `[]`是extra bits, `{}`是用**tree2**編碼的Huffman code
- #### 4. 轉換 tree1 & tree2
  Huffman tree可以表示成一顆斜斜的樹
- #### 5. 序列化 tree1 & tree2
  + 輸入: tree1 & tree2
  + 輸出: 兩個序列 **CL1** & **CL2**
- #### 6. 遊程編碼 CL1 & CL2
  + 輸入: CL1 & CL2
  + 輸出: 兩個序列 **SQ1** & **SQ2**
- #### 7. Huffman編碼3 (編碼SQ1 & SQ2)
  + 輸入: SQ1 & SQ2
  + 輸出: 兩個bit流**SQ1 bits** & **SQ2 bits**，一顆Huffman **tree3**
- #### 8. 轉換&序列化 tree3
  + 輸入: tree3
  + 輸出: **CCL bits**
  
  經過以上過程一個**動態Huffman block**要儲存的資訊有
  1. LIT bits
  2. DIST bits
  3. SQ1 bits
  4. SQ2 bits
  5. CCL bits
- ## 參考
  [Deflate Algorithm](https://thuc.space/posts/deflate/) <- 規格書
  [deflate算法总结](https://blog.csdn.net/qq_42139383/article/details/115064562) <- 完整說明
  [An Explanation of the Deflate Algorithm](https://www.zlib.net/feldspar.html)
  [【压缩原理】 deflate 算法](https://blog.csdn.net/tuwenqi2013/article/details/103758292)