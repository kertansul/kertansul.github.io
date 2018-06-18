---
layout: page
title: Clean Code - part 1
category: clean_code
---

## 入門觀念
* 為何要考慮 易讀 程式碼 之美學?
    * 不知道, 你是否跟我一樣, 並非CS本科, 但本著對 computer vision 或 deep learning 的熱忱, 半路出家開始寫起程式碼. 隨著時間 一點一滴過去, 你手下鍵盤敲出的程式碼 一行一行累積. 從原本什麼都不會 只能複製 hello world 的 範例; 開始會用 google 然後從 stackoverflow 找有綠勾勾的解答; 到 有點組織地結合各個功能, 東拼西湊 組出一個可以動的 project. 
    * 在這過程中, 不知道到你是否也跟我有過同樣的疑惑
        * 我沒受過什麼專業的訓練, 寫出來的程式碼好嗎?
        * 總覺得 自己寫的程式碼 比較醜, stackoverflow 貼來得比較漂亮, 但說不出具體原因
        * 過了 3個月~半年, 回頭看自己的程式碼, 發現根本看不懂自己在寫什麼
    * 如果我們面臨的疑惑相同, 那在此分享我找到的答案, 就是 “想辦法讓你的程式碼 變得 容易閱讀(/使用/修改, 請自行替換)”
    * 在這個 open-source code 滿天飛的世代, 身為一個 撰寫程式的 programmer, 從中獲得的成就感已經由 “哇! 我的程式碼跑得動!” 漸漸轉化成 “哇! 有好多人 fork 我的程式碼!” 一個 能夠執行的程式碼並不稀奇, 但 一個能讓 許多人喜愛使用的 程式碼 卻十分珍貴. 
* 文章編排
    * 本篇blog內容, 90%以上啟發或摘錄自 The Art of Readable Code (詳情見Ref), 所以也可以算是一篇 讀書心得整理報告. 這本書不厚, 內文+目錄不到200頁, 但頁頁精彩, 其中大部分的程式碼又以 Python 撰寫角度出發, 個人認為很適合 剛接觸 ML/DL, 同時希望寫出 “乾淨程式碼” 的 programmer閱讀. 當然, 也感謝在 Viscovery 的好夥伴 城市小模yoco 推薦我此書
    * 以下, 將以 條列式 具體描述 幾項我認為不錯的觀點


## 重點 1: 名稱的選擇

### 1.1 採用更具代表意義的名稱
* 程式碼是寫給人看的. 撰寫時, 應該細心地為讀者思考. 怎麼用簡潔地話語, 表達出程式碼的邏輯.
* 在這之中, 又以**命名**尤其重要. 使用具有代表意義的名稱, 能讓人更快地進入狀況, 了解某個function在處理的問題, 或是某個variable代表的意義.
* **使用具有代表意義的名稱, 比在乎名稱長短來得更重要.**
* 舉例來說
    * 實作一個 *從url下載圖片* 的程式碼, 若使用
    ```python
    def get_img(url, dst):
    ```
    * 因為 不清楚到底是在 `get` 什麼, 還不如使用更明確的
    ```python
    def download_image(url, dst):
    ```

### 1.2: 避免大量使用 tmp, retval 等無意義的詞彙
* 坦白來說, 你只是懶得 動腦思考 該取什麼名字對吧
* 允許的例外, `i`, `j`, `k` 等 通用 iterators
* `tmp`, `return retval` 這些變數不帶任何意義, 能不用則不用. 例外請見 1.3

### 1.3: 使用範圍 (scope) 越廣的名稱, 越重要!
* 若某個 function 或 variable 的 scope 是通用於整個 project, 那你就要小心了! 使用範圍越廣的 function 或 variable, 越要小心地命名. 因為它將會在你的程式碼中不斷出現
* 相對地, 使用範圍 極小的 function 或 variable, 若生命週期才短短幾行, 就算命名成西瓜也不會有人看不懂, 那倒是不用花太多心思著墨
* 舉例:
    ```python
    def swap_values(a, b):
        tmp = a
        a = b
        b = tmp
        return a, b
    ```
    * 這時你要叫 `tmp`, `buffer`, 或是`西瓜`, 我猜應該沒什麼影響


## 重點 2: 建立個人美學

### 2.1 使用普羅大眾接受的排版方式
* clean code 的概念並非近期出現, 從程式語言誕生的那年起, 許多程式設計師就已經在致力於優化程式碼並提高可讀性. 因此, 與其從無到有建立自己的coding 美學, 還不如從 一些現有模板著手. 在此附上兩個 python 常見(亦被多人使用)的 coding guideline
    * google
        * python coding guideline: https://github.com/google/styleguide/blob/gh-pages/pyguide.md
    * python 官方
        * PEP 8: https://www.python.org/dev/peps/pep-0008/
        * PEP 257: https://www.python.org/dev/peps/pep-0257/

### 2.2 輔助工具: convention 自動檢查程式
* 在 ubuntu 環境裡, 也可以安裝一些 自動檢查程式 (檢查是否follow python 官方 conventions). 舉例來說, `pylint` 就是個不錯的檢查工具
    * 使用方式, 安裝後
        * 在 bash command 下執行 `pylint YOUR_CODE.py`
        * 在 `vim` 中使用 `:SyntasticCheck pylint` (須先安裝 `vim-syntastic`)
* **注意**
    * 一昧追求 convention 計算出來的 高分, 是沒有意義的
    * 檢查工具, 僅提供 **死**的美學規則. 如何從中挑選適合地規則進行 **活用**, 是一個程式設計師必續具備地能力
    * 所謂 **活用**, 在這裡指: **如何讓讀者能更好上手**

### 2.3 程式碼的 一致性
* 如果你是 **自己** 在開發專案: 維持你的美學, 並確保該美學一致化地通用於程式碼
* 若你是在 **修改別人** 的專案, 請接受他的美學, 並在修改時, 維持既有美學
* 對於易讀性而言, **保持程式碼一致化 比 使用正確的規則 更重要**


## 重點 3: 合理地加入註解
* 加入註解不難. 難得是, 該如何 **適時地** 加入註解

### 3.1 什麼地方不該加入註解
* 註解也是程式碼, 寫越多, 後續讀者要讀的也越多
* 不要為了註解而註解
* **不要註解那些能很快從程式碼中知道的事實**
* 舉例:
    * 脫褲子放屁
        ```python
        # training function
        def train(...):
            ...
        ```
        * function 或 variable 名稱已清楚表達意義, 沒必要添加註解
* 不要用註解去 **解釋名稱取得不好 的 function 或 variables, 請 直接修改命名**

### 3.2 應該加入什麼樣的註解
* 與其把 名稱描述一遍, 不如 **解釋更多實作細節**
* 舉例
    * normal
    ```python
    # 在給定的 subtree 找尋指定的 name, 最多找到 depth層
    def find_node_in_subtree(subtree, name, depth)
    ```
    * better
    ```python
    # 找出有指定 'name' 的 node 或 回傳 None
    # 如果 depth <= 0, 只會檢查 subtree
    # 如果 depth == N, 只會檢查 subtree, 以及 N層內的 nodes
    def find_node_in_subtree(subtree, name, depth)
    ```
* **記下 寫程式時 重要的想法**
* 舉例
    * 適當地裡用 特殊名稱 標記, 讓未來的讀者能夠清楚了解程式碼缺陷或不足的地方
    ```python
    # TODO(owner):   作者還沒處理的部份
    # FIXME(owner):  已知的問題
    # HACK(owner):   承認解決方法不夠優雅
    # XXX(owner):    危險! 重要問題
    ```
* **描述 選用某些常數的特定原因**
* 舉例
    ```python
    NUM_THREADS = 8   # 只要 >= 2 * num_processors 就夠了
    ```
* **想像程式碼在他人眼中的樣子**, 用這樣的角度添加註解ˇ


## Part 1 結語
* 以上僅針對 *易讀程式之美學* 的前半段進行整理, 也就是 程式碼 **表層處理** 的部分. 然而, 書中後半部在描述 **程式碼的架構** 的部分 (e.g. 如何重構, 早期跳出, 一次做一項事情等等), 尚未整理完成, 還待 後續 part 2 進行撰寫. 


## References
* Dustin Boswell, Trevor Foucher, 莊弘祥 譯, The Art of Readable Code 易讀程式之美學
* Robert C. Martin, 戴于晉 譯, Clean Code 無瑕的程式碼
