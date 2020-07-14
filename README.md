# Data_Science_Wrangling
# HarvardX: PH125.6x | Data Science: Wrangling

## Abstract
This is the sixth course in the HarvardX Professional Certificate in Data Science, a series of courses that prepare you to do data analysis in R, from simple computations to machine learning.

The textbook for the Data Science course series is [freely available online](https://rafalab.github.io/dsbook/).

## Learning Objectives
- How to import data into R from different file formats
- How to scrape data from the web
- How to tidy data using the tidyverse to better facilitate analysis
- How to process strings with regular expressions (regex)
- How to wrangle data using dplyr
- How to work with dates and times as file formats
- How to mine text

## Course Overview

### Section 1: Data Import
You will learn how to import data from different sources.

### Section 2: Tidy Data
You will learn the first pieces of converting data into a tidy format.

### Section 3: String Processing
You will learn how to process strings using regular expressions (regex).

### Section 4: Dates, Times, and Text Mining
You will learn how to work with dates and times as file formats and how to mine text.

## Section 1 Overview

In the Data Import section, you will learn how import data into R.

After completing this section, you will be able to:
- Import data from spreadsheets.
- Identify and set your working directory and specify the path to a file.
- Use the readr and readxl packages to import spreadsheets.
- Use R-base functions to import spreadsheets.
- Download files from the internet using R.

The textbook for this section is available [here](https://rafalab.github.io/dsbook/importing-data.html)

## Assessment 1 - Importing Spreadsheets

1. Which of the following is NOT part of the data wranging process?
- [ ] A. Importing data into R
- [ ] B. Formatting dates/times
- [X] C. Checking correlations between your variables
- [ ] D. Tidying data

2. Which files could be opened in a basic text editor?

Select ALL that apply.

- [X] A. data.txt
- [X] B. data.csv
- [ ] C. data.xlsx
- [X] D. data.tsv

3. You want to analyze a file containing race finish times for a recent marathon. You open the file in a basic text editor and see lines that look like the following:
```
initials,state,age,time
vib,MA,61,6:01
adc,TX,45,5:45
kme,CT,50,4:19
```
What type of file is this?
- [ ] A. A comma-delimited file without a header
- [ ] B. A tab-delimited file with a header
- [ ] C. A white space-delimited file without a header
- [X] D. A comma-delimited file with a header

## Assessment 2 - Paths and the Working Directory

4. Assume the following is the full path to the directory that a student wants to use as their working directory in R: “/Users/student/Documents/projects/”

Which of the following lines of code CANNOT set the working directory to the desired “projects” directory?
- [ ] A. setwd("~/Documents/projects/")
- [ ] B. setwd("/Users/student/Documents/projects/")
- [X] C. setwd(/Users/student/Documents/projects/)
- [ ] D. dir <- "/Users/student/Documents/projects" setwd(dir)

5. We want to copy the “murders.csv” file from the dslabs package into an existing folder “data”, which is located in our HarvardX-Wrangling projects folder. We first enter the code below into our RStudio console.
```
> getwd()  
[1] "C:/Users/UNIVERSITY/Documents/Analyses/HarvardX-Wrangling"  
> filename <- "murders.csv"  
> path <- system.file("extdata", package = "dslabs")  
```
Which of the following commands would NOT successfully copy “murders.csv” into the folder “data”?
- [X] A. file.copy(file.path(path, "murders.csv"), getwd())
- [ ] B. setwd("data") file.copy(file.path(path, filename), getwd())
- [ ] C. file.copy(file.path(path, "murders.csv"), file.path(getwd(), "data"))
- [ ] D. file.location <- file.path(system.file("extdata", package = "dslabs"), "murders.csv")
file.destination <- file.path(getwd(),
"data") file.copy(file.location, file.destination)

## Assessment 3 - The readr and readxl Packages

6. You are not sure whether the murders.csv file has a header row. How could you check this?

Select ALL that apply.
- [X] A. Open the file in a basic text editor.
- [X] B. In the RStudio “Files” pane, click on your file, then select “View File”.
- [X] C. Use the command read_lines (remembering to specify the number of rows with the n_max argument).

7. What is one difference between read_excel and read_xlsx?

- [ ] A. Read_excel also reads meta-data from the excel file, such as sheet names, while read_xlsx only reads the first sheet in a file.
- [X] B. Read_excel reads both .xls and .xlsx files by detecting the file format from its extension, while read_xlsx only reads .xlsx files.
- [ ] C. Read_excel is part of the readr package, while read_xlsx is part of the readxl package and has more options.
- [ ] D. Read_xlsx has been replaced by read_excel in a recent readxl package update.

8. You have a file called “times.txt” that contains race finish times for a marathon. The first four lines of the file look like this:
```
initials,state,age,time
vib,MA,61,6:01
adc,TX,45,5:45
kme,CT,50,4:19
```
Which line of code will NOT produce a tibble with column names “initials”, “state”, “age”, and “time”?
- [ ] A. race_times <- read_csv("times.txt")
- [X] B. race_times <- read.csv("times.txt")
- [ ] C. race_times <- read_csv("times.txt", col_names = TRUE)
- [ ] D. race_times <- read_delim("times.txt", delim = “,”)

9. You also have access to marathon finish times in the form of an Excel document named “times.xlsx”. In the Excel document, different sheets contain race information for different years. The first sheet is named “2015”, the second is named “2016”, and the third is named “2017”.

Which line of code will NOT import the data contained in the “2016” tab of this Excel sheet?
- [ ] A. times_2016 <- read_excel("times.xlsx", sheet = 2)
- [X] B. times_2016 <- read_xlsx("times.xlsx", sheet = “2”)
- [ ] C. times_2016 <- read_excel("times.xlsx", sheet = "2016")
- [ ] D. times_2016 <- read_xlsx("times.xlsx", sheet = 2)

## Assessment 4 - Importing Data Using R-base Functions

10. You have a comma-separated values file that contains the initials, home states, ages, and race finish times for marathon runners. The runners’ initials contain three characters for the runners’ first, middle, and last names (for example, “KME”).

You read in the file using the following code.
```
race_times <- read.csv(“times.csv”)
```
What is the data type of the initials in the object race_times?
- [ ] A. integers
- [ ] B. characters
- [X] C. factors
- [ ] D. logical

Note: If you don’t supply the argument stringsAsFactors = F, the read.csv file will automatically convert characters to factors.

11. Which of the following is NOT a real difference between the readr import functions and the base R import functions?
- [ ] A. The import functions in the readr package all start as read_, while the import functions for base R all start with read.
- [ ] B. Base R import functions automatically convert character columns to factors.
- [X] C. The base R import functions can read .csv files, but cannot files with other delimiters, such as .tsv files, or fixed-width files.
- [ ] D. Base R functions import data as a data frame, while readr functions import data as a tibble.

12. You read in a file containing runner information and marathon finish times using the following code.
```
race_times <- read.csv(“times.csv”, stringsAsFactors = F)
```
What is the class of the object race_times?
- [X] A. data frame 
- [ ] B. tibble
- [ ] C. matrix
- [ ] D. vector

## Assessment 5 - Downloading Files from the Internet

13. Select the answer choice that summarizes all of the actions that the following lines of code can perform. Please note that the url below is an example and does not lead to data.
```
url <- "https://raw.githubusercontent.com/MyUserName/MyProject/master/MyData.csv "
dat <- read_csv(url)
download.file(url, "MyData.csv")
```
- [ ] A. Create a tibble in R called dat that contains the information contained in the csv file stored on Github and save that tibble to the working directory.
- [ ] B. Create a matrix in R called dat that contains the information contained in the csv file stored on Github. Download the csv file to the working directory and name the downloaded file “MyData.csv”.
- [ ] C. Create a tibble in R called dat that contains the information contained in the csv file stored on Github. Download the csv file to the working directory and randomly assign it a temporary name that is very likely to be unique.
- [X] D. Create a tibble in R called dat that contains the information contained in the csv file stored on Github. Download the csv file to the working directory and name the downloaded file “MyData.csv”.

14. Inspect the file at the following URL:

http://mlr.cs.umass.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data

Which readr function should be used to import this file?
- [ ] A. read_table()
- [X] B. read_csv()
- [ ] C. read_csv2()
- [ ] D. read_tsv()
- [ ] E. None of the above

15. Check the documentation for the readr function you chose in the previous question to learn about its arguments. Determine which arguments you need to the file from the previous question:

```
url <- "http://mlr.cs.umass.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data"
```

Does this file have a header row? Does the readr function you chose need any additional arguments to import the data correctly?

- [ ] A. Yes, there is a header. No arguments are needed.
- [ ] B. Yes, there is a header. The header=TRUE argument is necessary.
- [ ] C. Yes, there is a header. The col_names=TRUE argument is necessary.
- [ ] D. No, there is no header. No arguments are needed.
- [ ] E. No, there is no header. The header=FALSE argument is necessary.
- [X] F. No, there is no header. The col_names=FALSE argument is necessary.

16. Inspect the imported data from the previous question.

How many rows are in the dataset? 569

How many columns are in the dataset? 32 

## Section 2 Overview

In the Tidy Data section, you will learn how to convert data from a raw to a tidy format.

This section is divided into three parts: Reshaping Data, Combining Tables, and Web Scraping.

After completing the Tidy Data section, you will be able to:
- Reshape data using functions from the tidyr package, including gather, spread, separate, and unite.
- Combine information from different tables using join functions from the dplyr package.
- Combine information from different tables using binding functions from the dplyr package.
- Use set operators to combine data frames.
- Gather data from a website through web scraping and use of CSS selectors.

The textbook for this section is available [here](https://rafalab.github.io/dsbook/tidyverse.html#tidy-data) and [here](https://rafalab.github.io/dsbook/reshaping-data.html)

## Assessment 1 - Tidy Data

1. A collaborator sends you a file containing data for three years of average race finish times.
```
age_group,2015,2016,2017
20,3:46,3:22,3:50
30,3:50,3:43,4:43
40,4:39,3:49,4:51
50,4:48,4:59,5:01
```
Are these data considered “tidy” in R? Why or why not?
- [ ] A. Yes. These data are considered “tidy” because each row contains unique observations.
- [ ] B. Yes. These data are considered “tidy” because there are no missing data in the data frame.
- [X] C. No. These data are not considered “tidy” because the variable “year” is stored in the header.
- [ ] D. No. These data are not considered “tidy” because there are not an equal number of columns and rows.

2. Below are four versions of the same dataset. Which one is in a tidy format?

- [X] A.
```
state      abb   region  population total
Alabama    AL    South   4779736    135
Alaska     AK    West    710231     19
Arizona    AZ    West    6392017    232
Arkansas   AR    South   2915918    93
California CA    West    37253956   1257
Colorado   CO    West    5029196    65
```
- [ ] B.
```
state    abb  region        var        people
Alabama  AL   South         population 4779736
Alabama  AL   South         total      135
Alaska   AK   West          population 710231
Alaska   AK   West          total      19
Arizona  AZ   West          population 6392017
Arizona  AZ   West          total      232
```
- [ ] C.
```
state       abb       Northeast   South      North Central   West
Alabama     AL        NA          4779736    NA              NA
Alaska      AK        NA          NA         NA              710231
Arizona     AZ        NA          NA         NA              6392017
Arkansas    AR        NA          2915918    NA              NA
California  CA        NA          NA         NA              37253956
Colorado    CO        NA          NA         NA              5029196
```
- [ ] D.
```
state       abb  region    rate
Alabama     AL   South     2.82e-05
Alaska      AK   West      2.68e-05
Arizona     AZ   West      3.63e-05
Arkansas    AR   South     3.19e-05
California  CA   West      3.37e-05
Colorado    CO   West      1.29e-05
```
## Assessment 2 - Reshaping Data

3. Your file called “times.csv” has age groups and average race finish times for three years of marathons.
```
age_group,2015,2016,2017
20,3:46,3:22,3:50
30,3:50,3:43,4:43
40,4:39,3:49,4:51
50,4:48,4:59,5:01
```
You read in the data file using the following command.
```
d <- read_csv("times.csv")
```
Which commands will help you “tidy” the data?

- [X] A.
```
tidy_data <- d %>%
gather(year, time, `2015`:`2017`)
```
- [ ] B.
```
tidy_data <- d %>%
spread(year, time, `2015`:`2017`)
```
- [ ] C.
```
tidy_data <- d %>%
gather(age_group, year, time, `2015`:`2017`)
```
- [ ] D.
```
tidy_data <- d %>%
gather(time, `2015`:`2017`)
```
4. You have a dataset on U.S. contagious diseases, but it is in the following wide format:
```
> head(dat_wide)
state   year    population      Hepatitis A Mumps Polio Rubella
Alabama 1990    4040587         86          19    76    1
Alabama 1991    4066003         39          14    65    0
Alabama 1992    4097169         35          12    24    0
Alabama 1993    4133242         40          22    67    0
Alabama 1994    4173361         72          12    39    0
Alabama 1995    4216645         75          2     38    0
```
Which of the following would transform this into a tidy dataset, with each row representing an observation of the incidence of each specific disease (as shown below)?
```
> head(dat_tidy)
state   year    population   disease      count
Alabama 1990    4040587      Hepatitis A  86
Alabama 1991    4066003      Hepatitis A  39
Alabama 1992    4097169      Hepatitis A  35
Alabama 1993    4133242      Hepatitis A  40
Alabama 1994    4173361      Hepatitis A  72
Alabama 1995    4216645      Hepatitis A  75
```
- [ ] A.
```
dat_tidy <- dat_wide %>%
gather (key = count, value = disease, `Hepatitis A`, `Rubella`)
```
- [ ] B.
```
dat_tidy <- dat_wide %>%
gather(key = count, value = disease, -state, -year, -population)
```
- [ ] C.
```
dat_tidy <- dat_wide %>%
gather(key = disease, value = count, -state)
```
- [X] D.
```
dat_tidy <- dat_wide %>%
gather(key = disease, value = count, “Hepatitis A”: “Rubella”)
```
5. You have successfully formatted marathon finish times into a tidy object called tidy_data. The first few lines are shown below.
```
age_group,year,time
20,2015,03:46
30,2015,03:50
40,2015,04:39
50,2015,04:48
20,2016,03:22
```
Select the code that converts these data back to the wide format, where each year has a separate column.
- [ ] A. tidy_data %>% spread(time, year)
- [X] B. tidy_data %>% spread(year, time)
- [ ] C. tidy_data %>% spread(year, age_group)
- [ ] D. tidy_data %>% spread(time, year, `2015`:`2017`)
6.
```
> head(dat)
state    abb  region        var         people
Alabama  AL   South         population  4779736
Alabama  AL   South         total       135
Alaska   AK   West          population  710231
Alaska   AK   West          total       19
Arizona  AZ   West          population  6392017
Arizona  AZ   West          total       232
```
You would like to transform it into a dataset where population and total are each their own column (shown below). Which code would best accomplish this?
```
state       abb  region  population total
Alabama     AL   South   4779736    135
Alaska      AK   West    710231     19
Arizona     AZ   West    6392017    232
Arkansas    AR   South   2915918    93
California  CA   West    37253956   1257
Colorado    CO   West    5029196    65
```
- [X] A. dat_tidy <- dat %>% spread(key = var, value = people) 
- [ ] B. dat_tidy <- dat %>% spread(key = state:region, value = people) 
- [ ] C. dat_tidy <- dat %>% spread(key = people, value = var) 
- [ ] D. dat_tidy <- dat %>% spread(key = region, value = people)

## Assessment 3 - Separate and Unite

7. A collaborator sends you a file containing data for two years of average race finish times.
```
age_group,2015_time,2015_participants,2016_time,2016_participants
20,3:46,54,3:22,62
30,3:50,60,3:43,58
40,4:39,29,3:49,33
50,4:48,10,4:59,14
```
You read in the data file
```
d <- read_csv("times.csv")
```
Which of the answers below best tidys the data?
- [ ] A.
```
tidy_data <- d %>%
    gather(key = “key”, value = “value”, -age_group) %>%
    separate(col = key, into = c(“year”, “variable_name”), sep = “.”) %>% 
    spread(key = variable_name, value = value)
```
- [X] B.
```
tidy_data <- d %>%
        gather(key = “key”, value = “value”, -age_group) %>%
    separate(col = key, into = c(“year”, “variable_name”), sep = “_”) %>% 
    spread(key = variable_name, value = value)
```
- [ ] C.
```
 tidy_data <- d %>%
        gather(key = “key”, value = “value”) %>%
    separate(col = key, into = c(“year”, “variable_name”), sep = “_”) %>% 
    spread(key = variable_name, value = value)
```
- [ ] D.
```
tidy_data <- d %>%
        gather(key = “key”, value = “value”, -age_group) %>%
    separate(col = key, into = “year”, sep = “_”) %>% 
    spread(key = year, value = value)
```
8. You are in the process of tidying some data on heights, hand length, and wingspan for basketball players in the draft. Currently, you have the following:
```
> head(stats)
key                 value
allen_height        75
allen_hand_length   8.25
allen_wingspan      79.25
bamba_height        83.25
bamba_hand_length   9.75
bamba_wingspan      94
```
Select all of the correct commands below that would turn this data into a “tidy” format.

- [X] A.
```
tidy_data <- stats %>%
    separate(col = key, into = c("player", "variable_name"), sep = "_", extra = "merge") %>% 
    spread(key = variable_name, value = value) 
```
- [ ] B.
```
tidy_data <- stats %>%
    separate(col = key, into = c("player", "variable_name1", "variable_name2"), sep = "_", fill = "right") %>% 
    unite(col = variable_name, variable_name1, variable_name2, sep = "_") %>% 
    spread(key = variable_name, value = value)
```
- [ ] C.
```
tidy_data <- stats %>%
    separate(col = key, into = c("player", "variable_name"), sep = "_") %>% 
    spread(key = variable_name, value = value)
```
Use the following libraries for these questions:
```
library(tidyverse)
library(dslabs)
```
9. Examine the built-in dataset co2. This dataset comes with base R, not dslabs - just type co2 to access the dataset.

Is co2 tidy? Why or why not?

- [ ] A. co2 is tidy data: it has one year for each row.
- [ ] B. co2 is tidy data: each column is a different month.
- [ ] C. co2 is not tidy: there are multiple observations per column.
- [X] D. co2 is not tidy: to be tidy we would have to wrangle it to have three columns (year, month and value), and then each co2 observation would have a row.

10. Run the following command to define the co2_wide object:
```
co2_wide <- data.frame(matrix(co2, ncol = 12, byrow = TRUE)) %>% 
      setNames(1:12) %>%
    mutate(year = as.character(1959:1997))
```
Use the gather() function to make this dataset tidy. Call the column with the CO2 measurements co2 and call the month column month. Name the resulting object co2_tidy.

Which code would return the correct tidy format?
- [ ] A. co2_tidy <- gather(co2_wide,month,co2,year)
- [ ] B. co2_tidy <- gather(co2_wide,co2,month,-year)
- [ ] C. co2_tidy <- gather(co2_wide,co2,month,year)
- [X] D. co2_tidy <- gather(co2_wide,month,co2,-year)

11. Use co2_tidy to plot CO2 versus month with a different curve for each year:
```
co2_tidy %>% ggplot(aes(as.numeric(month), co2, color = year)) + geom_line()
```
What can be concluded from this plot?
- [ ] A. CO2 concentrations increased monotonically (never decreased) from 1959 to 1997.
- [X] B. CO2 concentrations are highest around May and the yearly average increased from 1959 to 1997.
- [ ] C. CO2 concentrations are highest around October and the yearly average increased from 1959 to 1997.
- [ ] D. Yearly average CO2 concentrations have remained constant over time.
- [ ] E. CO2 concentrations do not have a seasonal trend.

12. Load the admissions dataset from dslabs, which contains college admission information for men and women across six majors, and remove the applicants percentage column:
```
library(dslabs)
data(admissions)
dat <- admissions %>% select(-applicants)
```
Your goal is to get the data in the shape that has one row for each major, like this:
```
major  men   women
A      62    82		
B      63    68		
C      37    34		
D      33    35		
E      28    24		
F       6     7	
```
Which command could help you to wrangle the data into the desired format?
- [ ] A. dat_tidy <- spread(dat, major, admitted)
- [ ] B. dat_tidy <- spread(dat, gender, major)
- [X] C. dat_tidy <- spread(dat, gender, admitted)
- [ ] D. dat_tidy <- spread(dat, admitted, gender)

13. Now use the admissions dataset to create the object tmp, which has columns major, gender, key and value:
```
tmp <- gather(admissions, key, value, admitted:applicants)
tmp
```
Combine the key and gender and create a new column called column_name to get a variable with the following values: admitted_men, admitted_women, applicants_men and applicants_women. Save the new data as tmp2.

Which command could help you to wrangle the data into the desired format?

- [ ] A. tmp2 <- spread(tmp, column_name, key, gender)
- [ ] B. tmp2 <- gather(tmp, column_name, c(gender,key))
- [ ] C. tmp2 <- unite(tmp, column_name, c(gender, key)) 
- [ ] D. tmp2 <- spread(tmp, column_name, c(key,gender))
- [X] E. tmp2 <- unite(tmp, column_name, c(key, gender))

14. Which function can reshape tmp2 to a table with six rows and five columns named major, admitted_men, admitted_women, applicants_men and applicants_women?

- [ ] A. gather()
- [X] B. spread()
- [ ] C. separate()
- [ ] D. unite()

## Assessment 4 - Combining Table

1. You have created a tab1 and tab2 of state population and election data, similar to our module videos:
```
> tab1
state                    population
Alabama                  4779736
Alaska                   710231
Arizona                  6392017
Delaware                 897934
District of Columbia     601723

> tab2
state        electoral_votes
Alabama      9
Alaska       3
Arizona      11
California   55
Colorado     9
Connecticut  7

> dim(tab1)
[1] 5 2

> dim(tab2)
[1] 6 2
```
What are the dimensions of the table dat, created by the following command?
```
dat <- left_join(tab1, tab2, by = “state”)
```
- [ ] A. 3 rows by 3 columns
- [ ] B. 5 rows by 2 columns
- [X] C. 5 rows by 3 columns
- [ ] D. 6 rows by 3 columns

2. We are still using the tab1 and tab2 tables shown in question 1. What join command would create a new table “dat” with three rows and two columns?

- [ ] A. dat <- right_join(tab1, tab2, by = “state”)
- [ ] B. dat <- full_join(tab1, tab2, by = “state”)
- [ ] C. dat <- inner_join(tab1, tab2, by = “state”)
- [X] D. dat <- semi_join(tab1, tab2, by = “state”)

## Assessment 5 - Binding

3. Which of the following are real differences between the join and bind functions?

- [X] A. Binding functions combine by position, while join functions match by variables.
- [X] B. Joining functions can join datasets of different dimensions, but the bind functions must match on the appropriate dimension (either same row or column numbers).
- [X] C. Bind functions can combine both vectors and dataframes, while join functions work for only for dataframes.
- [ ] D. The join functions are a part of the dplyr package and have been optimized for speed, while the bind functions are inefficient base functions.

## Assessment 6 - Set Operators

4. We have two simple tables, shown below:
```
> df1
 x     y    
 a     a    
 b     a    

> df2
 x     y    
 a     a    
 a     b  
```
Which command would result in the following table?
```
> final
 x     y    
 b     a   
```
- [ ] A. final <- union(df1, df2)
- [X] B. final <- setdiff(df1, df2)
- [ ] C. final <- setdiff(df2, df1)
- [ ] D. final <- intersect(df1, df2)

Install and load the Lahman library. This library contains a variety of datasets related to US professional baseball. We will use this library for the next few questions and will discuss it more extensively in the Regression course. For now, focus on wrangling the data rather than understanding the statistics.

The Batting data frame contains the offensive statistics for all baseball players over several seasons.  Filter this data frame to define top as the top 10 home run (HR) hitters in 2016:
```
library(Lahman)
top <- Batting %>% 
  filter(yearID == 2016) %>%
  arrange(desc(HR)) %>%    # arrange by descending HR count
  slice(1:10)    # take entries 1-10
top %>% as_tibble()
```
Also Inspect the Master data frame, which has demographic information for all players:
```
Master %>% as_tibble()
```
5. Use the correct join or bind function to create a combined table of the names and statistics of the top 10 home run (HR) hitters for 2016. This table should have the player ID, first name, last name, and number of HR for the top 10 players. Name this data frame top_names.

Identify the join or bind that fills the blank in this code to create the correct table:
```
top_names <- top %>% ___________________ %>%
    select(playerID, nameFirst, nameLast, HR)
```
Which bind or join function fills the blank to generate the correct table?
- [ ] A. rbind(Master)
- [ ] B. cbind(Master)
- [X] C. left_join(Master)
- [ ] D. right_join(Master)
- [ ] E. full_join(Master)
- [ ] F. anti_join(Master)

6. Inspect the Salaries data frame. Filter this data frame to the 2016 salaries, then use the correct bind join function to add a salary column to the top_names data frame from the previous question. Name the new data frame top_salary. Use this code framework:
```
top_salary <- Salaries %>% filter(yearID == 2016) %>%
  ______________ %>%
  select(nameFirst, nameLast, teamID, HR, salary)
```
Which bind or join function fills the blank to generate the correct table?
- [ ] A. rbind(top_names)
- [ ] B. cbind(top_names)
- [ ] C. left_join(top_names)
- [X] D. right_join(top_names)
- [ ] E. full_join(top_names)
- [ ] F. anti_join(top_names)

7. Inspect the AwardsPlayers table. Filter awards to include only the year 2016.

How many players from the top 10 home run hitters won at least one award in 2016? Use a set operator. 
```
top_awards <- AwardsPlayers %>% filter(yearID == 2016)
length(intersect(top_awards$playerID, top_names$playerID))

3 
```
How many players won an award in 2016 but were not one of the top 10 home run hitters in 2016? Use a set operator.
```
length(setdiff(top_awards$playerID, top_names$playerID))

44
```
## Assessment 7 - Web Scraping

Load the following web page, which contains information about Major League Baseball payrolls, into R: 

https://web.archive.org/web/20181024132313/http://www.stevetheump.com/Payrolls.htm
```
library(rvest)
url <- "https://web.archive.org/web/20181024132313/http://www.stevetheump.com/Payrolls.htm"
h <- read_html(url)
```
We learned that tables in html are associated with the table node.  Use the html_nodes() function and the table node type to extract the first table. Store it in an object nodes:
```
nodes <- html_nodes(h, "table")
```
The html_nodes() function returns a list of objects of class xml_node. We can see the content of each one using, for example, the html_text() function. You can see the content for an arbitrarily picked component like this:
```
html_text(nodes[[8]])
```
If the content of this object is an html table, we can use the html_table() function to convert it to a data frame:
```
html_table(nodes[[8]])
```
You will analyze the tables from this HTML page over questions 1-3.

1. Many tables on this page are team payroll tables, with columns for rank, team, and one or more money values.

Convert the first four tables in nodes to data frames and inspect them.

Which of the first four nodes are tables of team payroll? Check all correct answers. Look at table content, not column names.

- [ ] A. None of the above
- [ ] B. Table 1
- [X] C. Table 2
- [X] D. Table 3
- [X] E. Table 4

2. For the last 3 components of nodes, which of the following are true? Check all correct answers.

- [X] A. All three entries are tables.
- [ ] B. All three entries are tables of payroll per team.
- [X] C. The last entry shows the average across all teams through time, not payroll per team.
- [ ] D. None of the three entries are tables of payroll per team.

3. Create a table called tab_1 using entry 10 of nodes. Create a table called tab_2 using entry 19 of nodes.

Note that the column names should be c("Team", "Payroll", "Average"). You can see that these column names are actually in the first data row of each table, and that tab_1 has an extra first column No. that should be removed so that the column names for both tables match.

Remove the extra column in tab_1, remove the first row of each dataset, and change the column names for each table to c("Team", "Payroll", "Average"). Use a full_join() by the Team to combine these two tables.

Note that some students, presumably because of system differences, have noticed that entry 18 instead of entry 19 of nodes gives them the tab_2 correctly; be sure to check entry 18 if entry 19 is giving you problems.

How many rows are in the joined data table? ```58```

4. The Wikipedia page on opinion polling for the Brexit referendum, in which the United Kingdom voted to leave the European Union in June 2016, contains several tables. One table contains the results of all polls regarding the referendum over 2016.

Use the rvest library to read the HTML from this Wikipedia page (make sure to copy both lines of the URL):
```
library(rvest)
library(tidyverse)
url <- "https://en.wikipedia.org/w/index.php?title=Opinion_polling_for_the_United_Kingdom_European_Union_membership_referendum&oldid=896735054"
```
Assign tab to be the html nodes of the "table" class.

How many tables are in this Wikipedia page? ```40```

5. Inspect the first several html tables using html_table() with the argument fill=TRUE (you can read about this argument in the documentation). Find the first table that has 9 columns with the first column named "Date(s) conducted".

What is the first table number to have 9 columns where the first column is named "Date(s) conducted"? ```5```

## Section 3 Overview

In the String Processing section, we use case studies that help demonstrate how string processing is a powerful tool useful for overcoming many data wrangling challenges. You will see how the original raw data was processed to create the data frames we have used in courses throughout this series.

This section is divided into three parts.

After completing the String Processing section, you will be able to:
- Remove unwanted characters from text.
- Extract numeric values from text.
- Find and replace characters.
- Extract specific parts of strings.
- Convert free form text into more uniform formats.
- Split strings into multiple values.
- Use regular expressions (regex) to process strings.

The textbook for this section is available [here](https://rafalab.github.io/dsbook/string-processing.html)

## Assessment 1 - String Parsing

1. Which of the following is NOT an application of string parsing?

- [ ] A. Removing unwanted characters from text.
- [ ] B. Extracting numeric values from text.
- [X] C. Formatting numbers and characters so they can easily be displayed in deliverables like papers and presentations.
- [ ] D. Splitting strings into multiple values.

## Assessment 2 - Defining Strings: Single and Double Quotes and How to Escape

1. Which of the following commands would not give you an error in R?

- [X] A. cat(" LeBron James is 6’8\" ")
- [ ] B. cat(' LeBron James is 6'8" ')
- [ ] C. cat(` LeBron James is 6'8" `)
- [ ] D. cat(" LeBron James is 6\’8" ")

## Assessment 3 - stringr Package

1. Which of the following are advantages of the stringr package over string processing functions in base R? Select all that apply.

- [ ] A. Base R functions are rarely used for string processing by data scientists so it’s not worth learning them.
- [X] B. Functions in stringr all start with “str_”, which makes them easy to look up using autocomplete.
- [X] C. Stringr functions work better with pipes.
- [X] D. The order of arguments is more consistent in stringr functions than in base R.

## Assessment 4 - Case Study 1: US Murders Data

1. You have a dataframe of monthly sales and profits in R
```
> head(dat)
# A tibble: 5 x 3
Month       Sales       Profit 
<chr>       <chr>       <chr>  
January     $128,568    $16,234
February    $109,523    $12,876
March       $115,468    $17,920
April       $122,274    $15,825
May         $117,921    $15,437
```
Which of the following commands could convert the sales and profits columns to numeric? Select all that apply.

- [X] A. dat %>% mutate_at(2:3, parse_number)
- [ ] B. dat %>% mutate_at(2:3, as.numeric)
- [ ] C. dat %>% mutate_all(parse_number)
- [X] D. dat %>% mutate_at(2:3, funs(str_replace_all(., c("\\$|,"), ""))) %>%mutate_at(2:3, as.numeric)

## Assessment 5 - Case Study 2: Reported Heights

1. In the video, we use the function not_inches to identify heights that were incorrectly entered
```
not_inches <- function(x, smallest = 50, tallest = 84) {
  inches <- suppressWarnings(as.numeric(x))
  ind <- is.na(inches) | inches < smallest | inches > tallest 
  ind
}
```
In this function, what TWO types of values are identified as not being correctly formatted in inches?

- [ ] A. Values that specifically contain apostrophes (‘), periods (.) or quotations (“).
- [X] B. Values that result in NA’s when converted to numeric
- [X] C. Values less than 50 inches or greater than 84 inches
- [ ] D. Values that are stored as a character class, because most are already classed as numeric.

2. Which of the following arguments, when passed to the function not_inches, would return the vector c(FALSE)?

- [ ] A. c(175)
- [ ] B. c(“5’8\””)
- [X] C. c(70)
- [ ] D. c(85) (the height of Shaquille O'Neal in inches)

3. Our function `not_inches` returns the object `ind`. Which answer correctly describes ind?

- [X] A. ind is a logical vector of TRUE and FALSE, equal in length to the vector x (in the arguments list). TRUE indicates that a height entry is incorrectly formatted.
- [ ] B. indis a logical vector of TRUE and FALSE, equal in length to the vector x(in the arguments list). TRUE indicates that a height entry is correctly formatted.
- [ ] C. ind is a data frame like our reported_heights table but with an extra column of TRUE or FALSE. TRUE indicates that a height entry is incorrectly formatted.
- [ ] D. ind is a numeric vector equal to reported_heights$heights but with incorrectly formatted heights replaced with NAs.

## Assessment 6 - Regex

1. Given the following code
```
> s
[1] "70"       "5 ft"     "4'11"     ""         "."        "Six feet"
```
What `pattern` vector yields the following result?
```
str_view_all(s, pattern)
70
5 ft
4’11
.
Six feet
```
- [X] A. ```pattern <- "\\d|ft"```
- [ ] B. ```pattern <- "\d|ft"```
- [ ] C. ```pattern <- "\\d\\d|ft"```
- [ ] D. ```pattern <- "\\d|feet"```

## Assessment 7 - Character Classes, Anchors, and Qualifiers

1. You enter the following set of commands into your R console. What is your printed result?
```
> animals <- c("cat", "puppy", "Moose", "MONKEY")
> pattern <- "[a-z]"
> str_detect(animals, pattern)
```
- [ ] A. TRUE
- [ ] B. TRUE TRUE TRUE TRUE
- [X] C. TRUE TRUE TRUE FALSE
- [ ] D. TRUE TRUE FALSE FALSE

2. You enter the following set of commands into your R console. What is your printed result?
```
> animals <- c("cat", "puppy", "Moose", "MONKEY")
> pattern <- "[A-Z]$"
> str_detect(animals, pattern)
```
- [ ] A. FALSE FALSE FALSE FALSE
- [ ] B. FALSE FALSE TRUE TRUE
- [X] C. FALSE FALSE FALSE TRUE
- [ ] D. TRUE TRUE TRUE FALSE

3. You enter the following set of commands into your R console. What is your printed result?
```
> animals <- c("cat", "puppy", "Moose", "MONKEY")
> pattern <- "[a-z]{4,5}"
> str_detect(animals, pattern)
```
- [X] A. FALSE TRUE TRUE FALSE
- [ ] B. TRUE TRUE FALSE FALSE
- [ ] C. FALSE FALSE FALSE TRUE
- [ ] D. TRUE TRUE TRUE FALSE

## Assessment 8 - Search and Replace with Regex

1. Given the following code
```
animals <- c(“moose”, “monkey”, “meerkat”, “mountain lion”) Which TWO “pattern” vectors would yield the following result?
str_detect(animals, pattern) 
[1] TRUE TRUE TRUE TRUE
```
- [X] A. pattern <- “mo*”
- [X] B. pattern <- “mo?”
- [ ] C. pattern <- “mo+”
- [ ] D. pattern <- “moo*”

2. You are working on some data from different universities. You have the following vector
```
> schools
[1] "U. Kentucky"                 "Univ New Hampshire"          "Univ. of Massachusetts"      "University Georgia"         
[5] "U California"                "California State University"
```
You want to clean this data to match the full names of each university
```
> final
[1] "University of Kentucky"      "University of New Hampshire" "University of Massachusetts" "University of Georgia"         
[5] "University of California"    "California State University"
```
What of the following commands could accomplish this?

- [ ] A.
```
schools %>% 
  str_replace("Univ\\.?|U\\.?", "University ") %>% 
  str_replace("^University of |^University ", "University of ")
```
- [X] B.
```
schools %>% 
  str_replace("^Univ\\.?\\s|^U\\.?\\s", "University ") %>% 
  str_replace("^University of |^University ", "University of ")
```
- [ ] C.
```
schools %>% 
  str_replace("^Univ\\.\\s|^U\\.\\s", "University") %>% 
  str_replace("^University of |^University ", "University of ")
```
- [ ] D.
```
schools %>% 
  str_replace("^Univ\\.?\\s|^U\\.?\\s", "University") %>% 
  str_replace("University ", "University of ")
```
## Assessment 9 - Groups with Regex

1. Rather than using the pattern_with_groups vector from the video, you accidentally write in the following code
```
problems <- c("5.3", "5,5", "6 1", "5 .11", "5, 12")
pattern_with_groups <- "^([4-7])[,\\.](\\d*)$"
str_replace(problems, pattern_with_groups, "\\1'\\2")
```
What is your result?

- [X] A. [1] "5'3" "5'5" "6 1" "5 .11" "5, 12"
- [ ] B. [1] “5.3” “5,5” “6 1” “5 .11” “5, 12”
- [ ] C. [1] “5’3” “5’5” “6’1” “5 .11” “5, 12”
- [ ] D. [1] “5’3” “5’5” “6’1” “5’11” “5’12”

2. You notice your mistake and correct your pattern regex to the following
```
problems <- c("5.3", "5,5", "6 1", "5 .11", "5, 12")
pattern_with_groups <- "^([4-7])[,\\.\\s](\\d*)$"
str_replace(problems, pattern_with_groups, "\\1'\\2")
```
What is your result?

- [ ] A. [1] “5’3” “5’5” “6 1” “5 .11” “5, 12”
- [ ] B. [1] “5.3” “5,5” “6 1” “5 .11” “5, 12”
- [X] C. [1] "5'3" "5'5" "6'1" "5 .11" "5, 12"
- [ ] D. [1] “5’3” “5’5” “6’1” “5’11” “5’12”

## Assessment 10 - Testing and Improving

1. In our example, we use the following code to detect height entries that do not match our pattern of x’y”.
```
converted <- problems %>% 
  str_replace("feet|foot|ft", "'") %>% 
  str_replace("inches|in|''|\"", "") %>% 
  str_replace("^([4-7])\\s*[,\\.\\s+]\\s*(\\d*)$", "\\1'\\2")

pattern <- "^[4-7]\\s*'\\s*\\d{1,2}$"
index <- str_detect(converted, pattern)
converted[!index]
```
Which answer best describes the differences between the regex string we use as an argument in `str_replace("^([4-7])\\s*[,\\.\\s+]\\s*(\\d*)$", "\\1'\\2")`

And the regex string in `pattern <- "^[4-7]\\s*'\\s*\\d{1,2}$"`?

- [ ] A. The regex used in str_replace looks for either a comma, period or space between the feet and inches digits, while the pattern regex just looks for an apostrophe; the regex in str_replace allows for one or more digits to be entered as inches, while the pattern regex only allows for one or two digits.
- [ ] B. The regex used in str_replace allows for additional spaces between the feet and inches digits, but the pattern regex does not.
- [ ] C. The regex used in str_replace looks for either a comma, period or space between the feet and inches digits, while the pattern regex just looks for an apostrophe; the regex in str_replace allows none or more digits to be entered as inches, while the pattern regex only allows for the number 1 or 2 to be used.
- [X] D. The regex used in str_replace looks for either a comma, period or space between the feet and inches digits, while the pattern regex just looks for an apostrophe; the regex in str_replace allows for none or more digits to be entered as inches, while the pattern regex only allows for one or two digits.

2. You notice a few entries that are not being properly converted using your str_replace and str_detect code
```
yes <- c("5 feet 7inches", “5 7”)
no <- c("5ft 9 inches", "5 ft 9 inches")
s <- c(yes, no)

converted <- s %>% 
  str_replace("feet|foot|ft", "'") %>% 
  str_replace("inches|in|''|\"", "") %>% 
  str_replace("^([4-7])\\s*[,\\.\\s+]\\s*(\\d*)$", "\\1'\\2")

pattern <- "^[4-7]\\s*'\\s*\\d{1,2}$"
str_detect(converted, pattern)
[1]  TRUE FALSE FALSE
```
It seems like the problem may be due to spaces around the words feet|foot|ft and inches|in. What is another way you could fix this problem?

- [X] A.
```
converted <- s %>% 
  str_replace("\\s*(feet|foot|ft)\\s*", "'") %>% 
  str_replace("\\s*(inches|in|''|\")\\s*", "") %>% 
  str_replace("^([4-7])\\s*[,\\.\\s+]\\s*(\\d*)$", "\\1'\\2")
```
- [ ] B. 
```
converted <- s %>% 
  str_replace("\\s+feet|foot|ft\\s+”, "'") %>% 
  str_replace("\\s+inches|in|''|\"\\s+", "") %>% 
  str_replace("^([4-7])\\s*[,\\.\\s+]\\s*(\\d*)$", "\\1'\\2")
```
- [ ] C.
```
converted <- s %>% 
  str_replace("\\s*|feet|foot|ft", "'") %>% 
  str_replace("\\s*|inches|in|''|\"", "") %>% 
  str_replace("^([4-7])\\s*[,\\.\\s+]\\s*(\\d*)$", "\\1'\\2") 
```
- [ ] D.
```
converted <- s %>% 
  str_replace_all(“\\s”, “”) %>% 
  str_replace("\\s|feet|foot|ft", "'") %>% 
  str_replace("\\s|inches|in|''|\"", "") %>% 
  str_replace("^([4-7])\\s*[,\\.\\s+]\\s*(\\d*)$", "\\1'\\2")
```
## Assessment 11 - Using Groups and Quantifiers

1.
```
s <- c("5'10", "6'1\"", "5'8inches", "5'7.5")
tab <- data.frame(x = s)
```
If you use the extract code from our video, the decimal point is dropped. What modification of the code would allow you to put the decimals in a third column called “decimal”?
- [ ] A.
```
extract(data = tab, col = x, into = c(“feet”, “inches”, “decimal”), regex = "(\\d)'(\\d{1,2})(\\.)?"
```
- [ ] B.
```
extract(data = tab, col = x, into = c("feet", "inches", "decimal"), regex = "(\\d)'(\\d{1,2})(\\.\\d+)" 
```
- [ ] C.
```
extract(data = tab, col = x, into = c("feet", "inches", "decimal"), regex = "(\\d)'(\\d{1,2})\\.\\d+?"
```
- [X] D.
```
extract(data = tab, col = x, into = c("feet", "inches", "decimal"), regex = "(\\d)'(\\d{1,2})(\\.\\d+)?")  
```

## Assessment 12 - String Splitting

1. You have the following table
```
>schedule
day         staff
Monday      Mandy, Chris and Laura
Tuesday     Steve, Ruth and Frank
```
You want to turn this into a more useful data frame.

Which two commands would properly split the text in the “staff” column into each individual name? Select ALL that apply.

- [ ] A. str_split(schedule$staff, ",|and")
- [X] B. str_split(schedule$staff, ", | and ")
- [X] C. str_split(schedule$staff, ",\\s|\\sand\\s")
- [ ] D. str_split(schedule$staff, "\\s?(,|and)\\s?")

2. You have the following table
```
> schedule
day         staff
Monday      Mandy, Chris and Laura
Tuesday     Steve, Ruth and Frank
```
What code would successfully turn your “Schedule” table into the following tidy table
```
< tidy
day      staff
<chr>    <chr>
Monday   Mandy
Monday   Chris
Monday   Laura
Tuesday  Steve
Tuesday  Ruth 
Tuesday  Frank
```
- [X] A.
```
tidy <- schedule %>% 
  mutate(staff = str_split(staff, ", | and ")) %>% 
  unnest()
```
- [ ] B.
```
tidy <- separate(schedule, staff, into = c("s1","s2","s3"), sep = “,”) %>% 
  gather(key = s, value = staff, s1:s3)
```
- [ ] C.
```
tidy <- schedule %>% 
  mutate(staff = str_split(staff, ", | and ", simplify = TRUE)) %>%   unnest()
```

## Assessment 13 - Recoding

1. Using the gapminder data, you want to recode countries longer than 12 letters in the region “Middle Africa” to their abbreviations in a new column, “country_short”. Which code would accomplish this?
- [ ] A.
```
dat <- gapminder %>% filter(region == "Middle Africa") %>% 
  mutate(recode(country, 
                          "Central African Republic" = "CAR", 
                          "Congo, Dem. Rep." = "DRC",
                          "Equatorial Guinea" = "Eq. Guinea"))
```
- [ ] B.
```
dat <- gapminder %>% filter(region == "Middle Africa") %>% 
  mutate(country_short = recode(country, 
                          c("Central African Republic", "Congo, Dem. Rep.", "Equatorial Guinea"),
                          c("CAR", "DRC", "Eq. Guinea")))
```
- [ ] C.
```
dat <- gapminder %>% filter(region == "Middle Africa") %>% 
  mutate(country = recode(country, 
                          "Central African Republic" = "CAR", 
                          "Congo, Dem. Rep." = "DRC",
                          "Equatorial Guinea" = "Eq. Guinea"))
```
- [X] D.
```
dat <- gapminder %>% filter(region == "Middle Africa") %>% 
  mutate(country_short = recode(country, 
                          "Central African Republic" = "CAR", 
                          "Congo, Dem. Rep." = "DRC",
                          "Equatorial Guinea" = "Eq. Guinea"))
```

2. Import raw Brexit referendum polling data from Wikipedia:

```
library(rvest)
library(tidyverse)
library(stringr)
url <- "https://en.wikipedia.org/w/index.php?title=Opinion_polling_for_the_United_Kingdom_European_Union_membership_referendum&oldid=896735054"
tab <- read_html(url) %>% html_nodes("table")
polls <- tab[[5]] %>% html_table(fill = TRUE)
```

You will use a variety of string processing techniques learned in this section to reformat these data.

Some rows in this table do not contain polls. You can identify these by the lack of the percent sign (%) in the Remain column.

Update polls by changing the column names to c("dates", "remain", "leave", "undecided", "lead", "samplesize", "pollster", "poll_type", "notes") and only keeping rows that have a percent sign (%) in the remain column.

How many rows remain in the polls data frame? ```129```

3. The ```remain``` and ```leave``` columns are both given in the format "48.1%": percentages out of 100% with a percent symbol.

Which of these commands converts the remain vector to a proportion between 0 and 1?

Check all correct answers.

- [ ] A. as.numeric(str_remove(polls$remain, "%"))
- [ ] B. as.numeric(polls$remain)/100
- [ ] C. parse_number(polls$remain)
- [ ] D. str_remove(polls$remain, "%")/100
- [X] E. as.numeric(str_replace(polls$remain, "%", ""))/100
- [X] F. parse_number(polls$remain)/100

4. The undecided column has some "N/A" values. These "N/A"s are only present when the remain and leave columns total 100%, so they should actually be zeros.

Use a function from stringr to convert "N/A" in the undecided column to 0. The format of your command should be function_name(polls$undecided, "arg1", "arg2").

What function replaces function_name? ```str_replace```

What argument replaces arg1? ```N/A```

What argument replaces arg2? ```0```

5. The dates column contains the range of dates over which the poll was conducted. The format is "8-10 Jan" where the poll had a start date of 2016-01-08 and end date of 2016-01-10. Some polls go across month boundaries (16 May-12 June).

The end date of the poll will always be one or two digits, followed by a space, followed by the month as one or more letters (either capital or lowercase). In these data, all month abbreviations or names have 3, 4 or 5 letters.

Write a regular expression to extract the end day and month from dates. Insert it into the skeleton code below:

```
temp <- str_extract_all(polls$dates, _____)
end_date <- sapply(temp, function(x) x[length(x)]) # take last element (handles polls that cross month boundaries)
```

Which of the following regular expressions correctly extracts the end day and month when inserted into the blank in the code above?
Check all correct answers.

- [ ] A. ```"\\d?\\s[a-zA-Z]?"```
- [X] B. ```"\\d+\\s[a-zA-Z]+"```
- [ ] C. ```"\\d+\\s[A-Z]+"```
- [X] D. ```"[0-9]+\\s[a-zA-Z]+"```
- [X] E. ```"\\d{1,2}\\s[a-zA-Z]+"```
- [ ] F. ```"\\d{1,2}[a-zA-Z]+"```
- [X] G. ```"\\d+\\s[a-zA-Z]{3,5}"```

## Section 4 Overview

In the Dates, Times, and Text Mining section, you will learn how to deal with dates and times in R and also how to generate numerical summaries from text data.

After completing this section, you will be able to:
- Handle dates and times in R.
- Use the lubridate package to parse dates and times in different formats.
- Generate numerical summaries from text data and apply data visualization and analysis techniques to those data.

The textbook for this section is available [here](https://rafalab.github.io/dsbook/parsing-dates-and-times.html)

## Assessment 1- Dates and Times

1. Which of the following is the standard ISO 8601 format for dates?

- [ ] A. MM-DD-YY
- [X] B. YYYY-MM-DD
- [ ] C. YYYYMMDD
- [ ] D. YY-MM-DD

2. Which of the following commands could convert this string into the correct date format?
```
dates <- c("09-01-02", "01-12-07", "02-03-04")
```
- [ ] A. ymd(dates)
- [ ] B. mdy(dates)
- [ ] C. dmy(dates)
- [X] D. It is impossible to know which format is correct without additional information.

3. Load the brexit_polls data frame from dslabs:

```
data(brexit_polls)
```

How many polls had a start date (startdate) in April (month number 4)? ```25```
 
Use the round_date() function on the enddate column with the argument unit="week". How many polls ended the week of 2016-06-12? ```13```
```
sum(round_date(brexit_polls$enddate, unit = "week") == "2016-06-12")
```

# Final: Comprehensive Assessment

## Comprehensive Assessment: Puerto Rico Hurricane Mortality

### Project Introduction

On September 20, 2017, Hurricane Maria made landfall on Puerto Rico. It was the worst natural disaster on record in Puerto Rico and the deadliest Atlantic hurricane since 2004. However, Puerto Rico's official death statistics only tallied 64 deaths caused directly by the hurricane (due to structural collapse, debris, floods and drownings), an undercount that slowed disaster recovery funding. The majority of the deaths resulted from infrastructure damage that made it difficult to access resources like clean food, water, power, healthcare and communications in the months after the disaster, and although these deaths were due to effects of the hurricane, they were not initially counted.

In order to correct the misconception that few lives were lost in Hurricane Maria, statisticians analyzed how death rates in Puerto Rico changed after the hurricane and estimated the excess number of deaths likely caused by the storm. This analysis suggested that the actual number of deaths in Puerto Rico was 2,975 (95% CI: 2,658-3,290) over the 4 months following the hurricane, much higher than the original count.

We will use your new data wrangling skills to extract actual daily mortality data from Puerto Rico and investigate whether the Hurricane Maria had an immediate effect on daily mortality compared to unaffected days in September 2015-2017.

```{r}
library(tidyverse)
library(pdftools)
options(digits = 3)    # report 3 significant digits
```

### Puerto Rico Hurricane Mortality: Part 1

#### Question 1
In the extdata directory of the dslabs package, you will find a PDF file containing daily mortality data for Puerto Rico from Jan 1, 2015 to May 31, 2018. You can find the file like this:
```{r}
fn <- system.file("extdata", "RD-Mortality-Report_2015-18-180531.pdf", package="dslabs")
```

Find and open the file or open it directly from RStudio. On a Mac, you can type:
```{r}
system2("open", args = fn)
```
#### Question 2
We are going to create a tidy dataset with each row representing one observation. The variables in this dataset will be year, month, day and deaths.  
Use the pdftools package to read in fn using the pdf_text function. Store the results in an object called txt.  
Describe what you see in txt.  

```{r}
txt <- pdf_text(fn)
class(txt)
str(txt)
dim(txt)
```
#### Question 3
Extract the ninth page of the PDF file from the object txt, then use the str_split function from the stringr package so that you have each line in a different entry. The new line character is \n. Call this string vector x.  
Look at x. What best describes what you see?

```{r}
page_9 <- txt[9]
page_9
x <- str_split(page_9, "\n")
class(x)
length(x)
```
#### Question 4
Define s to be the first entry of the x object.  
What kind of object is s?
```{r}
s <- x[[1]]
class(s)
length(s)
s
```
#### Question 5
When inspecting the string we obtained above, we see a common problem: white space before and after the other characters. Trimming is a common first step in string processing. These extra spaces will eventually make splitting the strings hard so we start by removing them.  
We learned about the command str_trim that removes spaces at the start or end of the strings. Use this function to trim s and assign the result to s again.

After trimming, what single character is the last character of element 1 of s?
```{r}
s <- str_trim(s)
s[1] # print string, visually inspect last character
```
#### Question 6
We want to extract the numbers from the strings stored in s. However, there are a lot of non-numeric characters that will get in the way. We can remove these, but before doing this we want to preserve the string with the column header, which includes the month abbreviation.

Use the *str_which* function to find the row with the header. Save this result to *header_index*.  
Hint: find the first string that matches the pattern "2015" using the str_which function.

What is the value of header_index?
```{r}
header_index <- str_which(s, pattern="2015")[1]
header_index
```
#### Question 7
We want to extract two objects from the header row: *month* will store the month and *header* will store the column names.  
Save the content of the header row into an object called header, then use str_split to help define the two objects we need.

What is the value of month?
```{r}
tmp <- str_split(s[header_index], pattern='\\s+', simplify=TRUE)
month <- tmp[1]
header <- tmp[-1]
```
### Puerto Rico Hurricane Mortality: Part 2

#### Question 8
Notice that towards the end of the page defined by s you see a "Total" row followed by rows with other summary statistics. Create an object called tail_index with the index of the "Total" entry.
What is the value of tail_index?
```{r}
tail_index <- str_which(s, pattern="Total")
tail_index
```
#### Question 9
Because our PDF page includes graphs with numbers, some of our rows have just one number (from the y-axis of the plot). Use the str_count function to create an object n with the count of numbers in each row.  
How many rows have a single number in them?
```{r}
n <- str_count(s, pattern='\\d+')
which(n==1)
```
#### Question 10
We are now ready to remove entries from rows that we know we don't need. The entry header_index and everything before it should be removed. Entries for which n is 1 should also be removed, and the entry tail_index and everything that comes after it should be removed as well.

How many entries remain in s?
```{r}
s <- s[-c(1:header_index, which(n==1), tail_index:length(s))]
length(s)
```
#### Question 11
Now we are ready to remove all text that is not a digit or space. Do this using regular expressions (regex) and the str_remove_all function.
In regex, using the ^ inside the square brackets [] means not, like the ! means not in !=. To define the regex pattern to catch all non-numbers, you can type [^\\d]. But remember you also want to keep spaces.

Which of these commands produces the correct output?
```{r}
s <- str_remove_all(s, "[^\\d\\s]")
s
```
#### Question 12
Use the str_split_fixed function to convert s into a data matrix with just the day and death count data:
```{r}
s <- str_split_fixed(s, "\\s+", n = 6)[,1:5]
```

Now you are almost ready to finish. Add column names to the matrix: the first column should be day and the next columns should be the header. Convert all values to numeric. Also, add a column with the month. Call the resulting object tab.
```{r}
# colnames(s) <- c('day', header)
# parse_number(s[,1])
# tab <- data.frame(parse_number(s[,1]), parse_number(s[,2]), parse_number(s[,3]), parse_number(s[,4]), parse_number(s[,5]))
# colnames(tab) <- colnames(s)
# tab <- cbind(tab, month="SEP")
tab <- s %>% 
    as_data_frame() %>% 
    setNames(c("day", header)) %>%
    mutate_all(as.numeric)
tab
```
```{r}
# What was the mean number of deaths per day in September 2015?
mean(tab$`2015`)
# What is the mean number of deaths per day in September 2016?
mean(tab$`2016`)
# Hurricane Maria hit Puerto Rico on September 20, 2017. What was the mean number of deaths per day from September 1-19, 2017, before the hurricane hit?
mean(tab$`2017`[1:19])
# What was the mean number of deaths per day from September 20-30, 2017, after the hurricane hit?
mean(tab$`2017`[20:30])
```
#### Question 13
Finish it up by changing tab to a tidy format, starting from this code outline:
```{r}
tab <- tab %>% gather(year, deaths, -day) %>%
    mutate(deaths = as.numeric(deaths))
tab
```
#### Question 14
Make a plot of deaths versus day with color to denote year. Exclude 2018 since we have no data. Add a vertical line at day 20, the day that Hurricane Maria hit in 2017.
```{r}
tab %>%
    filter(year<2018) %>%
    ggplot(aes(day,deaths, color=year)) + 
    geom_line() +
    geom_vline(xintercept=20)
```
Which of the following are TRUE?

* September 2015 and 2016 deaths by day are roughly equal to each other.
* The day with the most deaths was the day of the hurricane: September 20, 2017.
* After the hurricane in September 2017, there were over 100 deaths per day every day for the rest of the month.
* No days before September 20, 2017 have over 100 deaths per day.
