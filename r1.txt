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
First Line
Second Line