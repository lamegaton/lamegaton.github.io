# Plot
To plot in R, I use ggplot
```r
ggplot(table, aes(x = country_code, y = avg_meat, color = country_code)) + geom_point()#plot to see consumption of beef overtime  
```
in which table has to be in dataframe type. 
To plot in ggplot, you have to set your table to dataframe datatype
1. add data to vector
2. treat each vector as a column 
3. add to dataframe 
4. plot

# Import file
