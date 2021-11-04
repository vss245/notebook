# R

Language for statistical computing

#### Syntax:

- {} brackets for loops
- no terminating semicolons

#### Operators and loops:

- <- operator can be used instead of =

- ```R
  x <- c(2,5,3,9,8,11,6)
  count <- 0
  ```

- Loops:

- ```r
  for (val in x) {
  if(val %% 2 == 0)  count = count+1
  }
  print(count)
  ```

#### Data types:

- numeric
- strings
  - methods: paste (concat), grep (regex matches), gsub (find and replace), toupper, tolower
- factor (character strings with preset levels)
- boolean

#### Data structures:

- list - list(1:3, “a”) - can hold any types, can also contain other lists

- vector - c(1,2,3) - hold specific types

  - vector functions: rev(), unique(), table() - to see counts, sort()

- matrices and arrays - matrix(1:6, ncol=, nrow=), array(1:6)

  - t(m) to transpose, m %*% n to multiply, solve (m,n) - find m * x = n

- dataframes - list of equal length vectors, looks like a table

  - ```R
    df <- data.frame(x = 1:3, y = c("a", "b", "c"))
    ```

  - can be combined with rbind and cbind 

- sidenote: all objects can have attributes, e.g. attr(mylist, “my_attr”) <- “this is an attribute”

#### Subsetting and indexing:

- indexing matrices:

  - m[2,] - select row
  - m[,1] - select column

- x[c(1,3)] will return elements at specified positions (or -c(1,3) to omit)

- [] will simplify the results to the lowest possible dimensionality

- structures can also be indexed with TRUE/FALSE (a[c(TRUE, FALSE)])

- dataframes have named columns: 

  - ```R
    df <- data.frame(x = 1:3, y = 3:1, z = letters[1:3])
    
    df[df$x == 2, ]
    ```

  - dataframe methods: nrow, ncol, head (first 6 rows), view (all)

- to extract columns from dataframes, use [[]] e.g. mtcars[[1]]

- [] is for returning lists, [[]] is for single elements

#### Function declaration:

- ```r
  myfunc <- function(x) {
    return(x*2)
  }
  ```

#### Stats (very brief):

- exploring data:

  - head(), str() - structure, min(), max(), mean(), median(), sd(), quantile(), IQR() - interquartile range (summary will also give a neat output)

  - otherwise also:

  - ```R
    library(pastecs)
    stat.desc(dat)
    ```

- plots: plot(), hist(), boxplot(), dotplot(), qqplot() - for normality check

- modeling:

  - linear models: my_model <- lm(x ~ y, data = df)
  - generalized linear models: my_model <- glm(x ~ y, data = df)
  - t.test(x,y)
  - summary(my_model) - full info on model

#### Using libraries:

- install.packages(‘dplyr’)
- library(‘dplyr’) - to load library
- data(iris) - load a built-in dataset

#### Super-useful packages:

- ggplot2 - plotting
- dplyr - data manipulation
- tidyr - tidy data, used for cleaning
- shiny - small web applications
- knitr - can create reports
- mlr3 - machine learning

