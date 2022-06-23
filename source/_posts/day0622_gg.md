---
title: "ggplot2"
output: 
  html_document:
    keep_md: true
date: '2022-06-22'
---



## ggplot2 강의
- 데이터 불러오기

```r
# install.packages("nycflights13")
# install.packages("tidyverse")

library(dplyr)
```

```
## 
## 다음의 패키지를 부착합니다: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
library(readxl)
library(ggplot2)

library(nycflights13)
library(tidyverse)
```

```
## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
```

```
## ✔ tibble  3.1.7     ✔ purrr   0.3.4
## ✔ tidyr   1.2.0     ✔ stringr 1.4.0
## ✔ readr   2.1.2     ✔ forcats 0.5.1
```

```
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

```r
who_disease <- read_xlsx("data/who_disease.xlsx")


# 기본 시각화
ggplot(who_disease, aes(x = year, y = cases))+
  # 그래프 종류
  geom_point()
```

![](/images/0622gg/unnamed-chunk-1-1.png)<!-- -->

```r
# 옵션 1. 투명도 주기
ggplot(who_disease, aes(x = year, y = cases))+
  # 그래프 종류
  geom_point(alpha = 0.1)
```

![](/images/0622gg/unnamed-chunk-1-2.png)<!-- -->

```r
# 옵션 2. 색상 변화
ggplot(who_disease, aes(x = year, y = cases))+
  # 그래프 종류
  geom_point(alpha = 0.1, colour = "red")
```

![](/images/0622gg/unnamed-chunk-1-3.png)<!-- -->

```r
ggplot(who_disease, aes(x = year, y = cases))+
  # 그래프 종류
  geom_point(alpha = 0.1, colour = "#F8A821")
```

![](/images/0622gg/unnamed-chunk-1-4.png)<!-- -->

```r
?geom_point
```

```
## httpd 도움말 서버를 시작합니다 ...
```

```
##  완료
```

- colour 입력 위치
  + geom_point(colour=red)
  + aes(x, y, colour = 칼럼명)
  

```r
str(iris)
```

```
## 'data.frame':	150 obs. of  5 variables:
##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
##  $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...
```

```r
ggplot(iris, aes(x = Sepal.Length,
                 y = Sepal.Width,
                 colour = Species,
                 size = Petal.Length))+
geom_point()
```

![](/images/0622gg/unnamed-chunk-2-1.png)<!-- -->


- 산점도: x축 수치형 연속형 데이터, y축 수치형 연속형 데이터 
- 

```r
ggplot(who_disease, aes(x = year, y = cases))+
  geom_point(alpha = 0.1)
```

![](/images/0622gg/unnamed-chunk-3-1.png)<!-- -->


- 히스토그램
 + 질병 데이터 region = AMR, year = 1980, disease = 백일해(pertussis)
 case > 0
 

```r
library(dplyr)
str(who_disease)
```

```
## tibble [43,262 × 6] (S3: tbl_df/tbl/data.frame)
##  $ region     : chr [1:43262] "EMR" "EUR" "AFR" "EUR" ...
##  $ countryCode: chr [1:43262] "AFG" "ALB" "DZA" "AND" ...
##  $ country    : chr [1:43262] "Afghanistan" "Albania" "Algeria" "Andorra" ...
##  $ disease    : chr [1:43262] "measles" "measles" "measles" "measles" ...
##  $ year       : num [1:43262] 2016 2016 2016 2016 2016 ...
##  $ cases      : num [1:43262] 638 17 41 0 53 0 0 2 99 27 ...
```

```r
data2 <- who_disease %>%
  filter(region == 'AMR',
         year == 1980,
         disease == 'pertussis',
         cases > 0) -> data2

ggplot(data2, aes(x = cases))+
  geom_histogram()
```

```
## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.
```

![](/images/0622gg/unnamed-chunk-4-1.png)<!-- -->
 
명료하지 않다



```r
ggplot(data2, aes(x = country, y = cases))+
  geom_col()+
  # 옵션
  coord_flip()
```

![](/images/0622gg/unnamed-chunk-5-1.png)<!-- -->



```r
ggplot(data2, aes(x = country, y = cases))+
  geom_col(fill = "blue")+
  # 옵션
  coord_flip()
```

![](/images/0622gg/unnamed-chunk-6-1.png)<!-- -->

#산점도 그래프 그리기

```r
library(ggplot2)
```



```r
diamonds <- ggplot2::diamonds
ggplot(diamonds, aes(x=carat, y=price))+geom_point()
```

![](/images/0622gg/unnamed-chunk-8-1.png)<!-- -->




# 막대그래프 그리기

```r
table(diamonds$cut)
```

```
## 
##      Fair      Good Very Good   Premium     Ideal 
##      1610      4906     12082     13791     21551
```

```r
ggplot(diamonds, aes(x=cut,y=price))+geom_bar(stat = "identity")
```

![](/images/0622gg/unnamed-chunk-11-1.png)<!-- -->


## ggplot() 정교하게 그리기 
- 산점도 그리기 

```r
diamonds <- ggplot2::diamonds
ggplot(diamonds, aes(x=carat,
                     y=price,
                     col=cut))+
  geom_point()
```

![](/images/0622gg/unnamed-chunk-12-1.png)<!-- -->

- 막대그래프에 2개 범주 내용 반영하기

```r
ggplot(diamonds, aes(x=color))+
  geom_bar()
```

![](/images/0622gg/unnamed-chunk-13-1.png)<!-- -->


```r
ggplot(diamonds, aes(x=color, fill=cut))+
  geom_bar()
```

![](/images/0622gg/unnamed-chunk-14-1.png)<!-- -->


```r
ggplot(diamonds, aes(x=color, fill=cut))+
  geom_bar(position = "fill")
```

![](/images/0622gg/unnamed-chunk-15-1.png)<!-- -->


- p219
선 그래프에 2개 범주 내용 반영

```r
leisure <- read.csv("data/leisure.csv")
str(leisure)
```

```
## 'data.frame':	200 obs. of  3 variables:
##  $ age    : int  2 2 3 3 4 4 5 5 6 6 ...
##  $ sex    : chr  "female" "male" "female" "male" ...
##  $ expense: num  25.8 21 30 16.3 25.7 ...
```


```r
ggplot(data=leisure, aes(x=age, y=expense))+
  geom_line()
```

![](/images/0622gg/unnamed-chunk-17-1.png)<!-- -->


```r
ggplot(data=leisure, aes(x=age,
                         y=expense,
                         col=sex))+
  geom_line()
```

![](/images/0622gg/unnamed-chunk-18-1.png)<!-- -->


```r
ggplot(data=leisure, aes(x=age,
                         y=expense,
                         col=sex))+
  geom_line(size=1.5, linetype=6)
```

![](/images/0622gg/unnamed-chunk-19-1.png)<!-- -->


## 막대그래프의 순서변경
- reorder()

```r
mpg1 <- read.csv("data/mpg1.csv",
                 stringsAsFactors = F)

# 데이터 가공
drv_hwy <- mpg1 %>% 
  group_by(drv) %>% 
  summarise(mean_hwy=mean(hwy))
```

오름차순

```r
ggplot(data = drv_hwy, aes(x=reorder(drv,mean_hwy), y=mean_hwy))+
  geom_col()
```

![](/images/0622gg/unnamed-chunk-21-1.png)<!-- -->

내림차순

```r
ggplot(data = drv_hwy, aes(x=reorder(drv,-mean_hwy), y=mean_hwy))+
  geom_col()
```

![](/images/0622gg/unnamed-chunk-22-1.png)<!-- -->



```r
ggplot(data = drv_hwy, aes(x=drv, y=mean_hwy))+
  geom_col()+
  labs(
    title = "그래프 제목을 입력하세요",
    subtitle = "그래프 소제목을 입력하세요",
    x="x변수명을 입력하세요",
    y="y변수명을 입력하세요",
    caption = "데이터 출처를 입력하세요"
  )
```

![](/images/0622gg/unnamed-chunk-23-1.png)<!-- -->


