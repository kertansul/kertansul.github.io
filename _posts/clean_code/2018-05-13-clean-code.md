---
layout: page
title: Clean Code
category: clean_code
---

## 前前言
由於EE的背景, 以前在學校學程式語言時, 課堂上多充斥著 演算法的架構與優化.
也導致我剛入社會時, 腦中僅是思考 如何讓 寫出來的程式, 電腦執行更快, memory 消耗更少.
不是說這樣的觀念不正確, 而是工作幾年後, 體悟所謂 "雜亂程式碼 乃身外之物, 生不帶來, 死不帶去" 的道理.
在追求 程式效率的同時, 該如何讓 後續讀者 看懂 你撰寫的邏輯, 亦是非常重要的課題.
就算程式邏輯寫得再好, 若無法讓 後續讀者(或是幾個月後得自己) 看懂,
該如何談 coding 的 maintain, debug, 跟 後續開發 呢?
最終, 這個沒有人看得懂的code, 將被迫丟到垃圾桶.
而你的所有努力, 也淪為了一次工.

## 前言
Q1: 為什麼 我們需要 無瑕的程式碼 clean code
<details><summary markdown="span">曾經有這樣的玩笑, "唯一有效的 程式品質 度量單位: 每分鐘罵髒話的次數 (WTFs/minute)"</summary>
* 有人統計過, 一個軟體工程師 閱讀程式碼 與 撰寫程式碼 的時間比大約是 9:1<br/>
* 除了追求程式碼的 效能與正確性 外, 撰寫時的 可閱讀性 亦是重要的一環<br/>
* 高品質的程式碼, 是能讓讀者(包含自己) 在 重複利用, 除蟲, 或 拓展新功能 時能輕易上手
</details><br>

Q2: 怎樣的 程式碼, 能夠稱之為 clean code?
<details><summary markdown="span">程式碼 應該 ***易於理解***</summary>
  **可讀性基本定理**: 撰寫程式時, 應該將 讀者理解 所需的時間 降到最短<br>
  舉個例子, 這種寫法:
    
```java
for (Node * node = list->head; node != NULL; node = node->next)
    Print(node->data);
```
  比下面這種寫法來得好:
  
```java
Node* node = list->head;
if (node == NULL) return;
  
while (node->next != NULL) {
    Print(node->data);
    node = node->next;
}
if (node != NULL) Print(node->data);
```
</details><br>

Q3: 短的程式碼 都比較好嗎?
<details><summary markdown="span">不一定. 與其 減少程式碼數量, 還不如 想辦法 ***縮短理解時間*** 更加重要</summary>
  舉個例子, 這個 單行 表示式:
 
```java
assert((!(bucket = FindBucket(key))) || !bucket->IsOccupied() )
```
  比起 兩行的寫法 需要更多時間理解:

```java
bucket = FindBucket(key)
if (bucket != NULL) assert(!bucket->IsOccupied());
```
</details><br>

## 改善方案
* To be Done<br>

## References
* Dustin Boswell, Trevor Foucher, 莊弘祥 譯, The Art of Readable Code 易讀程式之美學
* Robert C. Martin, 戴于晉 譯, Clean Code 無瑕的程式碼
* Google Style Guide: <https://google.github.io/styleguide/pyguide.html>
* PEP 8: <https://www.python.org/dev/peps/pep-0008/>
* PEP 257: <https://www.python.org/dev/peps/pep-0257/>
