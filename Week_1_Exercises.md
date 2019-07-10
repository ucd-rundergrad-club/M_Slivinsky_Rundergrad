---
title: "Week 1 Exercises and Questions"
author: "Mitchell"
date: "June 28, 2019"
output: 
  html_document: 
    keep_md: yes
---
Questions are **bolded**. 

### Module 3: Sequences of Numbers 


```r
my_seq <- seq(5,10,length=30)
my_seq
```

```
##  [1]  5.000000  5.172414  5.344828  5.517241  5.689655  5.862069  6.034483
##  [8]  6.206897  6.379310  6.551724  6.724138  6.896552  7.068966  7.241379
## [15]  7.413793  7.586207  7.758621  7.931034  8.103448  8.275862  8.448276
## [22]  8.620690  8.793103  8.965517  9.137931  9.310345  9.482759  9.655172
## [29]  9.827586 10.000000
```

```r
seq(along.with=my_seq)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30
```

```r
seq_along(my_seq)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30
```

```r
? `along.with= x`
```

```
## No documentation for 'along.with= x' in specified packages and libraries:
## you could try '??along.with= x'
```

```r
? `seq_along()`
```

```
## No documentation for 'seq_along()' in specified packages and libraries:
## you could try '??seq_along()'
```

**What is the actual function of 'along.with' and `seq_along` in the above code? Swirl never directly explained the code, and when I attempted to access the documentation, nothing came up.**  
* `length()` describes length of vector within argument 
* `rep(a, times = b)` generates a vector containing all elements of `a` repeated `b` times
* `rep(a, each = b)` generates a vector containing all elements of a `a` repeated `b` times, one after another

### Module 4: Vectors

>Vectors come in two different flavors: atomic vectors and lists. An atomic vector contains exactly one data type, whereas a list may contain multiple data types... numeric vectors, which are one type of atomic vector. Other types of atomic vectors include logical, character, integer, and complex  

* `a <- b (logical argument such as >, <=, ==, or !=) c` creates a new logical vector `a` containing a series of logical values that compare every element in vector `b` with those of `c` as defined by the logical argument
* Logical operators include `|` for union; `&` for intersection; `!A` for negation of `A`.   
* `a <- c("a", "b", "c")` creates a new character vector `a` with elements `"a"`, `"b"`, and `"c"`
* `paste(a, collapse = "q")` pushes all elements in `a` together to print a new character vector with length 1; between every element in `a`, the condition `q` is added
 * The paste function also changes all included numerical vectors into character vectors.
* `paste("a", "b", "c",..., sep = "q")` pushes `"a"`, `"b"`, `"c"`, etc. together to print a new character vector with length 1; between each element, the condition `q` is added
 * If any of the combined vectors are of length greater than 1, the vectors will be combined in order in a pairwise fashion; in other words, vector recycling occurs. Example: 

```r
boy <- c("Big", "angry")
paste("very", boy, sep = " ")
```

```
## [1] "very Big"   "very angry"
```

###Module 5: Missing Values

NA can be substituted for a value in a numerical vector, creating a numerical value that is **missing**.  
* `rnorm(a)`draws from the standard normal distribution `a` times and prints the result
* `sample(a,n)` draws from the vector (or vectors) `a` n times and prints the result
* `is.na(a)` assesses the numerical vector `a` for missing values and prints a new logical vector showing `TRUE` for each element of `a` that is missing, and vice versa for elements of `a` that are not missing  
Some applications of the above coding elements: 

```r
pesty <- c(NA, 2,21,5, 19, 15, 16, 6, 8)
sample_1 <- sample(pesty,5)
sample_2 <- sample(pesty,5)
sample_3 <- sample(pesty,5)
is.na(sample_1)
```

```
## [1] FALSE  TRUE FALSE FALSE FALSE
```

```r
is.na(sample_2)
```

```
## [1] FALSE FALSE FALSE  TRUE FALSE
```

```r
is.na(sample_3)
```

```
## [1] FALSE FALSE FALSE FALSE FALSE
```

When `sum(a)` is applied to a logical vector `a`, it sums all TRUE (1) and FALSE (0), thus printing a result that is the number of TRUE.
NaN is distinct from NA and represents a numerical value that is **not a number**. Examples include 

```r
0/0
```

```
## [1] NaN
```

```r
Inf-Inf
```

```
## [1] NaN
```

### Module 6: Subsetting Vectors 

>In this lesson, we'll see how to extract elements from a vector based on some conditions that we specify.

* `a[b]` selects some particular elements from vector `a` defined by vector `b`, creating a subset. 
 * The vector `b` is called an index vector and can be a logical vector, a vector of negative or positive integers, or a vector of character strings.
 * When `b` is a logical vector, the printed result is a subset defined by the logical argument. For example: 

```r
big <- c(2,3,4,5,NA)
big[big >= 3]
```

```
## [1]  3  4  5 NA
```

```r
big[is.na(big)]
```

```
## [1] NA
```

```r
bigger <- big[!is.na(big)]
bigger[bigger>=3]
```

```
## [1] 3 4 5
```

```r
big[!is.na(big) &big>=3]
```

```
## [1] 3 4 5
```
 
 * When `b` is a vector of positive integers, the printed result is a subset containing all entries of `a` that correspond to the positive integers. 
 * When `b` is a vector of negative integers, the printed result is a subset containing all entries of `a` that do not correspond to the negative integers. For example:   

```r
yup <- c(1,2,-3,-4)
yup[1:3]
```

```
## [1]  1  2 -3
```

```r
yup[c(1,3)]
```

```
## [1]  1 -3
```

```r
yup[c(-1,-3)]
```

```
## [1]  2 -4
```

```r
yup[-c(1,3)]
```

```
## [1]  2 -4
```

* Naming vectors
 * `a <- c(a=b, c=d, e=f)` creates a new named vector. The vector is a numerical vector containing elements `b`, `d`, and `f` with names, respectively, `a`, `c`, and `e`. 
 * `names(a)` will then give the names corresponding to the elements of `a`. 
 * `names()` could also be used to add names to elements of a numerical vector. Observe:  

```r
yee <- c(1,2,3)
names(yee) <- c("a", "b", "c")
yee
```

```
## a b c 
## 1 2 3
```

*`identical(a,b)` prints TRUE is `a` is identical to `b`
* For `a[b]`, when `a` is a names vector and `b` is a vector of character strings, the printed result will be a subset of `a` that contains the elements of `a` with names denoted by `b`.

### Matrrices and Data Frames

Matrices contain only a single class of data, while data frames can contain many different classes of data. 
* `dim(a)` gives the dimensions of `a`, a matrix or data frame. Is essentially `length()` for tabular data. It prints rows, then columns.
 *It can also be used to add values to the dim __attribute__ of a vector, creating a data frame. The frame's attributes could then be evaluated using `attributes(a)`. Observe: 

```r
hey <- c(2,3)
dim(hey) <- c(1,2)
attributes(hey)
```

```
## $dim
## [1] 1 2
```

Matrices could also be created using the `matrix()` command. Use `?matrix` to see more details. 
* `cbind()` combines columns. It can append a vector to a matrix.  

> Behind the scenes, the data.frame() function takes any number of arguments and returns a single object of class `data.frame` that is composed of the original objects.

*Much like `dim`, `colnames()` and `rownames()` can be used to both view the data of a data frame or to set the corresponding data. 

### Logic

New logical operators include: 
* `&&` is the same as `&`, except it only evaluates the first member of a vector(s). 
* `||` is the same as `|`, except it only evaluates the first member of a vector(s). 

### Looking at Data
Want so see how much space an object is taking up? Just use `object.size(object)`!
* When applied to a data frame, `names()` gives the column names.
* Whe applied to a data frame, `head` gives the top of the data set. Default is first 6 rows, which can be altered by including a numerical value in the argument.
* When applied to a data frame, `summary()` gives a summary of the output for each category (column). 
* When applied to a data frame, `table(dataframe$columnname)` gives a non-truncated summary of the specified column in the data. 
* When applied to a data frame, `str()` gives a summary of the data frame's structure. 

**Could we please go over the output for `str(plants)`? I understand that the command gives a broad summary of the overall data frame, but I'm not entirely understanding what the output data actually means.**

