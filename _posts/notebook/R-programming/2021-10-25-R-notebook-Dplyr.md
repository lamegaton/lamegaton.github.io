---
layout: post
title: R Notebook - dplyr 
categories: tip
author: "Son Pham, Truc Pham"
meta: R
description: "Essential R"
---


# Dplyr
We are gonna go through filter(), arrange(), select(), mutate(), summarise(),  
group_by(), slice(), rename(), transmute(), sample_n(), sample_frac()  
  
dplyr:  
* first argument is a data frame  
* function  
* result is a new data frame  
## Pipe
%>% is pronounced THEN

## All-in-one Example
```r
manager <- c(1, 2, 3, 4, 5) 
date <- c("10/24/08", "10/28/08", "10/1/08", "10/12/08", "5/1/09") 
country <- c("US", "US", "UK", "UK", "UK") 
gender <- c("M", "F", "F", "M", "F") 
age <- c(32, 45, 25, 39, 99) 
q1 <- c(5, 3, 3, 0, 2) 
q2 <- c(4, 5, 0, 3, 2) 
q3 <- c(5, 2, 5, 4, 1) 
q4 <- c(5, 0, 5, NA, 2) 
q5 <- c(5, 5, 2, NA, 1) 
leadership <- data.frame(manager, date, country, gender, age, 
                         q1, q2, q3, q4, q5, stringsAsFactors=FALSE)
> leadership
leadership <- leadership %>%
	mutate()

  manager     date country gender age q1 q2 q3 q4 q5
1       1 10/24/08      US      M  32  5  4  5  5  5
2       2 10/28/08      US      F  45  3  5  2  5  5
3       3  10/1/08      UK      F  25  3  5  5  5  2
4       4 10/12/08      UK      M  39  3  3  4 NA NA
5       5   5/1/09      UK      F  99  2  2  1  2  1
library(dplyr) #A 
# add total_score and mean_score columns
leadership <- mutate(leadership, #B 
                     total_score = q1 + q2 + q3 + q4 + q5, #B 
                     mean_score = total_score / 5) #B 
> leadership
  manager     date country gender age q1 q2 q3 q4 q5 total_score mean_score
1       1 10/24/08      US      M  32  5  4  5  5  5          24        4.8
2       2 10/28/08      US      F  45  3  5  2  5  5          20        4.0
3       3  10/1/08      UK      F  25  3  5  5  5  2          20        4.0
4       4 10/12/08      UK      M  39  3  3  4 NA NA          NA         NA
5       5   5/1/09      UK      F  99  2  2  1  2  1           8        1.6
# recode or change item in variable gender to M::male, F::female
# this is similar to search and replace
leadership$gender <- recode(leadership$gender, #C 
                            "M" = "male", "F" = "female") #C 
> leadership
  manager     date country gender age q1 q2 q3 q4 q5 total_score mean_score
1       1 10/24/08      US   male  32  5  4  5  5  5          24        4.8
2       2 10/28/08      US female  45  3  5  2  5  5          20        4.0
3       3  10/1/08      UK female  25  3  5  5  5  2          20        4.0
4       4 10/12/08      UK   male  39  3  3  4 NA NA          NA         NA
5       5   5/1/09      UK female  99  2  2  1  2  1           8        1.6														
# recode is similar to renaming the row, and rename is for columns
# right to left
leadership <- rename(leadership, ID = "manager", sex = "gender")#D
> leadership
  ID     date country    sex age q1 q2 q3 q4 q5 total_score mean_score
1  1 10/24/08      US   male  32  5  4  5  5  5          24        4.8
2  2 10/28/08      US female  45  3  5  2  5  5          20        4.0
3  3  10/1/08      UK female  25  3  5  5  5  2          20        4.0
4  4 10/12/08      UK   male  39  3  3  4 NA NA          NA         NA
5  5   5/1/09      UK female  99  2  2  1  2  1           8        1.6

leadership <- arrange(leadership, sex, total_score) #E 
> leadership
  ID     date country    sex age q1 q2 q3 q4 q5 total_score mean_score
1  5   5/1/09      UK female  99  2  2  1  2  1           8        1.6
2  2 10/28/08      US female  45  3  5  2  5  5          20        4.0
3  3  10/1/08      UK female  25  3  5  5  5  2          20        4.0
4  1 10/24/08      US   male  32  5  4  5  5  5          24        4.8
5  4 10/12/08      UK   male  39  3  3  4 NA NA          NA         NA
> leadership <- arrange(leadership, sex, desc(total_score)) #E
> leadership
  ID     date country    sex age q1 q2 q3 q4 q5 total_score mean_score
1  2 10/28/08      US female  45  3  5  2  5  5          20        4.0
2  3  10/1/08      UK female  25  3  5  5  5  2          20        4.0
3  5   5/1/09      UK female  99  2  2  1  2  1           8        1.6
4  1 10/24/08      US   male  32  5  4  5  5  5          24        4.8
5  4 10/12/08      UK   male  39  3  3  4 NA NA          NA         NA

> leadership_ratings <- select(leadership, ID, mean_score) #F
> leadership_ratings
  ID mean_score
1  2        4.0
2  3        4.0
3  5        1.6
4  1        4.8
5  4         NA
leadership_men_high <- filter(leadership, #G
                              sex == "male" & total_score > 10) #G 
> leadership_men_high <- filter(leadership, #G
+                               sex == "male" & total_score > 10) #G
> leadership_men_high
  ID     date country  sex age q1 q2 q3 q4 q5 total_score mean_score
1  1 10/24/08      US male  32  5  4  5  5  5          24        4.8															
```

## filter()
```r
library('nycflights13')
library('dplyr')
filter(flights, month == 1, day == 1, dep_delay >= 15)

flights[flights$month == 1 & flights$day == 1 & flights$dep_delay >= 15, ]

# this is similar 
subset(flights, month == 1 & day == 1 & dep_delay >= 15)
# better 
```
filter(), with %in%, select specific values in a col 

```r
filter(flights, month %in% c(6,7,8))
```
## slice()  
slice() will cut by user input  
```r
slice(flights, c(1:3, 5200, 9000:9100))
```

## arrange(): order data
```r
arrange(flights, year, month, day)
```
### arrange in descending order
```r
arrange(flights, desc(dep_delay))
```

### sorting missing value
```r
df <- tibble(x = c(5, 2, NA))
arrange(df, x)
```
### select()
```r
# select columns by name
select(flights, year, month, day)

head(dplyr::select(flights, 'year', 'month', 'day'),5)

# Select all columns between year and day (inclusive)
head(dplyr::select(flights, year:day),2)

# the reason, dplyr::select is used because it may clash with other packages

# Select all columns except those from year to day (inclusive)
head(dplyr::select(flights, -(year:day)),3)
```
If the column names are stored quoted in a variable, they should be passed to the one_of argument.

```r

theCols <- c('flights', 'year', 'month','day')
select(flights, one_of(theCols))
```

We can also use everything() helper with select to move the selected columns to  
the beginning of a dataframe
Ex: Flights has 19 columns from year, month, day ... time_hour. If we want to move  
time_hour to the first column we can use select and everything()

```r
select(flights, time_hour, day, month, year, everything())
# A tibble: 336,776 x 19
   time_hour             day month  year dep_time sched_dep_time dep_delay
   <dttm>              <int> <int> <int>    <int>          <int>     <dbl>
 1 2013-01-01 05:00:00     1     1  2013      517            515         2
 2 2013-01-01 05:00:00     1     1  2013      533            529         4
 3 2013-01-01 05:00:00     1     1  2013      542            540         2
 4 2013-01-01 05:00:00     1     1  2013      544            545        -1
```
### Rename a variable (column)
select(df, something, name_to_be_change = current_name)  
Lets change tailnum to tail_num

```r
select(flights, flight, tail_num = tailnum)
   flight tail_num
    <int> <chr>
 1   1545 N14228
 2   1714 N24211
 3   1141 N619AA
 4    725 N804JB
 5    461 N668DN
```
Or if you want to keep every variable, you can use rename() function
rename(df, name_to_be_change = current_name) 
 
```r
rename(flights, tail_num = tailnum)
    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
 1  2013     1     1      517            515         2      830            819
 2  2013     1     1      533            529         4      850            830
 3  2013     1     1      542            540         2      923            850
```
### Select with other helper functions
- starts_with("abc"): matches names that begin with “abc”.
- ends_with("xyz"): matches names that end with “xyz”.
- contains("ijk"): matches names that contain “ijk”.
- matches("(.)\\1"): selects variables that match a regular expression. This
one matches any variables that contain repeated characters.
- num_range("x", 1:3) matches x1, x2 and x3.

```r
select(flights, contains(arr))
   arr_time sched_arr_time arr_delay carrier
      <int>          <int>     <dbl> <chr>
 1      830            819        11 UA
 2      850            830        20 UA
 3      923            850        33 AA
```

## Group_by()
- .by_group = TRUE for arrange()
- sample_n(), sample_frac()  

In the example below, we group dest to 105 group  
Then, we use 

```r
> by_dest <- group_by(flights, dest)
> by_dest
# A tibble: 336,776 x 19
# Groups:   dest [105]
    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
 1  2013     1     1      517            515         2      830            819
 2  2013     1     1      533            529         4      850            830
 
> delay <- summarise(by_dest,
+ 	count = n(),
+ 	dist = mean(distance, na.rm = TRUE),
+ 	delay = mean(arr_delay, na.rm = TRUE))
> delay
# A tibble: 105 x 4
   dest  count  dist delay
   <chr> <int> <dbl> <dbl>
 1 ABQ     254 1826   4.38
 2 ACK     265  199   4.85
 3 ALB     439  143  14.4
 4 ANC       8 3370  -2.5
 5 ATL   17215  757. 11.3
 6 AUS    2439 1514.  6.02
 7 AVL     275  584.  8.00
 
# Subset the data to only include frequently flown planes
# and distances < 3000
delay <- filter(delay, count > 20, dist < 3000)
delay
   dest  count  dist delay
   <chr> <int> <dbl> <dbl>
 1 ABQ     254 1826   4.38
 2 ACK     265  199   4.85
 3 ALB     439  143  14.4
 4 ATL   17215  757. 11.3
 5 AUS    2439 1514.  6.02
```

## Other useful functions for R
- n(): number of items in a group (observations)
- n_distinct(x): find distinct value in x
- first(x) = x[1]
- last(x) = x[n] = x[length(x)]

```r
> destinations <- group_by(flights, dest)
> destinations
# Groups:   dest [105]
    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
 1  2013     1     1      517            515         2      830            819
 2  2013     1     1      533            529         4      850            830
 3  2013     1     1      542            540         2      923            850
 4  2013     1     1      544            545        -1     1004           1022
 5  2013     1     1      554            600        -6      812            837
 6  2013     1     1      554            558        -4      740            728
 7  2013     1     1      555            600        -5      913            854
 
> summarise(destinations,
+ 	planes = n_distinct(tailnum),
+ 	flights = n() # this will count how many thing in a group
+ )
   dest  planes flights
   <chr>  <int>   <int>
 1 ABQ      108     254
 2 ACK       58     265
 3 ALB      172     439
 4 ANC        6       8
 5 ATL     1180   17215
 6 AUS      993    2439
 7 AVL      159     275
 8 BDL      186     443
 9 BGR       46     375
10 BHM       45     297

# we can verify by using 
count(filter(destinations, dest == "AUS"))
# Groups:   dest [1]
  dest      n
  <chr> <int>
1 AUS    2439
```


## Merging (base R)
```r
# merge option
flights.df <- merge(flights.df, cor, by.x=c("origin"), by.y=c("faa"))
flights.df <- merge(flights.df, cor, by.x=c("dest"), by.y=c("faa"),suffixes=c(".origin",".dest"))
```

## remove col/s in R
```r
N0EGMQ         
#find value in a col
flights %>% filter_all(any_vars(. %in% c('N0EGMQ', 'N10156')))




# sum them up by year


# this is NA: N267AT
planes %>% filter_all(any_vars(. %in% c('N267AT')))

# find values
flights %>% filter_all(any_vars(. %in% c('N0EGMQ', 'N10156')))
# because we just want to know the relation between 

#

planes_delay %>% data.frame(row.names = planes_delay$tailnum)

cor(select(planes_delay,!(arr_delay)), select(planes_delay,!(year)))

cor(arrange(select(planes,c(tailnum,year)),tailnum), arrange(select(flights,c(tailnum,arr_delay)),tailnum))

planes.delay <- planes.delay %>%   filter(across(everything(),~ !is.na(.)))

```

# Pull all of the departure-related columns
select(flights, contains("dep"))

# Pull all of the arrival and departure related columns
select(flights, 
       contains("dep"),
       contains("arr"))

```r
# Correlation matrix from mtcars
# with mpg, cyl, and disp as rows
# and hp, drat, and wt as columns
x <- mtcars[1:3]
y <- mtcars[4:6]
cor(x, y)
```

```r
by_dest <- group_by(flights, dest)
delay <- summarise(by_dest,
  count = n(),
  dist = mean(distance, na.rm = TRUE),
  delay = mean(arr_delay, na.rm = TRUE))

head(delay,3)
```

## inner_join
Joining three tables with the same variable

```r
sets
   set_num   name                                                  year theme_id
   <chr>     <chr>                                                <dbl>    <dbl>
 1 700.3-1   Medium Gift Set (ABB)                                 1949      365
 2 700.1.1-1 Single 2 x 4 Brick (ABB)                              1950      371
 3 700.B.2-1 Single 1 x 2 x 3 Window without Glass (ABB)           1950      371
 
inventories
      id version set_num 
   <dbl>   <dbl> <chr>   
 1     1       1 7922-1  

inventory_parts
   inventory_id part_num             color_id quantity
          <dbl> <chr>                   <dbl>    <dbl>
 1           21 3009                        7       50
 2           25 21019c00pat004pr1033       15        1
 3           25 24629pr0002                78        1
 4           25 24634pr0001                 5        1
 
sets %>%
	inner_join(inventories, by = "set_num") %>%
	inner_join(inventory_parts, by = c("id" = "inventory_id"))

sets
   set_num name           year theme_id    id version part_num color_id quantity
   <chr>   <chr>         <dbl>    <dbl> <dbl>   <dbl> <chr>       <dbl>    <dbl>
 1 700.3-1 Medium Gift ~  1949      365 24197       1 bdoor01         2        2
 2 700.3-1 Medium Gift ~  1949      365 24197       1 bdoor01        15        1
 3 700.3-1 Medium Gift ~  1949      365 24197       1 bdoor01         4        1
 4 700.3-1 Medium Gift ~  1949      365 24197       1 bslot02        15        6
```

`parts` has 3 columns part_num, name, and part_cat_id
`part_categories` has id, name
when we do 
`parts %>% 
inner_join(part_categories, by = c("part_cat_id" = "id"))`

All parts columns will be the input of inner_join, when we state part_cat_id = id
inner_join will take the name on the left to be the name of final column

```r
parts
# A tibble: 17,501 x 3
   part_num   name                                                      part_cat_id
   <chr>      <chr>                                                           <dbl>
 1 0901       Baseplate 16 x 30 with Set 080 Yellow House Print                   1
 2 0902       Baseplate 16 x 24 with Set 080 Small White House Print              1
 3 0903       Baseplate 16 x 24 with Set 080 Red House Print                      1
# ... with 17,491 more rows
part_categories
# A tibble: 64 x 2
      id name                   
   <dbl> <chr>                  
 1     1 Baseplates             
 2     3 Bricks Sloped          
 3     4 Duplo, Quatro and Primo
 4     5 Bricks Special            
# ... with 54 more rows
parts %>% 
inner_join(part_categories, by = c("part_cat_id" = "id"))
# A tibble: 17,501 x 4
   part_num   name.x                                  part_cat_id name.y        
   <chr>      <chr>                                         <dbl> <chr>         
 1 0901       Baseplate 16 x 30 with Set 080 Yellow ~           1 Baseplates    
 2 0902       Baseplate 16 x 24 with Set 080 Small W~           1 Baseplates    
 3 0903       Baseplate 16 x 24 with Set 080 Red Hou~           1 Baseplates    
```
## left_join
In this example we merge star_destroyer to millennium_falcon by both  
color_id and part_num
```r
millennium_falcon
# A tibble: 263 x 4
   set_num part_num color_id quantity
   <chr>   <chr>       <dbl>    <dbl>
 1 7965-1  63868          71       62
 2 7965-1  3023            0       60
 3 7965-1  3021           72       46

star_destroyer
# A tibble: 293 x 4
   set_num part_num color_id quantity
   <chr>   <chr>       <dbl>    <dbl>
 1 75190-1 6141           72       66
 2 75190-1 3020            0       38
 3 75190-1 2780            0       36
 
millennium_falcon %>%
left_join(star_destroyer, by = c("color_id", "part_num"), suffix = c("_falcon", "_star_destroyer"))

# A tibble: 263 x 6
   set_num_falcon part_num color_id quantity_falcon set_num_star_destroyer
   <chr>          <chr>       <dbl>           <dbl> <chr>                 
 1 7965-1         63868          71              62 NA                    
 2 7965-1         3023            0              60 NA                    
 3 7965-1         3021           72              46 75190-1  
 
```

# group_by() and summarise()
In this example we will count how many thing in a group

```r
# Aggregate Millennium Falcon for the total quantity in each part
millennium_falcon

# A tibble: 263 x 4
   set_num part_num color_id quantity
   <chr>   <chr>       <dbl>    <dbl>
 1 7965-1  63868          71       62
 2 7965-1  3023            0       60
# ... with 253 more rows
millennium_falcon_colors <- millennium_falcon %>%
  group_by(color_id) %>%
  summarize(total_quantity = sum(quantity))
	
millennium_falcon_colors 

# A tibble: 21 x 2
   color_id total_quantity
      <dbl>          <dbl>
 1        0            201
 2        1             15
 3        4             17
 4       14              3
# ... with 11 more rows
```

# left_join and filter to find na value
Na is important for statistic because sometime our function will not work if we 
dont treat or ignore NA values

```r
inventory_version_1 <- inventories %>%
  filter(version == 1)
head(inventory_version_1,3)
# A tibble: 3 x 3
     id version set_num
  <dbl>   <dbl> <chr>  
1     1       1 7922-1 
2     3       1 3931-1 
3     4       1 6942-1 
head(sets,3)
# A tibble: 3 x 4
  set_num   name                                         year theme_id
  <chr>     <chr>                                       <dbl>    <dbl>
1 700.3-1   Medium Gift Set (ABB)                        1949      365
2 700.1.1-1 Single 2 x 4 Brick (ABB)                     1950      371
3 700.B.2-1 Single 1 x 2 x 3 Window without Glass (ABB)  1950      371
# Join versions to sets
sets %>%
  left_join(inventory_version_1, by = 'set_num') %>%
  # Filter for where version is na
  filter(is.na(version))
# A tibble: 1 x 6
  set_num name       year theme_id    id version
  <chr>   <chr>     <dbl>    <dbl> <dbl>   <dbl>
1 40198-1 Ludo game  2018      598    NA      NA
```

# right_join
This is similar to left join but it will merge into table on the right side

# count()
count(x, ..., wt = NULL, sort = FALSE, name = NULL)  
- wt stands for weight  

In 	#A, it will count how many occurrence for each carrier in a dataset  
		#B, it will count how many flights for each carrier  

```r
# using lego sets
# we can download and read_csv function
count(flights, carrier) 													#A
# A tibble: 16 x 2
   carrier     n
   <chr>   <int>
 1 9E      18460
 2 AA      32729
 3 AS        714
 4 B6      54635
 5 DL      48110
 6 EV      54173
 
count(flights, carrier, wt = flight, sort = TRUE) #B
# A tibble: 16 x 2
   carrier         n
   <chr>       <int>
 1 EV      250500399
 2 MQ      101761406
 3 DL       66141518
 4 9E       65847885
 5 UA       56289091
 6 B6       36669259
```

# joining their children
We can represent hirachy in table format by using number  
example:  

Car- Honda  
	|- Toyota  
	|- Ford - Bronco  
				 |- F150  
```r 
			id name           parent_id
   <dbl> <chr>              <dbl>
 1     1 Car           		    NA
 2     2 Honda								1
 3     3 Toyota								1
 4     4 Ford									1
 5     5 Bronco								4
 6     6 F150									4
``` 

## nycflights13

```r
> flights
# A tibble: 336,776 x 19
    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time arr_delay carrier flight tailnum origin dest  air_time distance  hour minute time_hour          
   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>     <dbl> <chr>    <int> <chr>   <chr>  <chr>    <dbl>    <dbl> <dbl>  <dbl> <dttm>             
 1  2013     1     1      517            515         2      830            819        11 UA        1545 N14228  EWR    IAH        227     1400     5     15 2013-01-01 05:00:00
 2  2013     1     1      533            529         4      850            830        20 UA        1714 N24211  LGA    IAH        227     1416     5     29 2013-01-01 05:00:00
 3  2013     1     1      542            540         2      923            850        33 AA        1141 N619AA  JFK    MIA        160     1089     5     40 2013-01-01 05:00:00
 4  2013     1     1      544            545        -1     1004           1022       -18 B6         725 N804JB  JFK    BQN        183     1576     5     45 2013-01-01 05:00:00
 
 
> nycflights13::weather
# A tibble: 26,115 x 15
   origin  year month   day  hour  temp  dewp humid wind_dir wind_speed wind_gust precip pressure visib time_hour          
   <chr>  <int> <int> <int> <int> <dbl> <dbl> <dbl>    <dbl>      <dbl>     <dbl>  <dbl>    <dbl> <dbl> <dttm>             
 1 EWR     2013     1     1     1  39.0  26.1  59.4      270      10.4         NA      0    1012     10 2013-01-01 01:00:00
 2 EWR     2013     1     1     2  39.0  27.0  61.6      250       8.06        NA      0    1012.    10 2013-01-01 02:00:00
 3 EWR     2013     1     1     3  39.0  28.0  64.4      240      11.5         NA      0    1012.    10 2013-01-01 03:00:00
```
	