# R 的初體驗

## R

* 語言 language、編譯 compiler、程式環境 IDE
* The R programming language is \(originally\) used for statistical computing and graphics.

### R 的學習

### 自學教材課程

* [tryr](http:\\tryr.codeschool.com)

* [datacamp](https:\\www.datacamp.com\home\)

* [dataquest](https:\\www.dataquest.io\dashboard\)

* [resources](https:\\github.com\datasciencemasters\go\blob\master\r-resources.md\)

---

## RStudio 安裝

* RStudio is an open source Integrated Development Environment \(IDE\) for the R platform.

* `RStudio Desktop 0.99.903` 還是 [`Preview v 1.0.27`](https:\\www.rstudio.com\products\rstudio\download\preview%29 %28推薦\)

---

## RStudio 設定與熟悉

* 版型調整: \(Workspace\)、\(Console\)、\(Environment and History\)、\(Files, Plots, Packages, Help, Viewer\)

* 目錄結構 \(dsr: data, scripts, homework, etc\)

---

## 用 RStudio 還可以做很多事 \(to be continued...\)

* 做 [可重製 reproducible](http:\\rmarkdown.rstudio.com\lesson-1.html\)、[可調參數 Parameterized](http:\\rmarkdown.rstudio.com\developer_parameterized_reports.html\)、[互動型 interactive](http:\\rmarkdown.rstudio.com\lesson-14.html%29 筆記%28notebook%29 與報告 %28report\)

* 做投影片 \(presentation\)

* 做網站 \(website\) 與 web application \(using `shiny`\)

* 做「數位報表」\(dashboard\)

* 做專業科學文件 \(using $$\LaTeX$$\)

---

\`\`\`{r}

data\(\) \# browse pre-loaded data sets

data\(rivers\) \# get this one: "Lengths of Major North American Rivers"

?rivers

head\(rivers\) \# peek at the data set

length\(rivers\) \# how many rivers were measured?

summary\(rivers\) \# what are some summary statistics?

\`\`\`

---

\#\# R 的初體驗

\`\`\`{r}

\# make a histogram

hist\(rivers, col="blue", border="white", breaks=25\) \# play around with these parameters

\`\`\`

---

\#\# In-class Exercise

* 換看看顏色 \(用 \`colors\(\)\` 看 R 認識什麼顏色\)

\`\`\`{r}

hist\(log\(rivers\), col="sienna", border="white", breaks=25\)

\`\`\`

---

### 入門小秘訣

* \`ctrl + l\` 清除 console 的顯示內容。

* \`rm\(list=ls\(\)\)\` 清除 workspace 中的變數。

* 但請注意：R 也可以在終端機執行：對於日後在雲端伺服器工作者，特別是結合\*\*指令列 \(command line\)\*\* 很重要。

* 隨時知道妳在那裡：\`getwd\(\)\` and \`Set Working Directory\`

* use tab to get suggestions

* use ESC to interrupt

---

### 套件 package：安裝與載入 \(發佈在 CRAN 上的套件\)

```
> install.packages("ggplot2")
> library(ggplot2)
> qplot(Sepal.Length, Petal.Length, data = iris, color = Species, size = Petal.Width)
```

* \`require\(\)\`

之後提到的先安裝起來

```
> install.packages(c("abd", "acs", "arules", "arulesViz", "asympTest", "beanplot", "boot", "bootES", "ca", 
"choroplethr", "choroplethrMaps", "classInt", "cluster", "clustvarsel", "data.table", "dbscan", "devtools", 
"DMwR", "dplyr", "DT", "dygraphs", "epitools", "eurostat", "extremeStat", "flexdashboard", "forecast", 
"gamlss.tr", "gdata", "GGally", "ggExtra", "ggplot2", "ggseas", "googleVis", "gridExtra", "htmlTable", 
"htmlwidgets", "httr", "jsonlite", "kulife", "leaflet", "likert", "lubridate", "maps", "maptools", 
"mc2d", "mclust", "mgcv", "mvoutlier", "NeatMap", "orddom", "pairsD3", "polycor", "plotly", "pscl", 
"psych", "qcc", "quantreg", "RColorBrewer", "RCurl", "readxl", "reshape2", "rjags", "rmarkdown", "RODBC", 
"scales", "segmented", "shiny", "simpleboot", "sqldf", "strucchange", "survival", "survminer", "tidyr", 
"tolerance", "useful", "vcd", "vegan", "VIM", "XLConnect", "XML", "xtable", "zipcode", "zoo"), 
dependencies = TRUE)

> source("https://bioconductor.org/biocLite.R")
```

```
devtools::install_github("vqv/ggbiplot")
devtools::install_github("twitter/AnomalyDetection")
devtools::install_github("hrbrmstr/taucharts")
devtools::install_github("timelyportfolio/parcoords")
devtools::install_github("rasmusab/bayesian_first_aid")
```

---

### **Work Session Management**



