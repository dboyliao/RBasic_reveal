---
title       : DSC 2014
subtitle    : R Basic Tutorial
author      : Dboy
job         : Taiwan UseR Group for Hackers
framework   : revealjs        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax, bootstrap]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

---

<h1>
  <font color='navy'>DSC 2014</font>
</h1>
<h2>
  <font color='yellow'>R Basic Tutorial</font>
</h2>

<h3>
  <font color="wheat">Dboy</font>
</h3>


--- &vertical

# Why R?

***

# Why not R?

***

- 1. It is FREE!
- 2. It is open!
- 3. It is popular! ---> [Kaggle](https://www.kaggle.com/wiki/Software)
- 4. It is powerful!

***

<br>
<br>
It is cool to be a hacker!!
<br>
<img src="assets/img/cool_hacker.jpg" height="60%" width="60%" />
<br>
<a src='http://www.teachprivacy.com/category/phishing/'>圖片來源</a>
<p class="fragment">
Our Goal: Become a Cool Guy!
</p>

***

## Mini Project I: Barnsley Fern Fractal

<font size = '6'>
Work this cool picture out.<br>
And you can claim that you can do sketch by a computer!
<br>
<br>
</font>

<img src="assets/img/Barnsley.gif" height="70%" width="70%" />

***

## Mini Project II: Battleship

<img src="assets/img/battle_ship.gif" height="30%" width="30%" />

***

## 最後讓我們打個廣告XDD

接下來的系列課程:

- ETL
- Data Analysis
- Data Visulization

<br>
<p class='fragment'>
在今天的課程裡也會讓大家體驗一下每個課程的主題是什麼。
</p>

--- &vertical

# Syllabus

***

## Syllabus

<ul>
  <li><strong>DATA: Where the Story Begins</strong>
    <ul>
      <li>資料屬性</li>
      <li>資料形態</li>
    </ul>
  </li>
  <li><strong>Basic Operations - Phase I</strong>
    <ul>
      <li>Logical Operations: &, |, ==</li>
    </ul>
  </li>
  <li><strong>Subsetting - Phase I</strong>
    <ul>
      <li>Vector and List</li>
      <li>Matrix Subsetting - Phase I</li>
      <li>Data Frame Subsetting - Phase I</li>
    </ul>
  </li>
  <li>Subsetting - Phase II
    <ul>
      <li>Matrix Subsetting - Phase II</li>
      <li>Data Frame Subsetting - Phase II</li>
    </ul>
  </li>
</ul>

***

<ul>
  <li><strong>Merging</strong>
    <ul>
      <li>cbind v.s rbind</li>
    </ul>
  </li>
  <li><strong>Basic Operation - Phase II</strong>
    <ul>
      <li>Arithmetic Operations</li>
    </ul>
  </li>
  <li><strong>Loops and Control Flow</strong>
    <ul>
      <li>for</li>
      <li>if / else if / else</li>
      <li>while</li>
    </ul>
  </li>
  <li><strong>Function</strong>
    <ul>
      <li>Basic Syntex</li>
      <li>Scoping Rules</li>
    </ul>
  </li>
  <li><strong>Mini Project</strong>
    <ul>
      <li>Barnsley Fern Fractal</li>
      <li>Battleship</li>
    </ul>
  </li>
</ul>

--- &vertical

## package: DSC2014Tutorial

For the best tutorial experience:

<a href="https://github.com/TaiwanRUserGroup/DSC2014Tutorial">Installation</a>

<p class='fragment'>
  This package contains all codes and packages we need during this and other
  tutorial sessions.
</p>

***

Once you are done with installation:


```r
library("DSC2014Tutorial")
```

<p class='fragment'>
  Let's begin!
</p>

--- &vertical

# Data: Where the Story Begins

***

### 以資料屬性來分：
- Character (字串)
- Integer (整數)
- Numeric (雙浮點數 / 實數)
- Logical (邏輯值)
- Complex (複數)

***

### 以資料形態來分：
- 一般變數
- Vector
- Matrix
- Factor and Data Frame

***

## Examples


```r
(x <- 'R is easy to learn!') # 這是字串
(y <- 3) # 這是整數
(z <- pi) # 圓周率
```

```
## [1] "R is easy to learn!"
```

```
## [1] 3
```

```
## [1] 3.142
```

***


```r
(k <- 1 + 2i) # 複數
(boo1 <- TRUE) # TRUE (or T for short)
(boo2 <- FALSE) # FALSE (or F for short)
```

```
## [1] 1+2i
```

```
## [1] TRUE
```

```
## [1] FALSE
```

--- &vertical

# Logical Operation

***

## Basic Operations: & (and), | (or), ==


```r
bol1 <- T; bol2 <- TRUE
bol3 <- F
('Dboy' == 'Dboy')
(bol1 == bol2)
(bol1 & bol2)
(bol3 | 4 > 5)
```

```
## [1] TRUE
```

```
## [1] TRUE
```

```
## [1] TRUE
```

```
## [1] FALSE
```

***


```r
4 > 2
1 >= 2
a <- NA
a == NA     # 要用is.na(a)才會傳回TRUE或FALSE。(另外還有is.nan())
is.na(a)
```

```
## [1] TRUE
```

```
## [1] FALSE
```

```
## [1] NA
```

```
## [1] TRUE
```

***

## Fun Time


```r
my_vec <- c(1, 2, 5, 90, 37)
ind <- my_vec >= 5
sum(ind)
```

```
## [1] 3
```
<p class='fragment'>Why???</p>

--- &vertical

# Subsetting Phase I
## Index

***

# Vector and List

***

## Vector and List

<div align='left'>
<ul>
  <li>c(): concatenation function</li>
  <li>範例：
  </li>
</ul>
</div>


```r
vec1 <- c(1, 2, 3)
vec2 <- c('a', 'b', 'c')
```
<div align='left'>
  <ul>
    <li>vector 中所有元素都必須是同一種資料屬性。</li>
    <li>Named Vector:</li>
  </ul>
</div>


```r
(Bob <- c(age = 27, height = 187, weight = 80))
```

```
##    age height weight 
##     27    187     80
```

***

## Funtime


```r
(mix_vec1 <- c('a', 2))
(mix_vec2 <- c(2, T))
```

```
## [1] "a" "2"
```

```
## [1] 2 1
```

<p class='fragment'>Why???</p>

***

## Useful Methods for Vector
- length(): 
  - 語法: **length(my_vec)**
  - 傳回 my_vec 的長度
- names():
 - 語法: **names(my_vec)**
 - 傳回 my_vec 各維度的名字。


***

## Examples


```r
vec <- c(4, 5, 6, 11, 5)
length(vec)
Bob
names(Bob)
```

```
## [1] 5
```

```
##    age height weight 
##     27    187     80
```

```
## [1] "age"    "height" "weight"
```

***

## Examples 

c() 也可以被用來結合兩個向量。


```r
x <- c(1:5)
y <- c(2, 4, 8)
z <- c(x, y)
z
```

```
## [1] 1 2 3 4 5 2 4 8
```

***

## Exercise

定義一個向量 me 記錄自己的身高(公分)、體重(公斤)與年齡。

<p class='fragment'>女性參考答案： me <- c(age = "18 forever", W = "secret", height="非常高佻")</p>

***

如果我還想記錄頭髮的顏色跟電話號碼呢?

<p class='fragment'>把 hair_color='Black' 存進去?</p>
<p class='fragment'>如果電話是 +886 911333966 呢?</p>
<p class='fragment'>都用字串存好嗎?</p>

***

## List

- list 是非常方便好用的資料形態。尤其是需儲存不同類型資料的時候，特別好用。

- 還記得剛剛提過的優先順序嗎？


```r
c(1, '2')
c(1, T)
```

```
## [1] "1" "2"
```

```
## [1] 1 1
```

***

### 比較


```r
list(1, '2')
list(1, T)
```

```
## [[1]]
## [1] 1
## 
## [[2]]
## [1] "2"
```

```
## [[1]]
## [1] 1
## 
## [[2]]
## [1] TRUE
```

***


```r
data(iris)
(Bob <- list(age=27, weight = 80,
            favorite_data_name = 'iris', favorite_data = iris))
```

```
## $age
## [1] 27
## 
## $weight
## [1] 80
## 
## $favorite_data_name
## [1] "iris"
## 
## $favorite_data
##     Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
## 1            5.1         3.5          1.4         0.2     setosa
## 2            4.9         3.0          1.4         0.2     setosa
## 3            4.7         3.2          1.3         0.2     setosa
## 4            4.6         3.1          1.5         0.2     setosa
## 5            5.0         3.6          1.4         0.2     setosa
## 6            5.4         3.9          1.7         0.4     setosa
## 7            4.6         3.4          1.4         0.3     setosa
## 8            5.0         3.4          1.5         0.2     setosa
## 9            4.4         2.9          1.4         0.2     setosa
## 10           4.9         3.1          1.5         0.1     setosa
## 11           5.4         3.7          1.5         0.2     setosa
## 12           4.8         3.4          1.6         0.2     setosa
## 13           4.8         3.0          1.4         0.1     setosa
## 14           4.3         3.0          1.1         0.1     setosa
## 15           5.8         4.0          1.2         0.2     setosa
## 16           5.7         4.4          1.5         0.4     setosa
## 17           5.4         3.9          1.3         0.4     setosa
## 18           5.1         3.5          1.4         0.3     setosa
## 19           5.7         3.8          1.7         0.3     setosa
## 20           5.1         3.8          1.5         0.3     setosa
## 21           5.4         3.4          1.7         0.2     setosa
## 22           5.1         3.7          1.5         0.4     setosa
## 23           4.6         3.6          1.0         0.2     setosa
## 24           5.1         3.3          1.7         0.5     setosa
## 25           4.8         3.4          1.9         0.2     setosa
## 26           5.0         3.0          1.6         0.2     setosa
## 27           5.0         3.4          1.6         0.4     setosa
## 28           5.2         3.5          1.5         0.2     setosa
## 29           5.2         3.4          1.4         0.2     setosa
## 30           4.7         3.2          1.6         0.2     setosa
## 31           4.8         3.1          1.6         0.2     setosa
## 32           5.4         3.4          1.5         0.4     setosa
## 33           5.2         4.1          1.5         0.1     setosa
## 34           5.5         4.2          1.4         0.2     setosa
## 35           4.9         3.1          1.5         0.2     setosa
## 36           5.0         3.2          1.2         0.2     setosa
## 37           5.5         3.5          1.3         0.2     setosa
## 38           4.9         3.6          1.4         0.1     setosa
## 39           4.4         3.0          1.3         0.2     setosa
## 40           5.1         3.4          1.5         0.2     setosa
## 41           5.0         3.5          1.3         0.3     setosa
## 42           4.5         2.3          1.3         0.3     setosa
## 43           4.4         3.2          1.3         0.2     setosa
## 44           5.0         3.5          1.6         0.6     setosa
## 45           5.1         3.8          1.9         0.4     setosa
## 46           4.8         3.0          1.4         0.3     setosa
## 47           5.1         3.8          1.6         0.2     setosa
## 48           4.6         3.2          1.4         0.2     setosa
## 49           5.3         3.7          1.5         0.2     setosa
## 50           5.0         3.3          1.4         0.2     setosa
## 51           7.0         3.2          4.7         1.4 versicolor
## 52           6.4         3.2          4.5         1.5 versicolor
## 53           6.9         3.1          4.9         1.5 versicolor
## 54           5.5         2.3          4.0         1.3 versicolor
## 55           6.5         2.8          4.6         1.5 versicolor
## 56           5.7         2.8          4.5         1.3 versicolor
## 57           6.3         3.3          4.7         1.6 versicolor
## 58           4.9         2.4          3.3         1.0 versicolor
## 59           6.6         2.9          4.6         1.3 versicolor
## 60           5.2         2.7          3.9         1.4 versicolor
## 61           5.0         2.0          3.5         1.0 versicolor
## 62           5.9         3.0          4.2         1.5 versicolor
## 63           6.0         2.2          4.0         1.0 versicolor
## 64           6.1         2.9          4.7         1.4 versicolor
## 65           5.6         2.9          3.6         1.3 versicolor
## 66           6.7         3.1          4.4         1.4 versicolor
## 67           5.6         3.0          4.5         1.5 versicolor
## 68           5.8         2.7          4.1         1.0 versicolor
## 69           6.2         2.2          4.5         1.5 versicolor
## 70           5.6         2.5          3.9         1.1 versicolor
## 71           5.9         3.2          4.8         1.8 versicolor
## 72           6.1         2.8          4.0         1.3 versicolor
## 73           6.3         2.5          4.9         1.5 versicolor
## 74           6.1         2.8          4.7         1.2 versicolor
## 75           6.4         2.9          4.3         1.3 versicolor
## 76           6.6         3.0          4.4         1.4 versicolor
## 77           6.8         2.8          4.8         1.4 versicolor
## 78           6.7         3.0          5.0         1.7 versicolor
## 79           6.0         2.9          4.5         1.5 versicolor
## 80           5.7         2.6          3.5         1.0 versicolor
## 81           5.5         2.4          3.8         1.1 versicolor
## 82           5.5         2.4          3.7         1.0 versicolor
## 83           5.8         2.7          3.9         1.2 versicolor
## 84           6.0         2.7          5.1         1.6 versicolor
## 85           5.4         3.0          4.5         1.5 versicolor
## 86           6.0         3.4          4.5         1.6 versicolor
## 87           6.7         3.1          4.7         1.5 versicolor
## 88           6.3         2.3          4.4         1.3 versicolor
## 89           5.6         3.0          4.1         1.3 versicolor
## 90           5.5         2.5          4.0         1.3 versicolor
## 91           5.5         2.6          4.4         1.2 versicolor
## 92           6.1         3.0          4.6         1.4 versicolor
## 93           5.8         2.6          4.0         1.2 versicolor
## 94           5.0         2.3          3.3         1.0 versicolor
## 95           5.6         2.7          4.2         1.3 versicolor
## 96           5.7         3.0          4.2         1.2 versicolor
## 97           5.7         2.9          4.2         1.3 versicolor
## 98           6.2         2.9          4.3         1.3 versicolor
## 99           5.1         2.5          3.0         1.1 versicolor
## 100          5.7         2.8          4.1         1.3 versicolor
## 101          6.3         3.3          6.0         2.5  virginica
## 102          5.8         2.7          5.1         1.9  virginica
## 103          7.1         3.0          5.9         2.1  virginica
## 104          6.3         2.9          5.6         1.8  virginica
## 105          6.5         3.0          5.8         2.2  virginica
## 106          7.6         3.0          6.6         2.1  virginica
## 107          4.9         2.5          4.5         1.7  virginica
## 108          7.3         2.9          6.3         1.8  virginica
## 109          6.7         2.5          5.8         1.8  virginica
## 110          7.2         3.6          6.1         2.5  virginica
## 111          6.5         3.2          5.1         2.0  virginica
## 112          6.4         2.7          5.3         1.9  virginica
## 113          6.8         3.0          5.5         2.1  virginica
## 114          5.7         2.5          5.0         2.0  virginica
## 115          5.8         2.8          5.1         2.4  virginica
## 116          6.4         3.2          5.3         2.3  virginica
## 117          6.5         3.0          5.5         1.8  virginica
## 118          7.7         3.8          6.7         2.2  virginica
## 119          7.7         2.6          6.9         2.3  virginica
## 120          6.0         2.2          5.0         1.5  virginica
## 121          6.9         3.2          5.7         2.3  virginica
## 122          5.6         2.8          4.9         2.0  virginica
## 123          7.7         2.8          6.7         2.0  virginica
## 124          6.3         2.7          4.9         1.8  virginica
## 125          6.7         3.3          5.7         2.1  virginica
## 126          7.2         3.2          6.0         1.8  virginica
## 127          6.2         2.8          4.8         1.8  virginica
## 128          6.1         3.0          4.9         1.8  virginica
## 129          6.4         2.8          5.6         2.1  virginica
## 130          7.2         3.0          5.8         1.6  virginica
## 131          7.4         2.8          6.1         1.9  virginica
## 132          7.9         3.8          6.4         2.0  virginica
## 133          6.4         2.8          5.6         2.2  virginica
## 134          6.3         2.8          5.1         1.5  virginica
## 135          6.1         2.6          5.6         1.4  virginica
## 136          7.7         3.0          6.1         2.3  virginica
## 137          6.3         3.4          5.6         2.4  virginica
## 138          6.4         3.1          5.5         1.8  virginica
## 139          6.0         3.0          4.8         1.8  virginica
## 140          6.9         3.1          5.4         2.1  virginica
## 141          6.7         3.1          5.6         2.4  virginica
## 142          6.9         3.1          5.1         2.3  virginica
## 143          5.8         2.7          5.1         1.9  virginica
## 144          6.8         3.2          5.9         2.3  virginica
## 145          6.7         3.3          5.7         2.5  virginica
## 146          6.7         3.0          5.2         2.3  virginica
## 147          6.3         2.5          5.0         1.9  virginica
## 148          6.5         3.0          5.2         2.0  virginica
## 149          6.2         3.4          5.4         2.3  virginica
## 150          5.9         3.0          5.1         1.8  virginica
```

***

<p class='fragment'>我們可以用 list 來儲存異質的資料。</p>
<p class='fragment'>但如何從中擷取出想要的資料呢?</p>
<p class='fragment'>在接下來的 Subsetting 單元中將一一介紹。</p>

--- &vertical

# Vector Subsetting
## Phase I

***

## Subsetting by Index

<div align='left'>
<code>
  <font size="6">
  Syntax: vec[index]
  </font>
</code>
<br>
Examples:
</div>


```r
vec <- c(1, 5, 10, 33, 6)
vec[3]
vec[length(vec)]
```

```
## [1] 10
```

```
## [1] 6
```

***

## Subsetting by Name

<div align='left'>
<code>
<font size="6">
Syntax: vec["name"]
</font>
</code>
</div>


```r
Dboy <- c(age=27, weight=82, height=172)
Dboy["age"]
```

```
## age 
##  27
```

***

# List Subsetting
## Phase I

***

## Subsetting by Index

<div align='left'>
<code>
  <font size="6">
    Syntax: a_list[index] or a_list[[index]]
  </font>
</code>
<br>
Examples:
</div>


```r
Bob[1]; class(Bob[1])
Bob[[1]]; class(Bob[[1]])
```

```
## $age
## [1] 27
```

```
## [1] "list"
```

```
## [1] 27
```

```
## [1] "numeric"
```

***

## Subsetting by Name

<div align='left'>
<code>
  <font size="6">
    Syntax: a_list["name"] or a_list[["name"]]
  </font>
</code>
<br>
Examples:
</div>


```r
Bob["age"]
Bob[["age"]]
```

```
## $age
## [1] 27
```

```
## [1] 27
```

--- &vertical

# Matrix Subsetting
## Phase I

***

## Matrix: First Look

<br>
<font size="6" color="SlateGray">
A Matrix is something looks like this:
</font>

<img src="assets/img/R_Basic_Matrix.png" height="100%" width="100%"/>

***

## Dimension

<br>
<font size="6" color="SlateGray">
A Matrix has two dimensions, denoted by i and j.<br>
i for row indexing, j for column indexing.
</font>

***

## Dimension

<br>
<font size="6" color="SlateGray">
 i alone can specify one row.
</font>

<img src="assets/img/R_Basic_Matrix_row.png" height="100%" width="100%"/>


***

## Dimension

<br>
<font size="6" color="SlateGray">
j alone can specify one column.
</font>

<img src="assets/img/R_Basic_Matrix_col.png" height="100%" width="100%"/>

***

## Dimension

<br>
<font size="6" color="SlateGray">
i together with j can specify one element in a matrix.
</font>

<img src="assets/img/R_Basic_Matrix_RowAndCol.png" height="100%" width="100%"/>

***

## Matrix in R

<div align='left'>
<code>
  <font size="5">
    Syntax: matrix(elements, nrow, ncol, byrow = FALSE)
  </font>
</code>
</div>


```r
M1 <- matrix(c(1:144), 12, 12)
```

<center>
<img src="assets/img/R_Basic_Matrix_ex.png" height="75%" width="75%"/>
</center>

***

## Matrix: Subsetting by Index.

<div align='left'>
<code>
  <font size='6'>
    Syntax: my_matrix[i, ] or my_matrix[, j]
  </font>
</code>
</div>


```r
M1[6, ]
```

```
##  [1]   6  18  30  42  54  66  78  90 102 114 126 138
```

<center>
<img src="assets/img/R_Basic_Matrix_ex_row.png" height="65%" width="65%"/>
</center>

***

## Matrix: Subsetting by Index


```r
M1[, 6]
```

```
##  [1] 61 62 63 64 65 66 67 68 69 70 71 72
```

<center>
<img src="assets/img/R_Basic_Matrix_ex_col.png" height="70%" width="70%"/>
</center>

***

## Matrix: Rename


```r
colnames(M1) <- LETTERS[1:12]
```

<center>
<img src="assets/img/R_Basic_Matrix_ex_name.png" height="75%" width="75%"/>
</center>


***

## Matrix: Subsetting by Name


```r
M1[, 'F']
```

```
##  [1] 61 62 63 64 65 66 67 68 69 70 71 72
```

<center>
<img src="assets/img/R_Basic_Matrix_ex_name_ref.png" height="65%" width="65%"/>
</center>

***

## Fun Time

What will happend to matrix Mat?

```r
Mat <- matrix(c(1:15), 3, 5)
Mat[3, 3] <- "Ha Ha!"    # t(Mat)
```

<pre class='fragment'><code>##      [,1] [,2] [,3]     [,4] [,5]
## [1,] &quot;1&quot;  &quot;4&quot;  &quot;7&quot;      &quot;10&quot; &quot;13&quot;
## [2,] &quot;2&quot;  &quot;5&quot;  &quot;8&quot;      &quot;11&quot; &quot;14&quot;
## [3,] &quot;3&quot;  &quot;6&quot;  &quot;Ha Ha!&quot; &quot;12&quot; &quot;15&quot;
</code></pre>

<p class='fragment'><font color="yellow"> Why? </font></p>

--- &vertical

# Data Frame Subsetting
## Phase I

***

## Data Frame: First Look

<center>
<br>
<font size="6" color="SlateGray">
We take iris data set for example
</font>
</center>
<center>
<img src="assets/img/iris.png" height="70%" width=70%>
</center>

***

## Dimension

<center>
<br>
<font size="6" color="SlateGray">
Similer to the matrix, a data frame also has two dimensions.
 <br>
</font>
    <center>
    <img src="assets/img/iris_index.png" height="70%" width="70%">
    </center>
</center>

***

## Data Frame: Subsetting by Index


```r
data(iris); iris <- iris[1:12, ];iris[6, ]
```

```
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 6          5.4         3.9          1.7         0.4  setosa
```

<center>
<img src="assets/img/iris_row.png" height="70%" width="70%">
</center>

***


```r
iris[, 2]
```

```
##  [1] 3.5 3.0 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 3.7 3.4
```

<center>
<img src="assets/img/iris_col.png" height="70%" width="70%">
</center>

***

## Data Frame: Subsetting by Column Name


```r
iris[, "Sepal.Width"]
```

```
##  [1] 3.5 3.0 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 3.7 3.4
```

<center>
<img src="assets/img/iris_col.png" height="70%" width="70%">
</center>

***

## Data Frame: Rename


```r
colnames(iris) <- c("Sepal.L", "Sepal.W", "Petal.L", "Petal.W", "Species")
iris
```

```
##    Sepal.L Sepal.W Petal.L Petal.W Species
## 1      5.1     3.5     1.4     0.2  setosa
## 2      4.9     3.0     1.4     0.2  setosa
## 3      4.7     3.2     1.3     0.2  setosa
## 4      4.6     3.1     1.5     0.2  setosa
## 5      5.0     3.6     1.4     0.2  setosa
## 6      5.4     3.9     1.7     0.4  setosa
## 7      4.6     3.4     1.4     0.3  setosa
## 8      5.0     3.4     1.5     0.2  setosa
## 9      4.4     2.9     1.4     0.2  setosa
## 10     4.9     3.1     1.5     0.1  setosa
## 11     5.4     3.7     1.5     0.2  setosa
## 12     4.8     3.4     1.6     0.2  setosa
```


***

## One Simple Way to Construct a Data Frame.


```r
my_list <- list(Age = c(17, 22, 38), B.Type = c("A", "B", "O"))
(my_data <- as.data.frame(my_list))
str(my_data)
```

```
##   Age B.Type
## 1  17      A
## 2  22      B
## 3  38      O
```

```
## 'data.frame':	3 obs. of  2 variables:
##  $ Age   : num  17 22 38
##  $ B.Type: Factor w/ 3 levels "A","B","O": 1 2 3
```

***

## Fun Time

> 1. 向你身邊的 5 個人詢問基本資料。(上課不忘交新朋友)
> 2. 將得到的資料存成一個 data frame。
> 3. 如果問不到.... NA 是你的好朋友。

--- &vertical

# Subsetting Phase II
## Indices

***

## Vector: Reference by Indices

In R, we use c() to specify multiple indices.

<div align='left'>
  Example:
</div>


```r
Dboy <- c(age=27, weight=82, height=172)
(Dboy)
(Dboy[c(1, 3)])
```

```
##    age weight height 
##     27     82    172
```

```
##    age height 
##     27    172
```

***

## Vector: Multi Indexing with Expression

<div align='left'>
Examples:
</div>


```r
data(cars)
speed <- cars[, "speed"]
speed[speed > 5]
```

```
##  [1]  7  7  8  9 10 10 10 11 11 12 12 12 12 13 13 13 13 14 14 14 14 15 15
## [24] 15 16 16 17 17 17 18 18 18 18 19 19 19 20 20 20 20 20 22 23 24 24 24
## [47] 24 25
```

***

## Vector: Multi Indexing with which()

<div align='left'>
<code>
  <font size="6">
    Syntax: which(expression)
  </font>
</code>
<br>
Examples:
</div>


```r
my_vec <- runif(30, 0, 1) # 用 runif 從(0, 1)均勻分佈中抽取 30 個值。
(ind <- which(my_vec > 0.5))
(my_vec[ind])
```

```
##  [1]  1  3  8  9 10 11 12 13 15 16 17 19 20 21 22 23 24 25
```

```
##  [1] 0.9638 0.8423 0.5757 0.5377 0.5155 0.6238 0.9371 0.6781 0.9303 0.6985
## [11] 0.9157 0.5766 0.6292 0.6930 0.6831 0.7012 0.9176 0.5749
```

***

## Vector: Multi Indexing with which()

<div align='left'>
<code>
  <font size="6">
    Syntax: which(expression)
  </font>
</code>
<br>
Examples:
</div>


```r
(ind <- which(names(Dboy) %in% c("age", "weight")))
Dboy[ind]
```

```
## [1] 1 2
```

```
##    age weight 
##     27     82
```


***

## List: Subsetting by Indices

Similarly, we use c() for multiple indexing in a list.

<div align='left'>
<code>
  <font size="6">
    Syntax: my_list[c(ind1, ind2, ...)]
  </font>
</code>
<br>
Example:
</div>


```r
Bob[c(1, 3)]
```

```
## $age
## [1] 27
## 
## $favorite_data_name
## [1] "iris"
```

***

## List: Subsetting with which()

<div align='left'>
Example:
</div>


```r
(names(Bob))
(ind <- which(names(Bob) %in% c("age", "favorite_data")))
```

```
## [1] "age"                "weight"             "favorite_data_name"
## [4] "favorite_data"
```

```
## [1] 1 4
```


***


```r
Bob[ind]
```

```
## $age
## [1] 27
## 
## $favorite_data
##     Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
## 1            5.1         3.5          1.4         0.2     setosa
## 2            4.9         3.0          1.4         0.2     setosa
## 3            4.7         3.2          1.3         0.2     setosa
## 4            4.6         3.1          1.5         0.2     setosa
## 5            5.0         3.6          1.4         0.2     setosa
## 6            5.4         3.9          1.7         0.4     setosa
## 7            4.6         3.4          1.4         0.3     setosa
## 8            5.0         3.4          1.5         0.2     setosa
## 9            4.4         2.9          1.4         0.2     setosa
## 10           4.9         3.1          1.5         0.1     setosa
## 11           5.4         3.7          1.5         0.2     setosa
## 12           4.8         3.4          1.6         0.2     setosa
## 13           4.8         3.0          1.4         0.1     setosa
## 14           4.3         3.0          1.1         0.1     setosa
## 15           5.8         4.0          1.2         0.2     setosa
## 16           5.7         4.4          1.5         0.4     setosa
## 17           5.4         3.9          1.3         0.4     setosa
## 18           5.1         3.5          1.4         0.3     setosa
## 19           5.7         3.8          1.7         0.3     setosa
## 20           5.1         3.8          1.5         0.3     setosa
## 21           5.4         3.4          1.7         0.2     setosa
## 22           5.1         3.7          1.5         0.4     setosa
## 23           4.6         3.6          1.0         0.2     setosa
## 24           5.1         3.3          1.7         0.5     setosa
## 25           4.8         3.4          1.9         0.2     setosa
## 26           5.0         3.0          1.6         0.2     setosa
## 27           5.0         3.4          1.6         0.4     setosa
## 28           5.2         3.5          1.5         0.2     setosa
## 29           5.2         3.4          1.4         0.2     setosa
## 30           4.7         3.2          1.6         0.2     setosa
## 31           4.8         3.1          1.6         0.2     setosa
## 32           5.4         3.4          1.5         0.4     setosa
## 33           5.2         4.1          1.5         0.1     setosa
## 34           5.5         4.2          1.4         0.2     setosa
## 35           4.9         3.1          1.5         0.2     setosa
## 36           5.0         3.2          1.2         0.2     setosa
## 37           5.5         3.5          1.3         0.2     setosa
## 38           4.9         3.6          1.4         0.1     setosa
## 39           4.4         3.0          1.3         0.2     setosa
## 40           5.1         3.4          1.5         0.2     setosa
## 41           5.0         3.5          1.3         0.3     setosa
## 42           4.5         2.3          1.3         0.3     setosa
## 43           4.4         3.2          1.3         0.2     setosa
## 44           5.0         3.5          1.6         0.6     setosa
## 45           5.1         3.8          1.9         0.4     setosa
## 46           4.8         3.0          1.4         0.3     setosa
## 47           5.1         3.8          1.6         0.2     setosa
## 48           4.6         3.2          1.4         0.2     setosa
## 49           5.3         3.7          1.5         0.2     setosa
## 50           5.0         3.3          1.4         0.2     setosa
## 51           7.0         3.2          4.7         1.4 versicolor
## 52           6.4         3.2          4.5         1.5 versicolor
## 53           6.9         3.1          4.9         1.5 versicolor
## 54           5.5         2.3          4.0         1.3 versicolor
## 55           6.5         2.8          4.6         1.5 versicolor
## 56           5.7         2.8          4.5         1.3 versicolor
## 57           6.3         3.3          4.7         1.6 versicolor
## 58           4.9         2.4          3.3         1.0 versicolor
## 59           6.6         2.9          4.6         1.3 versicolor
## 60           5.2         2.7          3.9         1.4 versicolor
## 61           5.0         2.0          3.5         1.0 versicolor
## 62           5.9         3.0          4.2         1.5 versicolor
## 63           6.0         2.2          4.0         1.0 versicolor
## 64           6.1         2.9          4.7         1.4 versicolor
## 65           5.6         2.9          3.6         1.3 versicolor
## 66           6.7         3.1          4.4         1.4 versicolor
## 67           5.6         3.0          4.5         1.5 versicolor
## 68           5.8         2.7          4.1         1.0 versicolor
## 69           6.2         2.2          4.5         1.5 versicolor
## 70           5.6         2.5          3.9         1.1 versicolor
## 71           5.9         3.2          4.8         1.8 versicolor
## 72           6.1         2.8          4.0         1.3 versicolor
## 73           6.3         2.5          4.9         1.5 versicolor
## 74           6.1         2.8          4.7         1.2 versicolor
## 75           6.4         2.9          4.3         1.3 versicolor
## 76           6.6         3.0          4.4         1.4 versicolor
## 77           6.8         2.8          4.8         1.4 versicolor
## 78           6.7         3.0          5.0         1.7 versicolor
## 79           6.0         2.9          4.5         1.5 versicolor
## 80           5.7         2.6          3.5         1.0 versicolor
## 81           5.5         2.4          3.8         1.1 versicolor
## 82           5.5         2.4          3.7         1.0 versicolor
## 83           5.8         2.7          3.9         1.2 versicolor
## 84           6.0         2.7          5.1         1.6 versicolor
## 85           5.4         3.0          4.5         1.5 versicolor
## 86           6.0         3.4          4.5         1.6 versicolor
## 87           6.7         3.1          4.7         1.5 versicolor
## 88           6.3         2.3          4.4         1.3 versicolor
## 89           5.6         3.0          4.1         1.3 versicolor
## 90           5.5         2.5          4.0         1.3 versicolor
## 91           5.5         2.6          4.4         1.2 versicolor
## 92           6.1         3.0          4.6         1.4 versicolor
## 93           5.8         2.6          4.0         1.2 versicolor
## 94           5.0         2.3          3.3         1.0 versicolor
## 95           5.6         2.7          4.2         1.3 versicolor
## 96           5.7         3.0          4.2         1.2 versicolor
## 97           5.7         2.9          4.2         1.3 versicolor
## 98           6.2         2.9          4.3         1.3 versicolor
## 99           5.1         2.5          3.0         1.1 versicolor
## 100          5.7         2.8          4.1         1.3 versicolor
## 101          6.3         3.3          6.0         2.5  virginica
## 102          5.8         2.7          5.1         1.9  virginica
## 103          7.1         3.0          5.9         2.1  virginica
## 104          6.3         2.9          5.6         1.8  virginica
## 105          6.5         3.0          5.8         2.2  virginica
## 106          7.6         3.0          6.6         2.1  virginica
## 107          4.9         2.5          4.5         1.7  virginica
## 108          7.3         2.9          6.3         1.8  virginica
## 109          6.7         2.5          5.8         1.8  virginica
## 110          7.2         3.6          6.1         2.5  virginica
## 111          6.5         3.2          5.1         2.0  virginica
## 112          6.4         2.7          5.3         1.9  virginica
## 113          6.8         3.0          5.5         2.1  virginica
## 114          5.7         2.5          5.0         2.0  virginica
## 115          5.8         2.8          5.1         2.4  virginica
## 116          6.4         3.2          5.3         2.3  virginica
## 117          6.5         3.0          5.5         1.8  virginica
## 118          7.7         3.8          6.7         2.2  virginica
## 119          7.7         2.6          6.9         2.3  virginica
## 120          6.0         2.2          5.0         1.5  virginica
## 121          6.9         3.2          5.7         2.3  virginica
## 122          5.6         2.8          4.9         2.0  virginica
## 123          7.7         2.8          6.7         2.0  virginica
## 124          6.3         2.7          4.9         1.8  virginica
## 125          6.7         3.3          5.7         2.1  virginica
## 126          7.2         3.2          6.0         1.8  virginica
## 127          6.2         2.8          4.8         1.8  virginica
## 128          6.1         3.0          4.9         1.8  virginica
## 129          6.4         2.8          5.6         2.1  virginica
## 130          7.2         3.0          5.8         1.6  virginica
## 131          7.4         2.8          6.1         1.9  virginica
## 132          7.9         3.8          6.4         2.0  virginica
## 133          6.4         2.8          5.6         2.2  virginica
## 134          6.3         2.8          5.1         1.5  virginica
## 135          6.1         2.6          5.6         1.4  virginica
## 136          7.7         3.0          6.1         2.3  virginica
## 137          6.3         3.4          5.6         2.4  virginica
## 138          6.4         3.1          5.5         1.8  virginica
## 139          6.0         3.0          4.8         1.8  virginica
## 140          6.9         3.1          5.4         2.1  virginica
## 141          6.7         3.1          5.6         2.4  virginica
## 142          6.9         3.1          5.1         2.3  virginica
## 143          5.8         2.7          5.1         1.9  virginica
## 144          6.8         3.2          5.9         2.3  virginica
## 145          6.7         3.3          5.7         2.5  virginica
## 146          6.7         3.0          5.2         2.3  virginica
## 147          6.3         2.5          5.0         1.9  virginica
## 148          6.5         3.0          5.2         2.0  virginica
## 149          6.2         3.4          5.4         2.3  virginica
## 150          5.9         3.0          5.1         1.8  virginica
```

***

# Matrix Subsetting
## Phase II

***

## Matrix: Subsetting with Indices

<div align='left'>
<code>
  <font size='6'>
    Syntax: my_matrix[c(rowind1, rowind2, ...), c(colind1, colind2, ...)]
  </font>
</code>
<br>
Example:
</div>


```r
M1[c(2, 4), 2:4]
```

```
##       B  C  D
## [1,] 14 26 38
## [2,] 16 28 40
```

<center>
<img src="assets/img/Matrix_Subsetting_2.png" width="60%" height="60%">
</center>

***

## Data Frame: Subsetting with Indices

<div align='left'>
<code>
  <font size='6'>
    Syntax: myDataFrame[c(rowind1, rowind2, ...), c(colind1, colind2, ...)]
  </font>
</code>
<br>
Example:
</div>


```r
data(iris); iris <- iris[1:12, ]
iris[c(2, 5), seq(from=1, to = 5, by = 2)]
```

```
##   Sepal.Length Petal.Length Species
## 2          4.9          1.4  setosa
## 5          5.0          1.4  setosa
```
<center>
<img src="assets/img/DataFrameSubsetting2.png" width="60%" height="60%">
</center>

***

# Merging
## rbind and cbind

***

## Merging: rbind

<font size="6">
  <strong>First Look:</strong>
</font>
<br>
<img src="assets/img/rbind.png" width="35%" height="35%">

<ul>
  <li class='fragment'>rbind: Row-like Binding (merge by column).</li>
  <li class='fragment'>Merge two data frames (or matrices) like rows.</li>
</ul>

***

<div align='left'>
<code>
  <font size='6'>
    Syntax: rbind(A, B) where A and B are two data frames or matrices
  </font>
</code>
<br>
Again, let's play with iris data set. <br>
Example:
</div>


```r
data(iris)
iris[1:3, ]
```

```
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 1          5.1         3.5          1.4         0.2  setosa
## 2          4.9         3.0          1.4         0.2  setosa
## 3          4.7         3.2          1.3         0.2  setosa
```


```r
iris[100:103, ]
```

```
##     Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
## 100          5.7         2.8          4.1         1.3 versicolor
## 101          6.3         3.3          6.0         2.5  virginica
## 102          5.8         2.7          5.1         1.9  virginica
## 103          7.1         3.0          5.9         2.1  virginica
```

***


```r
rbind(iris[1:3, ], iris[100:103, ])
```

```
##     Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
## 1            5.1         3.5          1.4         0.2     setosa
## 2            4.9         3.0          1.4         0.2     setosa
## 3            4.7         3.2          1.3         0.2     setosa
## 100          5.7         2.8          4.1         1.3 versicolor
## 101          6.3         3.3          6.0         2.5  virginica
## 102          5.8         2.7          5.1         1.9  virginica
## 103          7.1         3.0          5.9         2.1  virginica
```

***

## Merging: cbind

<font size="6">
**First Look**: 
</font>
  <br>
  <br>

<center>
<img src="assets/img/cbind.png" width="50%" height="50%">
</center>

<ul>
  <li class='fragment'>cbind: Column-like Binding (merge by row).</li>
  <li class='fragment'>Merge two data frames (or matrices) like columns.</li>
</ul>


***

## Merging: cbind

<div align='left'>
<code>
  <font size='6'>
    Syntax: cbind(A, B) where A and B are two data frames or matrices
  </font>
</code>
<br>
Our beloved iris data set. <br>
Example:
</div>


```r
(A <- iris[1:5, 2:4])
```

```
##   Sepal.Width Petal.Length Petal.Width
## 1         3.5          1.4         0.2
## 2         3.0          1.4         0.2
## 3         3.2          1.3         0.2
## 4         3.1          1.5         0.2
## 5         3.6          1.4         0.2
```


```r
(B <- iris[8:12, 1:2])
```

```
##    Sepal.Length Sepal.Width
## 8           5.0         3.4
## 9           4.4         2.9
## 10          4.9         3.1
## 11          5.4         3.7
## 12          4.8         3.4
```

***


```r
cbind(A, B)
```

```
##   Sepal.Width Petal.Length Petal.Width Sepal.Length Sepal.Width
## 1         3.5          1.4         0.2          5.0         3.4
## 2         3.0          1.4         0.2          4.4         2.9
## 3         3.2          1.3         0.2          4.9         3.1
## 4         3.1          1.5         0.2          5.4         3.7
## 5         3.6          1.4         0.2          4.8         3.4
```

***

## Fun Time

還記得剛剛我們怎麼交新朋友的嗎?

<ol>
  <li class='fragment'>向剛剛問過的新朋友多問兩個額外的資料，並合併至原來的 data frame。(cbind or rbind ?)</li>
  <li class='fragment'>再多問兩位新朋友，並把新朋友的資料合併至原來的 data frame。(cbind or rbind ?)</li>
</ol>

--- &vertical

# Sorting and Ordering

***

### The Difference Between sort() and order()

<font size="5">
- **sort()**: sort (or order) a vector or factor (partially) into ascending or descending order.
</font>
<font size="5">
- **order()**: order returns a permutation which rearranges its first argument into ascending or descending order, breaking ties by further arguments.
</font>

<center>
<img src="assets/img/Blah.jpg" width="40%" height="40%" class="fragment">
</center>

***

<center>
<img src="assets/img/What.png" width="50%" height="50%">
</center>

***

## Let the Code Reveals Itself

<div align='left'>Examples:</div>


```r
Sepal.Length <- iris[1:12, "Sepal.Length"]
(sort(Sepal.Length))
(order(Sepal.Length))
```

```
##  [1] 4.4 4.6 4.6 4.7 4.8 4.9 4.9 5.0 5.0 5.1 5.4 5.4
```

```
##  [1]  9  4  7  3 12  2 10  5  8  1  6 11
```

***

## Ordering by Multiple Arguments

<div align='left'>Examples:</div>


```r
ind <- order(iris[1:12, "Sepal.Length"], iris[1:12, "Sepal.Width"])
(iris_ordered <- iris[ind, ]) 
```

```
##    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 9           4.4         2.9          1.4         0.2  setosa
## 4           4.6         3.1          1.5         0.2  setosa
## 7           4.6         3.4          1.4         0.3  setosa
## 3           4.7         3.2          1.3         0.2  setosa
## 12          4.8         3.4          1.6         0.2  setosa
## 2           4.9         3.0          1.4         0.2  setosa
## 10          4.9         3.1          1.5         0.1  setosa
## 8           5.0         3.4          1.5         0.2  setosa
## 5           5.0         3.6          1.4         0.2  setosa
## 1           5.1         3.5          1.4         0.2  setosa
## 11          5.4         3.7          1.5         0.2  setosa
## 6           5.4         3.9          1.7         0.4  setosa
```

***

## Play With It And You Will Master It!

我們用房貸餘額資料來練習! (cl_info_other.csv)

之後會在 ETL 課程碰到它，也會學到進階的資料處理技巧。


***


```r
# read.table 小技巧。
tmp <- read.table(DSC2014Tutorial::ETL_file('cl_info_other.csv'), sep = ',',
                 stringsAsFactors = F, header = T, nrows = 100)
colClasses <- sapply(tmp, class)
DF <- read.table(DSC2014Tutorial::ETL_file('cl_info_other.csv'), sep = ',',
                 header = T, colClasses = colClasses)
```


<img src="assets/img/read_no_colClasses.png", height=80%, width=80% class='fragment'/>
<img src="assets/img/read_colClasses.png", height=80%, width=80% class='fragment'/>

***

## Exercises:

1. 顯示 DF 前 20 筆資料與所有欄位的名稱。
3. 將 mortgage_cnt < 2053 的資料另外儲存成 banks_below。
4. 將 mortgage_cnt >= 22538 的資料另外儲存成 banks_above。
5. 將 banks_below 與 banks_above 合併成 DF2。
6. 將 DF2 先依 mortgage_cnt 再依 mortgage_bal 排序。(Hint: order)

<br>

<div class='fragment'>
<font size='6'>
學員OS: 這作業實在太 trivial 了，簡直侮辱我的智慧。
</font>
</div>
<div class='fragment'>
<font size='6'>
接下來的 ETL 課程保證會滿足你的渴望!
</font>
</div>

***

## Useful Functions

給定一個名叫 data 的 data frame (or matrix)

- names(data): 傳回 data 的所有欄位名稱。

- nrow(data)/ncol(data): 傳回 data 的列 / 行數目。

- dim(data)

- head(data, n)/tail(data, n)/View(data)

***

# Factor

***

## Factor: First Look


```r
(Petal.W <- as.factor(iris[1:12, "Petal.Width"]))
```

```
##  [1] 0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 0.2 0.2
## Levels: 0.1 0.2 0.3 0.4
```
<p class='fragment'>有啥特別的? 不就多個 levels 嗎? 跟向量不是差不多?</p>

<p class='fragment'>同款就不同師父啊(台)</p>

***

## Try This!


```r
Petal.W <- as.numeric(Petal.W)
```

<div align='left'>
  <font color='yellow'>
    Which is the correct outcome?
  </font>
</div>

<ol>
  <li>0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 0.2 0.2</li>
  <li>"I" "love" "data" "science" "It's" "the" "coolest" "thing" "ever" </li>
  <li>2 2 2 2 2 4 3 2 2 1 2 2</li>
  <li>None of above.</li>
</ol>

<div align='left'>
<p class='fragment'>
  <font color='navy'>
    The answer is 3.
  </font>
</p>
<p class='fragment'>
  <font color='red'>
    But why?
  </font>
</p>
</div>

***

## The Answer

**This is what you really get**:


```r
Petal.W
as.numeric(Petal.W)
```

```
##  [1] 2 2 2 2 2 4 3 2 2 1 2 2
```

```
##  [1] 2 2 2 2 2 4 3 2 2 1 2 2
```

***

<center>
<img src="assets/img/What.png" width="50%" height="50%">
</cent>

***

## A Closer Look

<font size="6">
**Vector in R**
</font>
  <br>
<center>
<img src="assets/img/Vector.png" width="70%" height="70%">
</center>

***

## A Closer Look

<font size="6">
**Factor in R: A Key-Value Mapping**
</font>
  <br>
<center>
<img src="assets/img/Factor.png" width="70%" height="70%">
</center>

***

# Build-in Function
## factor()

***

## factor()

<div align='left'>
<code>
  <font size="6">
  Syntax: factor(x)
  </font>
</code>
<br>
Example:
</div>


```r
test_factor <- c(1, 3, 3, 5, 2, 4, 2, 5)
test_factor <- factor(test_factor)
```
<div class='fragment'>
<pre><code>## [1] 1 3 3 5 2 4 2 5
## Levels: 1 2 3 4 5
</code></pre>
</div>

***

## Build-in Function: factor()

<div align='left'>
<code>
  <font size="6">
    Syntax: factor(x)
  </font>
</code>
<br>
Example:
</div>


```r
levels(test_factor) <- c("A", "B", "C", "D", "E")
test_factor
```

```
## [1] A C C E B D B E
## Levels: A B C D E
```

***

## Pop Quiz

How can we correctly convert a factor into a vector? <br>

<div class='fragment' align='left'>
<font size='6'>Q: my_factor <- factor(seq(10, 1, -1))</font>
</div>

<div class='fragment' align='left'><font size='6'>Hint</font></div>
<ol>
  <li class='fragment'>my_vec <- seq(10, 1, by = -1)</li>
  <li class='fragment'>my_vec[c(3, 3, 5, 1, 6)]</li>
  <li class='fragment'>levels(my_factor): this will give you a vector of levels of a factor.</li>
</ol>


***

## The Answer


```r
(my_factor <- factor(seq(10, 1, -1)))
Levels <- levels(my_factor)
(my_vector <- Levels[as.numeric(my_factor)])
```

```
##  [1] 10 9  8  7  6  5  4  3  2  1 
## Levels: 1 2 3 4 5 6 7 8 9 10
```

```
##  [1] "10" "9"  "8"  "7"  "6"  "5"  "4"  "3"  "2"  "1"
```

--- &vertical

# Loops and Flow Control

***

## For Loop

### Syntex:

    for (iterator){
        #Do something here....
    } 

### Example: 土炮 sum()


```r
# 從 1 加到 10
final_result <- 0
for (i in 1:10){
        final_result <- final_result + i
}
final_result
```

```
## [1] 55
```


***

## 剛剛的例子有點兒無聊....

        # 讓 R 幫你驅邪避凶!!
        # This is for Mac.
        for (i in 1:5){
                system("say 'Nann Moll Ah Mi Tow Fo'")
                system("say 'Ah Men'")
        }
        # This is for Ubuntu.
        for (i in 1:5){
                system("espeak 'Nann Moll Ah Mi Tow Fo'")
                system("espeak 'Ah Men'")
        }
        # This is for Windows.
        for (i in 1:5){
                system("espeak NannMollAhMiTowFo")
                system("espeak AhMen")
        }

***

# Control Flow

***

### if / else
<div align='left'>Syntex:</div>

    if (condition_1){
        #Do something here....
    } else if (conditon_2){
        #Do something here
    } else {
        #Do something here
    }

<div align='left'>
Note: else if and else are optional.
</div>

***

## Exercise: SVM Classifier

<div align='left'>
<font size='6'>
Magic Vector: <br>
c(1.45284450, -0.04625854, 0.5211828, -1.003045, -0.4641298)
</font>

<p class='fragment'>(暫時)不要問我怎麼把這個向量生出來的。(汗)</p>
<p class='fragment'>或許你可以問助教，助教什麼都會!</p>
</div>

***

One simple way to get the data if you're using our package.


```r
data("RBasic_ForLoop_Ex")
```

***

## Exercise: SVM Classifier

<ol>
  <li class='fragment'>計算 X1 中某一筆資料與 magic_vector 內積的結果，並儲存為 inner。<br>sum(X1[i, ] * magic_vector), i 可以是1~100任何一個整數)</li>
  <li class='fragment'>如果 inner 大於或等於 0，print('setosa');反之，print('versicolor')</li>
  <li class='fragment'>執行 print(y1[i])，有何發現？</li>
</ol>

<br>
<div class='fragment'>
<font size='6' color='red'>
其他精彩的資料分析模型的理論與操作，敬請期待 Data Analysis 課程!
</font>
</div>

***

## While Loop

<div align='left'>
Syntex:
</div>

    while (condition_1){
        #Do something here....
    } 

<div align='left'>
Example:
</div>

    while (T){
            handsome <- readline('Are you handsome?[yes or no] ')
            if (handsome == 'yes'){
                    print('Really....!?')
            } else {
                    print('Now we are talking.')
                    break
            }
    }


***

## While Loop

<img src="assets/img/while.gif" height="60%" width="60%" />

### Exercise

<ol>
  <li class='fragment'>那如果要把上述程式改成電腦不斷詢問 "Do you like to code?" 呢?</li>
  <li class='fragment'>至於要回答 'yes' or 'no' 才會停....</li>
  <li class='fragment'>要如何避免使用者回答 'yes' 或 'no' 以外的東西呢?</li>
</ol>

--- &vertical

# Basic Operation
## Phase II

***

## Arithmetic Operations

<code class='ruby'>
  +, -, *, /, %/%, %%
</code>

<div align='left'>
<font size="5">
All these operations are vectorized. (element-by-element operation)
</font>
<br>
Examples:
</div>


```r
my_vec1 <- c(1, 3, 5, 7); my_vec2 <- c(2, 4, 6, 8)

(my_vec1 + my_vec2)
(my_vec1 * my_vec2)
```

```
## [1]  3  7 11 15
```

```
## [1]  2 12 30 56
```

***

## Matrix Operations
### Multiplication and Transpose

<div align='left'>
<code>Syntax: matrix1 %*% matrix2</code>
<br>
Example:
</div>


```r
set.seed(3690)
my_mat1 <- matrix(c(1:6), 2, 3)
my_mat2 <- matrix(runif(6), 3, 2)
(my_mat1 %*% my_mat2) 
```

```
##       [,1]  [,2]
## [1,] 5.577 5.534
## [2,] 7.263 7.478
```

***

### Solving Linear System

<div align='left'>
<code>
<font size="6">
Syntax: solve(A, b) <br>
</font>
</code>

<font size='6'>Given a linear system like this:</font>
<font size="12">
$$
A x = b
$$
</font>

<font size="6">
solve() will return:
</font>

<font size="12">
$$
x^*= A^{-1} b
$$
</font>
</div>

***

<div align='left'>Examples:</div>


```r
(A <- matrix(runif(9), 3, 3))
(A_inv <- solve(A))
(A %*% A_inv)
```

```
##        [,1]    [,2]    [,3]
## [1,] 0.4278 0.95646 0.05677
## [2,] 0.8543 0.06763 0.81184
## [3,] 0.5929 0.76707 0.11537
```

```
##        [,1]    [,2]   [,3]
## [1,] -4.458 -0.4842  5.601
## [2,]  2.775  0.1138 -2.166
## [3,]  4.460  1.7318 -5.713
```

```
##           [,1]       [,2]       [,3]
## [1,]  1.00e+00 -4.163e-17 -6.106e-16
## [2,]  0.00e+00  1.000e+00  0.000e+00
## [3,] -2.22e-16  5.551e-17  1.000e+00
```

***


```r
b <- c(1, 2, 3)
A_inv_b <- solve(A, b)
A %*% A_inv_b
```

```
##      [,1]
## [1,]    1
## [2,]    2
## [3,]    3
```

<br>
<div class='fragment'>
<font size='8' color='red'>
It's time for mini project!
</font>
</div>

--- &vertical 

# Mini Project I
## Barnsley Fern Fractal

***

## Barnsley Fern Fractal

<div align='left'>
・ 起始點: <br>
</div>
<img src="assets/img/Barnsley_Fern_0.png" height="20%" width="20%"/>

***

<div align='left'>
・ With 5% probability: <br>
</div>
<img src="assets/img/Barnsley_Fern_1.png" height="25%" width="25%"/>

<div align='left'>
・ With 81% probability: <br>
</div>
<img src="assets/img/Barnsley_Fern_2.png" height="42.5%" width="42.5%"/>

<div align='left'>
・ With 7% probability: <br>
</div>
<img src="assets/img/Barnsley_Fern_3.png" height="42.5%" width="42.5%"/>

<div align='left'>
・ With 7% probability: <br>
</div>
<img src="assets/img/Barnsley_Fern_4.png" height="42.5%" width="42.5%"/>


***


- 依此規則迭代出 40000 點，再把這些點畫成圖。
- 只要用我們有學過的 **for**/**if** 迴圈和矩陣運算就可以做到這件事。
- 你應該會看到:

<img src="assets/img/Barnsley_Fern_40000.png" height="70%" width="70%" />

***

## Tips

- 可以把迭代出來的點用一個 data.frame 存起來。(例如說存成 coor )

- 最後用 plot(x = coor[, 2], y = coor[, 1], plt = c(0, 10, -5, 5), cex = 0.1, asp = 1) 把它畫出來。

- 這些參數不懂沒關係，它們的唯一功能就只是讓圖變漂亮而已。(很多我也是 Google 來的XD)


***

## Template

One simple way to open the template if you're using our package.


```r
path <- DSC2014Tutorial::Basic_file("barnsley_fern_template.R")
utils::browseURL(path)
```

<div class='fragment'>
<font size='6'>
敬請期待 Data Visualization 教學課程。
</font>
</div>


***

## The Answer

<div align='left'>Reference answer</div>


```r
path <- DSC2014Tutorial::Basic_file("barnsley_fern_answer.R")
utils::browseURL(path)
```

--- &vertical

# Function
## Define Your Own Function

***

<div align='left'>
<font size="6">
Syntex: 
</font>
</div>

    my_function <- function(arg1, arg2 = arg2_default, ...){
            # do something here
            
            # return the result. (optional)
    }


<ol>
  <li class='fragment'>如果在最後沒有 return() ，R 會自動回傳<strong>最後一次運算</strong>的結果。</li>
  <li class='fragment'>強烈建議習慣性寫上 return()。</li>
</ol>

***

## Define Your Own Operation


```r
`%Q_Q%` <- function(x, y){
        return(2*x + 5*y)
}
2 %Q_Q% 3

`%(= ww =)%` <- function(x, y, z=3){
        return(x + 2*y + z)
}
2 %(= ww =)% 3
```

```
## [1] 19
```

```
## [1] 11
```

***

## Default Values and Scoping Rule

We use following example to demostrate how to set default values in function 
and the basic scoping rule in R.


```r
MyFunction <- function(x, y, z=3, ...){
        print("x, y, z:")
        print(c(x=x, y=y, z=z))
        print("The rest of args:")
        print(c(...))
        return(x + 2*y + 6*z + sum(...))
}
```

***

## Default Values and Scoping Rule


```r
MyFunction(x=1, y=3) # It works without z!! (By "default", z = 3)
MyFunction(1, 3, 5, 2, 9) 
```

```
## [1] "x, y, z:"
## x y z 
## 1 3 3 
## [1] "The rest of args:"
## NULL
```

```
## [1] 25
```

```
## [1] "x, y, z:"
## x y z 
## 1 3 5 
## [1] "The rest of args:"
## [1] 2 9
```

```
## [1] 48
```

***


```r
MyFunction(1, 3, 5, 2, z = 9)
MyFunction(1, 3, 5, y = 2, x = 9)
MyFunction(1, 3, 5, y = 2, x = 9)
```

```
## [1] "x, y, z:"
## x y z 
## 1 3 9 
## [1] "The rest of args:"
## [1] 5 2
```

```
## [1] 68
```

```
## [1] "x, y, z:"
## x y z 
## 9 2 1 
## [1] "The rest of args:"
## [1] 3 5
```

```
## [1] 27
```

```
## [1] "x, y, z:"
## x y z 
## 9 2 1 
## [1] "The rest of args:"
## [1] 3 5
```

```
## [1] 27
```

<div class='fragment'>
  <font color='red' size='6'>It is time for Mini Project II!</font>
</div>

--- &vertical

# Mini Project II
## Battleship

***

## Battleship

<img src="assets/img/battle_ship.gif" height="30%" width="30%" />

***

`接下來我們將一步步指導該如何造出這個 battleship()。`

<div align='left'>
<ul>
  <li>首先由電腦決定一個座標。</li>
  <li>定義一個 list 變數 map 如下</li>
</ul>
</div>


```r
map =list(c('O', 'O', 'O', 'O', 'O'),
          c('O', 'O', 'O', 'O', 'O'),
          c('O', 'O', 'O', 'O', 'O'),
          c('O', 'O', 'O', 'O', 'O'),
          c('O', 'O', 'O', 'O', 'O'))
```
<div>
<ul>
  <li>用一個 for 迴圈把 map 中的每一個項目 print 出來。</li>
  <li>定義一個變數 trial 並給予初始值 0 。(此變數將用於記錄玩家已經試過幾次)</li>
  <li>用一個 while 迴圈來判斷 trial 是否超過可嘗試次數。如果沒有，更新 map 並顯示適當訊息。若已超過， break 當前迴圈。</li>
</ul>
</div>


***

## Template

One simple way to open the template file if you are using our package.


```r
path <- DSC2014Tutorial::Basic_file("battleship_template.R")
utils::browseURL(path)
```


***

## Some Function You Might Need

<div align='left'>
<ul>
  <li>readline(msg)</li>
</ul>
</div>


```r
readline('Are you a girl?') # readline() 會把輸入的資料存成字串。
```

<div align='left'>
<ul>
  <li>sample.int(x, size)</li>
</ul>
</div>


```r
sample.int(5, 1)   # 從 1~5 中隨機抽取 1 個數字。
```

```
## [1] 1
```

<div align='left'>
<ul>
  <li>cat():</li>
</ul>
</div>


```r
print('I love R!'); cat('I love R!')
```

```
## [1] "I love R!"
```

```
## I love R!
```

***

## Battleship 成品範例 


```r
path <- DSC2014Tutorial::Basic_file("battleship_answer.R")
utils::browseURL(path)
```

--- &vertical

# Help Yourself by Yourself

***

## Why?

<ol>
  <li class='fragment'>By this time, you are already a R user.</li>
  <li class='fragment'>However, life sucks. Bugs and problems are everywhere.</li>
  <li class='fragment'>No one can give you a hand if you do not reach out.</li>
</ol>

***

## But How?

> 1. ?/??: helper function in R.
> 2. [Stack overflow](http://stackoverflow.com)
> 3. [Google](http://google.com/)


--- 

## Thanks for Your Attention!

