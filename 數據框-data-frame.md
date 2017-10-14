# Data Frame

---

* A dataframe is similar to the matrix, but in a data frame, the columns can hold data elements of different types.

* 最常處理的資料結構 the most commonly used data type for most of the analysis.


* create, manipulate, access

---

## 建立

```
> iris.simple <- data.frame(Sepal.Length = c(5.1, 4.7,5.0),
              Sepal.Width = c(3.5, 3.2, 3.6), 
              Pedal.Length = c(1.4, 1.3,1.4))

# 確認
> nrow(iris.simple)
> ncol(iris.simple)

# 快速瀏覽
> head(iris.simple)
> names(iris.simple)
> summary(iris.simple)
```

---

## 檢索

* \`\[\]\`, \`$\`, \`subset\(\)\`

```
> iris.simple[,1]
> iris.simple$Sepal.Width
> iris.simple$Sepal.Width[2]  
> subset(iris.simple, Sepal.Length < 5)
```

---

## 操作

```
## cbind(), rbind() 
> names(iris.simple) 
> names(iris.simple)[1] <- "sepal.length" 

#> class(iris.simple)
#> class(iris.simple$Sepal.Width)
```

> 小秘訣：attach\(\), detach\(\)

* 基本統計 \`mean\(\), median\(\), sum\(\), min\(\), max\(\), sd\(\), ...\`

---

### 











