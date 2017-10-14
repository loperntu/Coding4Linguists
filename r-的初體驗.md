# R 的初體驗

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

