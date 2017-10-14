# 向量

---

## 資料結構 Data structure

* 一組（2 個以上）相同或不同\*\*資料類型\*\*的資料元素組合在一起形成\*\*資料結構\*\*.
* R 提供 6 個基本的資料結構：\`vector\`, \`matrix\`, \`array\`, \`factor\`, \`list\`, \`data frame\`.
* 學習重點在於如何建立 create 與檢索 access

## 向量定義

* a vector is a data structure containing a collection of multiple values with the same type.

## 向量建立

* `c()`： A special function `c()` combines multiple values into a single vector object.

* `:` 可產生差距為 1 的等差數列向量。

* `seq()` 可產生等差數列向量，差距值可以自行決定。

* `rep()` 可產生重複數值的向量。


```

> g <- c(1,2,3)
> h <- c('me','you')
> i <- 1:6
> j <- seq(from=1, to=10, by=2)
> k <- rep(1:4, times=3, each=2)
```



---

## 向量運算

* 直接施行算術運算

```
> v <- c(1,2,3) 
> v + 2
[1] 3 4 5
```

* 不同長度的向量運算

```
> c(1,2,3,4,5,6) + c(100,200) 
[1] 101 202 103 204 105 206
```

---

## 向量檢索

```
> m <- c(2:10)
> m\[1\]
> m\[1:3\]
```

---


