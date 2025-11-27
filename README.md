# Box-Office-Analysis
Box-Office-Analysis is an R project that analyzes box office numbers for the Star Wars movies included in the dataset. The repository contains an R script that creates vectors of domestic and international earnings, builds matrices and data frames, computes worldwide totals, and reports summary results.

## Data Source  
Box office grosses (domestic, international, worldwide) taken from the Star Wars franchise summary page on The Numbers.  
[https://www.the-numbers.com/movies/franchise/Star-Wars#tab=summary](https://www.the-numbers.com/movies/franchise/Star-Wars#tab=summary)  

## Skills demonstrated
This project showcases  use of:
- Creating and naming vectors
- Building and labeling matrices
- Adding computed rows to a matrix
- Constructing data frames
- Organizing results inside a list
- Printing formatted output


## How to run
- Requirements: R (no additional packages required for the basic script).
- From an R console:
  - source("box_office_analysis.R")
- From the command line:
  - Rscript box_office_analysis.R

## Dataset
The analysis uses the following (sample) data (values are in millions):

- Movies:
  - Star Wars Episode I
  - Star Wars Episode II
  - Star Wars Episode III (The best one)
  - Star Wars Episode IV
  - Star Wars Episode V
  - Star Wars Episode VI

- Domestic earnings (millions): 460, 290, 310, 340, 410, 380  
- International earnings (millions): 550, 610, 620, 500, 450, 470

## Example R script
A minimal example script used to generate the results:

```r
# vectors of our earnings and movie titles
domestic <- c(488, 316, 414, 460, 291, 316)
international <- c(1046, 657, 902, 775, 549, 482)

movie_titles <- c("Star Wars Episode I", "Star Wars Episode II", "Star Wars Episode III (The best one)",
                  "Star Wars Episode IV", "Star Wars Episode V", "Star Wars Episode VI")

# Combine into a matrix
box_office <- rbind(domestic, international)
rownames(box_office) <- c("Domestic", "International")
colnames(box_office) <- movie_titles
worldwide <- box_office["Domestic", ] + box_office["International", ]
box_office_worldwide <- rbind(box_office, Worldwide = worldwide)

# Convert to a data frame
movie_data <- data.frame(
  Movie = movie_titles,
  Domestic = domestic,
  International = international,
  Worldwide = worldwide
)

# analysis
highest_movie <- movie_data$Movie[which.max(movie_data$Worldwide)]
total_revenue <- sum(movie_data$Worldwide)

# Put results in a list
results <- list(
  Matrix = box_office_worldwide,
  DataFrame = movie_data,
  HighestGrossing = highest_movie,
  TotalRevenue = total_revenue
)

# Print results
print("=== BOX OFFICE MATRIX (in millions)===")
print(box_office_worldwide)

print("=== DATA FRAME (in millions)===")
print(movie_data)
cat("Highest grossing movie:", highest_movie, "\n")
cat("Total revenue (all movies in millions):", total_revenue, "\n") 

## Results (from the above run)
Note: values are in millions.

=== BOX OFFICE MATRIX (in millions) ===

```
Movie                               Domestic  International  Worldwide
-----------------------------------------------------------------------
Star Wars Episode I                 488       1046           1534
Star Wars Episode II                316       657            973
Star Wars Episode III (The best one)414       902            1316
Star Wars Episode IV                460       775            1235
Star Wars Episode V                 291       549            840
Star Wars Episode VI                316       482            798

```

Summary:
- Highest grossing movie: Star Wars Episode I
- Total revenue (all movies, in millions): 6696
