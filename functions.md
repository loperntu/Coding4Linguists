# 撰寫函式


## 函式與論元 Functions and arguments

函式在某個角度很像動詞。如「愛」這個動詞可以理解成攜帶兩個必要論元（愛者與被愛者）的函式。熟悉語義學的人應該會熟悉如下的表達：


```R
FunctionName <- function(arg1,arg2){
body
return(expression)
}
```

所以寫一個帶兩個論元的加法函式如下：

```
addFunc <- function(x,y){
result <- x + y
return(result)
}
# 呼叫函式
addFunc(34,2)
```


## Lexical Scoping


## Closure





## Performing Lazy Evaluation