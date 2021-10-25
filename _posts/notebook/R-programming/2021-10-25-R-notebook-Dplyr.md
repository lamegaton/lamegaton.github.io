---
title: R Notebook - dplyr 
categories: en tip
author: "Son Pham, Truc Pham"
meta: R notebook
description: "Essential R"
---
# Dplyr
Throught out the example I will use flights dataframe from library nycflights13

```{r}
library("nycflights13")
```

## select()
we use select to choose the columns
also, we can combine select with one_of()



```{r}
> names(flights)
 [1] "year"           "month"          "day"           
 [4] "dep_time"       "sched_dep_time" "dep_delay"     
 [7] "arr_time"       "sched_arr_time" "arr_delay"     
[10] "carrier"        "flight"         "tailnum"       
[13] "origin"         "dest"           "air_time"      
[16] "distance"       "hour"           "minute"        
[19] "time_hour"    

> names(select(flights,"year","air_time"))
[1] "year"     "air_time"

> names(select(flights,-("year":"air_time")))
[1] "distance"  "hour"      "minute"    "time_hour"

> names(select(flights, "year":"day"))
[1] "year"  "month" "day" 

> theCols <- c('flights', 'year', 'month','day','chucmap','conmap')
> select(flights, one_of(theCols))
# A tibble: 336,776 x 3
    year month   day
   <int> <int> <int>
 1  2013     1     1
 2  2013     1     1
 3  2013     1     1
 4  2013     1     1
```


## filter()
Like filter in excel, if you want to look at specific value in one or a few
of the columns, you can filter out by using

```{r}
df <- flights
filter(df,
       month == 9,
       day == 24
       )
```

what if I want to filter more months?

```{r}
filter(df,
       month %in% c(9,10,11),
       day == 24
       )
```
we can also use slice() to get the row that we want
syntax:	slice(dataframe, selected_rows)
example:slice(flights, c(1:3, 5000, 6000:6700)) 

## arrange()
arrange is similar to sort 

desc(): descending

```{r}
flights %>% arrange(desc(dep_time))
```



## inner_join
Joining three tables with the same variable

```{r}
sets
# A tibble: 4,977 x 4
   set_num   name                                                  year theme_id
   <chr>     <chr>                                                <dbl>    <dbl>
 1 700.3-1   Medium Gift Set (ABB)                                 1949      365
 2 700.1.1-1 Single 2 x 4 Brick (ABB)                              1950      371
 3 700.B.2-1 Single 1 x 2 x 3 Window without Glass (ABB)           1950      371
 
inventories
# A tibble: 15,174 x 3
      id version set_num 
   <dbl>   <dbl> <chr>   
 1     1       1 7922-1  

inventory_parts
# A tibble: 258,958 x 4
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
# A tibble: 258,958 x 9
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

```{r}
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


```{r}
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

```{r}
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

```{r}
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

```{r}
# using lego sets
# we can download and read_csv function

```

# joining their children
We can represent hirachy in table format by using number 
example:

Car- Honda
	|- Toyota
	|- Ford - Bronco
				 |- F150 
```{r} 
			id name           parent_id
   <dbl> <chr>              <dbl>
 1     1 Car           		    NA
 2     2 Honda				          1
 3     3 Toyota			            1
 4     4 Ford  					        1
 5     5 Bronco			            4
 6     6 F150		                4
``` 