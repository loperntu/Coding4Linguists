有了基礎的 `R` 程式編寫概念，可以進入實際處理數據的階段。

# Data Manipulation

a majority of the time is dedicated to data cleaning and preprocessing \(80%\)

* it is always preferable to perform the operation within subgroups of a dataset to speed up the process. In the case of large-scale data, we can split the dataset, perform the manipulation or analysis, and then combine it into a single output again.

* R 的基本功能在處理大數據時花的時間較久。建議使用  `plyr` package


## The split-apply-combine strategy

The split-apply-combine strategy can be implemented using base R, but requires a large amount of code and is not memory or time efficient. To overcome this limitation, we discussed the `plyr` package, in which group-wise data manipulation can be implemented efficiently. \[The Split-Apply-Combine Strategy for Data Analysis\]\[1\]

* 我們用 \`iris\` 資料：This dataset contains the measurementsin centimeters of these variables: sepal length and width, and petal length and width, for 50 flowers from each of the three species of iris. The species are _Iris setosa_, _Iris versicolor_, and _Iris virginica_. 
* 假定要分別計算出 mean of each variable and for each species， 會怎麼做？

### **Split-apply-combine without a loop**

1. Split the iris dataset into three parts.
2. Remove the species name variable from the data.
3. Calculate the mean of each variable for the three different parts separately.
4. Combine the output into a single data frame.

```

# notice that during split step a negative 5 is used, 
# this negative 5 has been used to discard fifth column of the iris data that contains "species" information 
# and we do not need that column to calculate mean.

iris.set <- iris[iris$Species=="setosa",-5]
iris.versi <- iris[iris$Species=="versicolor",-5]
iris.virg <- iris[iris$Species=="virginica",-5]

# calculating mean for each piece (The apply step)
mean.set <- colMeans(iris.set)
mean.versi <- colMeans(iris.versi)
mean.virg <- colMeans(iris.virg)

# combining the output (The combine step)
mean.iris <- rbind(mean.set,mean.versi,mean.virg)

# giving row names so that the output could be easily understood
rownames(mean.iris) <- c("setosa","versicolor","virginica")






```

### Split-apply-combine with a loop

* In each iteration, we will split the data for each species and calculate the mean for each variable and then combine the output into a single data frame.

```R
# split-apply-combine using loop
# each iteration represents split
# mean calculation within each iteration represents apply step
# rbind command in each iteration represents combine step

mean.iris.loop <- NULL
for(species in unique(iris$Species)){
    iris_sub <- iris[iris$Species==species,]
    column_means <- colMeans(iris_sub[,-5])
    mean.iris.loop <- rbind(mean.iris.loop,column_means)} 

# giving row names so that the output could be easily understood
rownames(mean.iris.loop) <- unique(iris$Species)
```

* [\[1\]  http:\/\/www.jstatsoft.org\/v40\/i01\/paper](http://www.jstatsoft.org/v40/i01/paper)

