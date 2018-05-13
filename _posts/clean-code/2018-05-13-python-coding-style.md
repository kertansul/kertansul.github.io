---
layout: page
title: Python-Coding-Style
category: clean_code
---

## 前言
**為什麼 我們需要 無瑕的程式碼 clean code**

<details>
  <summary>曾經有這樣的玩笑, "唯一有效的 程式品質 度量單位: 每分鐘罵髒話的次數 (WTFs/minute)"</summary>
也有人統計過, 一個軟體工程師 撰寫程式碼 與 閱讀程式碼 的時間比大約是 1:9<br/>
換句話說, 除了追求程式碼的 效能與正確性 外, 撰寫時的 可閱讀性 亦是重要的一環<br/>
一個高品質的程式碼, 是能夠 讓後續使用者(包含自己) 在 重複利用, 除蟲, 或 拓展新功能 時能輕易上手
</details><br/>

**怎樣的 程式碼, 能夠稱之為 clean code?**

<details>
  <summary>程式碼 應該 易於理解</summary>

  <details>
    <summary>**可讀性基本定理**: 撰寫程式時, 應該將 讀者理解 所需的時間 降到最短</summary>
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
  </details>
</details><br/>

**短的程式碼 都比較好嗎?**

<details>
  <summary>不一定. 與其 減少程式碼數量, 還不如 想辦法 縮短理解時間 更加重要</summary>
  舉個例子, 這個 單行 表示式:
 
```java
assert((!(bucket = FindBucket(key))) || !bucket->IsOccupied() )
```
  比起 兩行的寫法 需要更多時間理解:

```java
bucket = FindBucket(key)
if (bucket != NULL) assert(!bucket->IsOccupied());
```
</details>


## 改善方案
* To be Done


## References
* Dustin Boswell, Trevor Foucher, 莊弘祥 譯, The Art of Readable Code 易讀程式之美學
* Robert C. Martin, 戴于晉 譯, Clean Code 無瑕的程式碼
* Google Style Guide: <https://google.github.io/styleguide/pyguide.html>
* PEP 8: <https://www.python.org/dev/peps/pep-0008/>
* PEP 257: <https://www.python.org/dev/peps/pep-0257/>
