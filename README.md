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
domestic <- c(460, 290, 310, 340, 410, 380)
international <- c(550, 610, 620, 500, 450, 470)

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
```

## Results (from the above run)
Note: values are in millions.

=== BOX OFFICE MATRIX (in millions) ===
```
                          Star Wars Episode I Star Wars Episode II Star Wars Episode III (The best one) Star Wars Episode IV Star Wars Episode V Star Wars Episode VI
Domestic                                460                   290                                  310                 340                 410                 380
International                           550                   610                                  620                 500                 450                 470
Worldwide                              1010                   900                                  930                 840                 860                 850
```

=== DATA FRAME (in millions) ===
```
                                 Movie Domestic International Worldwide
1                 Star Wars Episode I      460           550      1010
2                Star Wars Episode II      290           610       900
3 Star Wars Episode III (The best one)      310           620       930
4                Star Wars Episode IV      340           500       840
5                Star Wars Episode V      410           450       860
6                Star Wars Episode VI      380           470       850
```

Summary:
- Highest grossing movie: Star Wars Episode I
- Total revenue (all movies, in millions): 5390

## How to run
- Requirements: R (no additional packages required for the basic script).
- From an R console:
  - source("box_office_analysis.R")
- From the command line:
  - Rscript box_office_analysis.R
