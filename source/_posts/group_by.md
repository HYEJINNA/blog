---
title: "group_by(), summarise()"
output: 
 html_document:
    keep_md: true
date: '2022-06-21'
---




```r
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
mpg1<-read.csv("data/mpg1.csv", stringsAsFactors = F)
```


```r
mpg1 %>% 
  group_by(trans) %>% #trans범주로 분류
  summarise(n=n()) %>%  #trans 범주별 데이터 빈도 구하기
  mutate(total=sum(n), 
       pct=n/total*100)
```

```
## # A tibble: 2 × 4
##   trans      n total   pct
##   <chr>  <int> <int> <dbl>
## 1 auto     157   234  67.1
## 2 manual    77   234  32.9
```

