---
layout: page
title: Python Coding Style
category: clean_code
---

## 建議的 coding 格式

### `pylint`
<details><summary markdown="span">使用 `pylint` 檢查 程式碼</summary>
  
* 透過 `pip install pylint` 安裝
* `pylint XXX.py` 執行
* `pylint` 並非完美, 僅是一個輔助工具. 你應該事情況
  * 修改程式碼
  * 將部分報錯 加入 ignore list (過多報錯, 可能導致你忽略真正需要修改的資訊)
</details>

### 命名 Naming
<details><summary markdown="span">`module_name`, `package_name`, `ClassName`, `method_name`, `ExceptionName`, `function_name`, `GLOBAL_CONSTANT_NAME`, `global_var_name`, `instance_var_name`, `function_parameter_name`, `local_var_name`</summary>
  
* 不允許採用
  * 單一字元名稱 single character names (e.g. `a`, `b`, `c`)
    * counters 或 iterators 除外, 通常使用 `i`, `j`, `k`
  * 在 package/module name 中使用 dashes(`-`)
    * e.g. 創建一個module 叫做 `calculate-histogram.py`
  * 前後雙底線 `__double_leading_and_trailing_underscore__`
    * 為Python內部保留 reserved by Python
* 慣例 Convention
  * `internal`: 僅使用於某module 或 以protected/private的形式存於某class的 變數或函示
  * 前綴單底線(`_`): 僅 慣例上代表, 該 變數或函示 為 internal 使用
    * 前綴單底線 不具備實際 internal 效應, 僅特殊情況下提供 internal 保護
    * e.g. 在 `import * from` 時不會出現
  * 前綴雙底線(`__`): 對 編譯器interpreter 有實際意義, 將使 變數或函示 變成 internal
    * 舉下面例子,
 
```python
>>> class A(object):
...     def _internal_use(self):
...         pass
...     def __method_name(self):
...         pass
... 
>>> dir(A())
['_A__method_name', ..., '_internal_use']
```
  可以發現 前綴雙底線 `__method_name` 將被編譯器 自動取代成 `_A__method_name`<br/>
  這在處理 繼承 inherit 時是有幫助的
  
```python
>>> class B(A):
...     def __method_name(self):
...         pass
... 
>>> dir(B())
['_A__method_name', '_B__method_name', ..., '_internal_use']
```
    * 有關 前綴單底線 與 前綴雙底線, 更多資訊可參考 <https://shahriar.svbtle.com/underscores-in-python>
  * class 名稱 使用 `CapWords`, module 名稱 使用 `lower_with_under.py`
    * e.g. 避免出現 `from StringIO import StringIO` 的尷尬情況
* Naming Table
 
  Type | Public | Internal
  --- | --- | ---
  Packages |	lower_with_under	|
  Modules | lower_with_under | 	_lower_with_under
  Classes |	CapWords |	_CapWords
  Exceptions	| CapWords	|
  Functions |	lower_with_under() |	_lower_with_under()
  Global/Class Constants |	CAPS_WITH_UNDER |	_CAPS_WITH_UNDER
  Global/Class Variables |	lower_with_under	| _lower_with_under
  Instance Variables	| lower_with_under |	_lower_with_under (protected) or __lower_with_under (private)
  Method Names |	lower_with_under() |	_lower_with_under() (protected) or __lower_with_under() (private)
  Function/Method Parameters |	lower_with_under	|
  Local Variables |	lower_with_under	|
</details>

### 縮排 Indentation
<details><summary markdown="span">一律使用 4 `spaces`</summary>
  
* 永遠不可將 `tabs` 跟 `spaces` 混用
* 當需要以 多行 表示程式碼時, 可以考慮以下兩種方案
  * 使用 4 `spaces` 做縮排開頭
  * 使用 垂直方向 對齊
* e.g.
</details>

### 註解 Comments
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