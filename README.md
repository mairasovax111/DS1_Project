# DS1_Project
#importing my dataset
data <- read.csv("mini_project/Dataset.csv")

#inspecting the data
print(head(data))
print(str(data))
print(summary(data))

#installing the necessary packages for plotting and visualising
install.packages("ggplot2")
library(ggplot2)

#cleaning data
data <- na.omit(data)


#doing descriptive statistics
summary (data)
mean_value <- mean(data$price_usd, na.rm = TRUE)
median_value <- median(data$price_usd, na.rm = TRUE)
sd_value <- sd(data$price_usd, na.rm = TRUE)
min_value <- min(data$price_usd, na.rm = TRUE)
max_value <- max(data$price_usd, na.rm = TRUE)

# Calculate average price per brand
avg_price <- aggregate(price_usd ~ brand, data = data, FUN = mean)

# Bar plot
ggplot(avg_price, aes(x = reorder(brand, -price_usd), y = price_usd)) +
  geom_bar(stat = "identity", fill = "lavender") +
  labs(title = "Average Price per Brand",
       x = "Brand",
       y = "Average Price (USD)") +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))
  
