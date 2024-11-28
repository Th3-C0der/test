PR - 1
```
# a) Print a built-in dataset

# Printing the built-in 'mtcars' dataset

print(mtcars)

# b) Get information about the dataset

# Using the 'str()' function to get the structure of the dataset

str(mtcars)

# Using the 'ncol()' and 'nrow()' functions to get the number of rows and columns

cat("Number of rows in the dataset:", nrow(mtcars), "\n")

cat("Number of columns in the dataset:", ncol(mtcars), "\n")

# c) Find dimensions of the dataset and view the names of the variables

# Dimensions can be obtained using the 'dim()' function

# Variable names can be viewed using the 'names()' function

cat("Dimensions of the dataset:", dim(mtcars), "\n")

cat("Names of the variables:", names(mtcars), "\n")

# d) Find name of each row in the first column

# We can use the row names along with the first column to display them

cat("Names of rows in the first column:", rownames(mtcars), "\n")

# e) Print all the values of any variable of your choice from the dataset

# Printing all the values of the 'mpg' (miles per gallon) variable

cat("Values of the 'mpg' variable:", mtcars$mpg, "\n")

# f) Get statistical summary of the dataset

# Using the 'summary()' function to get the statistical summary

cat("Statistical summary of the dataset:\n")

summary(mtcars)
```

PR - 2
```
# a) Load and print a built-in dataset in R

df <- data.frame(iris)

print(df)

# b) Calculate Variance

# Calculating the variance of the Sepal.Length column

cat("Variance of Sepal.Length:", var(df$Sepal.Length), "\n")

# c) Calculate Standard Deviation

# Calculating the standard deviation of Sepal.Length column

cat("Standard Deviation of Sepal.Length:", sd(df$Sepal.Length), "\n")

# d) Calculate Range

# The range is the difference between the maximum and minimum values

range_sepal_length <- range(df$Sepal.Length)

cat("Range of Sepal.Length: From", range_sepal_length[1], "to", range_sepal_length[2], "\n")

# e) Calculate Mean Deviation and Skewness

# Mean deviation is the average of absolute differences from the mean

mean_deviation_sepal_length <- mean(abs(df$Sepal.Length - mean(df$Sepal.Length)))

cat("Mean Deviation of Sepal.Length:", mean_deviation_sepal_length, "\n")
```
```
# To calculate skewness, we need the 'e1071' package (for skewness function)

install.packages("e1071")

library(e1071)

# Skewness of Sepal.Length

cat("Skewness of Sepal.Length:", skewness(df$Sepal.Length), "\n")

Conclusion:

Statistical measures such as variance, standard deviation, range, mean de
```

PR - 4
```
# Load the 'mtcars' dataset

df <- data.frame(mtcars)

# a) Perform Spearman Rank Correlation Test

cor_test <- cor(df$mpg, df$wt, method="spearman")

# Displaying results of the Spearman Rank Correlation Test

cat("Spearman Rank Correlation Test Results:\n")

cat("Correlation Coefficient:", cor_test, "\n")

# Interpreting the correlation coefficient

if (cor_test > 0) {

cat("Positive correlation\n")

} else if(cor_test < 0) {

cat("Negative correlation\n")

} else {

cat("Zero or no correlation\n")

}
```
PR - 5
```
# a) Calculate the probability of getting heads when flipping a fair coin

outcomes <- c("heads", "tails")

total_outcomes <- length(outcomes) # Total no. of possible outcomes

favourable_outcomes <- length(outcomes[outcomes=="heads"])

# No. of outcomes in which we get a head

prob_head <- favourable_outcomes / total_outcomes

cat("Probability of getting a head when flipping a fair coin:", prob_head, "\n")

# Calculate the probability of drawing a spade from a standard deck of 52 cards.

deck <- rep(c("spades", "hearts", "diamonds", "clubs"), each = 13)

total_cards <- length(deck)

spades <- length(deck[deck == "spades"])

prob_spade <- spades / total_cards

cat("Probability of drawing a spade from a standard deck of cards:", prob_spade, "\n")
```
PR - 7
```
# a) Use Bayes Theorem in R

# Suppose we know the following probabilities:

# P(rain) = 0.20

# P(cloudy) = 0.40

# P(cloudy|rain) = 0.85

# To calculate P(rain|cloudy):

P_R <- 0.2

P_C <- 0.4

P_CR <- 0.85

P_RC <- P_CR * P_R / P_C # P(rain|cloudy)

cat("P(rain|cloudy):", P_RC)
```
PR - 8
```
extrapolation <- function(x, y, xp) {

n <- length(x)

if (xp < min(x)) { # if value to be predicted is smaller than available range

slope <- (y[2] - y[1]) / (x[2] - x[1])

yp <- y[1] + slope * (xp - x[1])

} else if (xp > max(x)) { # if value to be predicted is larger than available range

slope <- (y[n] - y[n - 1]) / (x[n] - x[n - 1])

yp <- y[n] + slope * (xp - x[n])

} else { # if value to be predicted falls within the available range

stop("xp must be outside the range of x for extrapolation") # Stops program execution

}

return (yp)

}

#Main Program

x <-c( 0.3, 0.5, 0.7, 0.9)

y <- c(1.8, 2.1, 2.4, 2.7)

xp <- 1.2

extrapolated_value <- extrapolation(x, y, xp)

cat("Extrapolated value at x = 1.2 is", extrapolated_value, "\n")
```
PR - 10
```
# a) Based on Chi-Square Distribution using dchisq, pchisq, qchisq, rchisq functions

# Defining the intervals (x) and degrees of freedom (df)

x <- seq(0, 5, by=1)

df <- 2

# 1. dchisq(): Chi-Square Probability Density Function (PDF)

dchisq_vals <- dchisq(x, df)

cat("The value of the probability density function up to x = 5 is:\n", dchisq_vals, "\n\n")

# 2.pchisq(): Chi-Square Cumulative Distribution Function (CDF)

pchisq_vals <- pchisq(x, df)

cat("The cumulative probability up to x = 5 is:\n", pchisq_vals, "\n\n")

# 3. qchisq(): Quantile function (Inverse CDF)

# Calculating the quantile for the cumulative probability 0.95

qchisq_vals <- qchisq(0.95, df)

cat("The quantile for the cumulative probability 0.95 is:", qchisq_vals, "\n\n")

# 4. rchisq(): Generate random values from a Chi-Square distribution

rchisq_vals <- rchisq(10, df)

cat("10 random values from a Chi-Square distribution with df = 2:\n", rchisq_vals, "\n")
```
