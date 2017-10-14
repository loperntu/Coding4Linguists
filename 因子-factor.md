# Factor

---



* The factor class is for categorical data, which are commonly seen in data frame.

* Factors can be ordered \(like childrens' grade levels\) or unordered \(like gender\)


\`\`\`{r,echo=FALSE}

factor\(c\("female", "female", "male", NA, "female"\)\)

\# The "levels" are the values the categorical data can take

\# Note that missing data does not enter the levels

levels\(factor\(c\("male", "male", "female", NA, "female"\)\)\) \# "female" "male"

\# If a factor vector has length 1, its levels will have length 1, too

length\(factor\("male"\)\)

data\(infert\) \# "Infertility after Spontaneous and Induced Abortion"

levels\(infert$education\) \# "0-5yrs" "6-11yrs" "12+ yrs"

\`\`\`

