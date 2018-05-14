---
layout: page
title: Python Coding Style
category: clean_code
---

## 建議的 coding 格式

#### `pylint`
<details><summary markdown="span">使用 `pylint` 檢查 程式碼</summary>
* 透過 `pip install pylint` 安裝<br/>
* `pylint XXX.py` 執行<br/>
* `pylint` 並非完美, 僅是一個輔助工具. 你應該事情況<br/>
  * 修改程式碼<br/>
  * 將部分報錯 加入 ignore list (過多報錯, 可能導致你忽略真正需要修改的資訊)<br/>
</details>

#### 命名 Naming
<details><summary markdown="span">`module_name`, `package_name`, `ClassName`, `method_name`, `ExceptionName`, `function_name`, `GLOBAL_CONSTANT_NAME`, `global_var_name`, `instance_var_name`, `function_parameter_name`, `local_var_name`</summary>
* 不允許採用<br/>
  * 單一字元名稱 single character names (e.g. a, b, c)<br/>
    * counters 或 iterators 除外, 通常使用 `i`, `j`, `k`<br/>
  * 在 package/module name 中使用 dashes(-)<br/>
    * e.g. 創建一個module 叫做 `calculate-histogram.py`<br/>
  * 前後雙底線 `__double_leading_and_trailing_underscore__`<br/>
    * 為Python內部保留 reserved by Python<br/>
* 慣例 Convention<br/>
  * `internal`定義: 意指 僅使用於某個 module 或 以protected/private的形式存於某個class 的 變數或函示<br/>
  * 前綴單底線(`_`): 僅 慣例上代表, 該 變數或函示 為 internal 使用<br/>
    * 前綴單底線 不具備實際 internal 效應, 僅特殊情況下提供 internal 保護 (e.g. 在 `import * from` 時不會出現)<br/>
  * 前綴雙底線(`__`): 對 編譯器interpreter 有實際意義, 將使 變數或函示 變成 internal<br/>
    * e.g.<br/>
    * 有關 前綴單底線 與 前綴雙底線, 更多資訊可參考 <https://shahriar.svbtle.com/underscores-in-python><br/>
  * class 名稱 使用 `CapWords`, module 名稱 使用 `lower_with_under.py`<br/>
    * e.g. 避免出現 `from StringIO import StringIO` 的尷尬情況<br/>
* Naming Table<br/>
</details>

### 縮排 Indentation
<details><summary markdown="span">一律使用 4 spaces</summary>
* 永遠不可將 tabs 跟 spaces 混用<br/>
* 當需要以 多行 表示程式碼時, 可以考慮以下兩種方案<br/>
  * 使用 4 spaces 做縮排開頭<br/>
  * 使用 垂直方向 對齊 <br/>
* e.g.
</details>

#### 註解 Comments
* TBD


## 結語
* **保持一制性 BE CONSISTENT**
  * 如果你是在修改別人的 程式碼, 花點時間熟悉 既有的 coding style.
  * **"一致" 的風格 比 "正確" 的風格 更重要**


## References
* Google Style Guide: https://google.github.io/styleguide/pyguide.html
* PEP 8: https://www.python.org/dev/peps/pep-0008/
* PEP 257: https://www.python.org/dev/peps/pep-0257/
* https://shahriar.svbtle.com/underscores-in-python
