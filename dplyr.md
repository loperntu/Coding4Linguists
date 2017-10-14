# dplyr: the essential data manipulation toolset

- 資料分析超級瑞士刀。
- 用 **chaining** 的方式寫程式，結合 `ggplot2` for rapid data exploration and transformation.
- Intuitive to write and easy to read, especially when using the *chaining* syntax- Fast on data frames



In data wrangling, what are the main tasks?

- Filtering rows (to create a subset)
- Selecting columns of data (i.e., selecting variables)
- Adding new variables
- Sorting
- Aggregating

Data manipulation 可歸納成五個基本動作：`filter()`, `select()`, `arrange()`, `mutate()`, `summarise()`。
> 注意：直行（VAR）橫列 (OBS)


dplyr gives you tools to do these tasks, and it does so in a way that streamlines the analytics workflow. 
- 篩選 `filter()`: 按給定的邏輯判斷篩選出符合要求的 OBS, 類似於 `subset()`。
- 選擇 `select()` : 用 VAR 作參數來選擇 OBS。
- 排列 `arrange()`: 按給定的 VAR 依次對 OBS 進行排序。類似於 `order()`。
- 增行 `mutate()`: 對已有 VAR 進行運算並添加為新的 VAR。類似於 `transform()`。
- 摘要 `summarise()`: 對 df 調用其它函數進行 summarise, 並回傳一維結果。

First argument is a data frame, and subsequent arguments say what to do with data frame.





## `dplyr` 5 main commands 例解

- `tbl_df()` creates a 「local data frame」, which is simply a wrapper for a data frame that prints nicely.

``
qie <- read.csv("idiom_freq_all.csv")
qienum <-tbl_df(qie)
``

#### `filter()`: Row selection from the dara
- `filter()` subsets your data by keeping 

``
filter(qienum, AnBn==1)
``


### `select()`: 

Select allows you to select specific columns from your data.


``
select(qienum, idioms, AnBn, PTT_WomenTalk, China_text, pooled)
``

### `mutate()`

Mutate allows you to add variables to your dataset. Obviously, this is a really common task in any programming environment.

``
qienum2 <- mutate(qienum, news_all = China_text + Apple_text)
``

### `arrange()`

Arrange sorts your data. In base R, this is commonly done with `order()`, and the syntax is a bit of a pain.

### `summarize()`
Summarize allows you to compute summary statistics.

``
qienum %>%
summarize(avg_mean = mean(pooled))
``



## The Chain syntax


``
qienum.nAnB <- qienum %>% 
    mutate(news_all = China_text + Apple_text) %>%        select(idioms, nAnB, PTT_WomenTalk, PTT_Hate, PTT_Gossiping,PTT_AllTogether, China_text, Apple_text, news_all,pooled) %>% 
    filter(nAnB ==1) %>% 
    arrange(pooled)
``


## Rapid Data Exploration with dplyr and ggplot















