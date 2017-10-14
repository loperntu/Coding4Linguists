# 檔案輸入輸出



## 使用 R 讀取資料

先安裝
```r
install.package('XML')
install.package('jsonlite')
```
取得檔案的連結之後（可用「右鍵 > 複製連結」），將連結指定給 `url` 變數。


* CSV

  - 讀取 CSV 檔是 R 的必備功能，可以是用內建的 `read.csv()` or `read.table()` 函數來讀取；
  - 常見的挫折則會有檔案編碼（big5, utf-8）的問題，這時候則需要加上參數 `fileEncoding = "utf8"` or `fileEncoding = "big5"` 重新讀取一次。

```r
> url <- 'http://data.gov.tw/iisi/logaccess/2877?dataUrl=http://file.data.gov.tw/event/dataset.csv&ndctype=CSV&ndcnid=8693'
> y <- read.csv(url, sep = ",", stringsAsFactors = F, header = T, fileEncoding = "utf8")
> head(y)
```

* XML

    Extensible Markup Language 可延伸標示語言，則是另外一種常見的資訊交換格式，可允許使用者事先定義客制標籤（tags），在網頁與各式應用程式之間讀取及傳遞資料。
    - 我們可以用 XML 套件，進行資料讀取以及整理的工作。其中，`xmlToDataFrame` 是個超級貼心的功能，可以將格式化的 XML 文件，直接轉成 R 使用者熟悉的 `dataframe`。


```r
> library(XML)
> url <- 'http://data.gov.tw/iisi/logaccess/2879?dataUrl=http://file.data.gov.tw/event/dataset.xml&ndctype=XML&ndcnid=8693'
> x <- xmlParse(url, encoding = "utf8") # 以 xmlParse 解析 XML 檔案
> xmlfiles <- xmlRoot(x) # 將 root 設定到 content 層級（一個偷吃步的做法）
> y <- xmlToDataFrame(xmlfiles) # 轉換成 dataframe
> colnames(y) <- c('資料集提供機關','資料集名稱','瀏覽次數','下載次數','資料集評分')
```

* JSON
  
  對於工程師來說，JSON 是很熟悉的檔案格式，R 裡面也有熱心的開發者貢獻了套件，可以將 JSON 資料轉換成為 large list or dataframe 格式，使用方法如下：

```r
> library(jsonlite)
> url <- 'http://data.gov.tw/iisi/logaccess/2878?dataUrl=http://file.data.gov.tw/event/dataset.json&ndctype=JSON&ndcnid=8693'
> y <- fromJSON(url, flatten = TRUE)
> y <- as.data.frame(y$Records)
```

## 輸出存檔

將讀取完的資料存成 csv 或 RDA 檔

```r
write.csv(file = 'open.csv', y, fileEncoding = 'big5')
```
