# R commands help
- Getting Summary (min, max, mean, median mode, quartiles) of the dataframe `summary(PAAD.clinical)`   
* **dplyr** [mutate based on condition](http://stackoverflow.com/questions/22337394/combine-mutate-with-conditional-values): here 394 is median value
`PAAD.clinical %>% mutate(longivity = ifelse(vital_status == 1 & days_to_death <= 394, "short", "long")) %>% select(Sample,years_to_birth,vital_status,days_to_death,days_to_last_followup,times,longivity) -> PAAD.short.long` 
- `na.rm=T`  removes NAs from variable when any statistics is calculated
* Moving data between excel and R via the [clipboard](http://www.johndcook.com/blog/r_excel_clipboard/)  
`mydata <- read.delim(pipe(“pbpaste”))`
* How to select columns from the dataframe based on variables from another dataframe using  `one_of` from dplyr?
See answer in [biostars](https://www.biostars.org/p/229786/#229888) 
* Function to draw row names as dplyr verbs don’t use rownames
`draw_rownames <- function(.data) .data %>% do(mutate(.,rownames=rownames(.)))`

* **To make list of characters from the column of dataframe:** [link](http://stackoverflow.com/questions/3922461/extract-column-from-data-frame-as-a-vector)
> This will create a character vector:  
 `list.char <- as.vector(df$col)` 
> This will retain the factor nature of the vector   
`list.factor <- df$col`

* **To subset dataframe based on row.names:** [link](http://stackoverflow.com/questions/22670541/subsetting-a-matrix-by-row-names)
  `new.df <-df[list.char, ]`
Or
 `new.df <- subset(df, rownames(m) == list.char)`
* **To get the matching rows between two datasets**
> Actually  it can be done using dplyr  
`NMDP.alleles[which(NMDP.alleles$Allele %in% DQB1.nVp.m$Allele), ]`

