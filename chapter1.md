# Reshaping data



- Reshaping a dataframe between wide and long

有些函式對於資料要是 **long format** 還是 **wide format** 要求不同。 轉換是需要的。

> When there are multiple measurements of the same subject, across time or using different tools, the data is often described as being in "**wide**" format if there is one observation row per subject with each measurement present as a different variable and "**long**" format if there is one observation row per measurement (thus, multiple rows per subject). 

 
![Long and Wide](/assets/Wide Format Transformationh.png)

- The `reshape2` package provides just that ability.




### Reshaping: melt and cast









### Reshaping data with`tidyr`

可以期待的套件。

> The R package tidyr, developed by Hadley Wickham, provides functions to help you organize (or reshape) your data set into tidy format. It’s particularly designed to work in combination with `magrittr` and `dplyr` to build a solid data analysis pipeline.


```r
install.packages("tidyr")
library(tidyr)
```

有四個動作：

- Collapse multiple columns together into key-value pairs (long data format): `gather(data, key, value, …)` 類似 `melt()`

- Spread key-value pairs into multiple columns (wide data format): `spread(data, key, value)` 類似 `cast()`

- Unite multiple columns into one: `unite(data, col, …)`

- Separate one columns into multiple: `separate(data, col, into)`


以 `USArrests data sets` 為例

```r
my_data <- USArrests[c(1, 10, 20, 30), ]
my_data

           Murder Assault UrbanPop Rape
Alabama      13.2     236       58 21.2
Georgia      17.4     211       60 25.8
Maryland     11.3     300       67 27.8
New Jersey    7.4     159       89 18.8

```

Row names 都是州名，所以我們先用 `cbind()` 來加入一個叫做 `state` 的 column。這樣資料就「整齊」一些，分析也較為容易。 

```r
my_data <- cbind(state = rownames(my_data), my_data)
my_data

                state Murder Assault UrbanPop Rape
Alabama       Alabama   13.2     236       58 21.2
Georgia       Georgia   17.4     211       60 25.8
Maryland     Maryland   11.3     300       67 27.8
New Jersey New Jersey    7.4     159       89 18.8

```
1. `gather()`: collapse columns into rows

`gather()` 可以將許多 columns 摺成 key-value pairs。這樣就從寬格 (wide format) 轉長格(long format)。像是 `reshape2` 的 `melt()` 做的事情。


```
語法： gather(data, key, value, ...)

data: A data frame
key, value: Names of key and value columns to create in output
…: Specification of columns to gather. Allowed values are:
variable names
  if you want to select all variables between a and e, use a:e
  if you want to exclude a column name y use -y
  for more options, see: dplyr::select()
```

  - Gather all columns except the column state

```r
my_data2 <- gather(my_data,
                   key = "arrest_attribute",
                   value = "arrest_estimate",
                   -state)
my_data2

        state arrest_attribute arrest_estimate
1     Alabama           Murder            13.2
2     Georgia           Murder            17.4
3    Maryland           Murder            11.3
4  New Jersey           Murder             7.4
5     Alabama          Assault           236.0
6     Georgia          Assault           211.0
7    Maryland          Assault           300.0
8  New Jersey          Assault           159.0
9     Alabama         UrbanPop            58.0
10    Georgia         UrbanPop            60.0
11   Maryland         UrbanPop            67.0
12 New Jersey         UrbanPop            89.0
13    Alabama             Rape            21.2
14    Georgia             Rape            25.8
15   Maryland             Rape            27.8
16 New Jersey             Rape            18.8

```
可以看到所有的 column names (除了 `state`) 都被摺疊成單一的 **key** column (`arrest_attribute`)，它們的 values 則被放到 **value** column (`arrest_estimate`).


  - Gather only Murder and Assault columns

 選擇特定的 columns 

```r
my_data2 <- gather(my_data,
                   key = "arrest_attribute",
                   value = "arrest_estimate",
                   Murder, Assault)
my_data2

   state UrbanPop Rape arrest_attribute arrest_estimate
1    Alabama       58 21.2           Murder            13.2
2    Georgia       60 25.8           Murder            17.4
3   Maryland       67 27.8           Murder            11.3
4 New Jersey       89 18.8           Murder             7.4
5    Alabama       58 21.2          Assault           236.0
6    Georgia       60 25.8          Assault           211.0
7   Maryland       67 27.8          Assault           300.0
8 New Jersey       89 18.8          Assault           159.0
```
Note that, the two columns Murder and Assault have been collapsed and the remaining columns (state, UrbanPop and Rape) have been duplicated.



- Gather all variables between Murder and UrbanPop

```r
my_data2 <- gather(my_data,
                   key = "arrest_attribute",
                   value = "arrest_estimate",
                   Murder:UrbanPop)
my_data2

        state Rape arrest_attribute arrest_estimate
1     Alabama 21.2           Murder            13.2
2     Georgia 25.8           Murder            17.4
3    Maryland 27.8           Murder            11.3
4  New Jersey 18.8           Murder             7.4
5     Alabama 21.2          Assault           236.0
6     Georgia 25.8          Assault           211.0
7    Maryland 27.8          Assault           300.0
8  New Jersey 18.8          Assault           159.0
9     Alabama 21.2         UrbanPop            58.0
10    Georgia 25.8         UrbanPop            60.0
11   Maryland 27.8         UrbanPop            67.0
12 New Jersey 18.8         UrbanPop            89.0


```

> How to use gather() programmatically inside an R function?
> You should use the function gather_() which takes character vectors, containing column names, instead of unquoted column names







`


