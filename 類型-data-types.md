# 類型

---

## 資料類型 \(Data type\) 與基本運算 \(basic arithmetic\)

資料類型包含以下幾種，可用 `mode()` 函數判斷

* **數值型** (numeric) ：實數（可以寫成整數 integers，小數 floating numners，或 科學記述 scientific notations）

```r
b <- 8.31
mode(b)

```

* \*\*字符型 \(character\)\*\*：文字字串，放入 "" 或 '' 中

\`\`\`{r}

c &lt;- 'coding'

mode\(c\)

\`\`\`

---

\#\# 資料類型 \(Data type\) 與基本運算 \(basic arithmetic\)

* \*\*邏輯型 \(logical\)\*\*：\`TRUE\`\(T\) 和 \`FALSE\`\(F\) 兩個值

\`\`\`{r}

d &lt;- F

mode\(d\)

\`\`\`

* \*\*複數型 \(complex\)\*\* :取值包含虛數 $a+bi$

\`\`\`{r}

e &lt;- 2+3i

mode\(e\)

\`\`\`

---

\#\# NA and NULL

* NA \(\*missing\*\)

* NULL \(\*undefined\*\)


---

\#\# 資料類型的判斷與轉換

\| 類型 \| 意義 \| 判斷 \| 轉換 \|

\|-----------\|---------\|--------------\|--------------\|

\| numeric \| 數值 \| is.numeric\(\) \| as.numeric\(\) \|

\| character \| 字符 \| is.character\(\) \| as.character\(\) \|

\| logical \| 邏輯 \| is.logical\(\) \| as.logical\(\) \|

\| complex \| 複數 \| is.complex\(\) \| as.complex\(\) \|

\| NA \| 缺失 \| is.na\(\) \| as.na\(\) \|

\`\`\`{r}

is.character\(b\)

as.character\(b\)

\`\`\`

---

## 類型強制轉換 \(type coercion\)：

## 

- If an R object contains both numeric and logical elements, the mode of that object will be numeric and in that case the logical element automatically gets converted to numeric. 

 - if any R object contains a character element along with both numeric and logical elements, it automatically converts to the character mode.

\`\`\`{r}

\# R object containing both numeric and logical element

x &lt;- c\(2, 4, TRUE, 6, FALSE, 8\); mode\(x\)

\# R object containing character, numeric, and logical elements

y &lt;- c\(1,2,TRUE,FALSE,"a"\); mode\(y\)

\`\`\`









---

## Modes and classes of R objects

* 變數命名規則舉例：cannot start with numbers; it will start with a character or underscore; no special character allowed, such as @, \#, $, and \*.

* 存入變數後，它就是個物件 \(object\)。兩種最重要的物件屬性 \(attribute\) 是 \`class\` 與 \`mode\` \(\*numeric, character\*, \*logical\*, \*function\*\).

  * The \`mode\(\)\` returns the mode of R objects. 表示物件在記憶體中是何種類型存儲的；類別概念以後再談。


