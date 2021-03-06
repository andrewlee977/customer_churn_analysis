# customer_churn_analysis

IBM Sample Dataset found [here](https://www.kaggle.com/blastchar/telco-customer-churn)

The initial EDA in `customer_churn.ipynb` found that `tenure` (Number of months the customer has stayed with the company), `InternetService` (Customer's internet service provider – DSL, Fiber Optic, or No) and `Contract` (Type of Contract the customer is under) were the most important in accurately predicting customer churn. I then proceeded to dig deeper into these features in Tableau to discover additional insight for the stakeholder (Link to dashboard in `About` section of this repo).

![Dashboard](/assets/customer_churn_screenshot.png?raw=true "Dashboard")

# More on the EDA Notebook:
Model Performance ~79% accuracy at the time of this writing. Precision and Recall are low for predicting churn, ~65% and ~51%, respectively. The most important features in predicting user churn are `tenure` and `InternetService` (Found using Permutation Feature Importances technique). Dropping columns that don't contribute to the model (features that contribute less than 1% increase to model performance) improved the accuracy of the model. If I wanted to improve the accuracy score further, I would tune the hyperparameters of Logistic Regression/Random Forest using Randomized Search to find important hyperparameters, then follow it up with brute force Grid Search on specific hyperparameters to optimize further.

For the purpose of this analysis, incremental accuracy improvements is not the goal. Understanding the patterns in the data and finding the most important features in correctly predicting churned users is. That way these features can be focused on when diving deeper into the analysis, visualizing, and communicating these insights using Tableau.

Next Step is to import this dataset into Tableau and focus on the top features (`tenure` and `InternetService`) that contribute to the accuracy of the model to try to find and visualize the relationships between these features and `Churn`. This will help us understand which users will likely churn in the future and how to create initiatives around decreasing churn and increasing the LTV of users.

# Graph Breakdown

### Avg Tenure by Internet Service & Churn
The key insight for this visualization is understanding the average tenure of a churned customer based on their Internet Service. For example, if a customer is using Fiber Optic internet service and plans on churning, we can expect their average tenure to be ~20 months. If this is something the stakeholder would want me to dive into, I would look into the policies of these Internet Services in order to find some significance in this average tenure. For example, if we observe a decrease in contract quality or quality of service for Fiber Optic internet at or before month 20, we could look into how this might affect customer churn. We've all dealt with internet service providers, it's not a stretch to think a change in contract after the first year could be causing this. Just postulating.

From this analysis we'll also find that for customers who churn, the average tenure of that customer is longest when they use Fiber optic internet (~20 months) and shortest when having no internet service (~8 months). 

### Percent Churn by Tenure (0-5 months)
In my analysis, I found that the largest percentage of customer churn happens within the first 5 months. I wanted to dig deeper into when these customers are churning, specifically. The key insight in this chart is that the highest percentage of churn is happening in month 2 (61.99% churn rate). A possible initiative to combat this churn is to implement a customer retention program that kicks in around this time. 

### Avg Monthly Charges by Churn
I wanted to figure out if the Monthly Charges incurred by a customer has a relationship with Customer Churn. I found that the average monthly charge of a customer that churns is $74.44 while the average monthly charge of a customer who does not churn is $62.27. This tells me that price of services might be contributing to customer churn.

### Percent Churn by Tenure
The key insight here is the proportion of customers who churn is highest within the first five months of being a customer. The proportion of churn tapers off after this time. The longer a customer stays with the company, the less likely they are to churn, this seems pretty intuitive.

### Churn by Contract Type
I wanted to understand the breakdown of Customer Churn by the Contracts those customers are under. It's no surprise that Month-to-month customers are more likely to churn than longer term customers under the One year and Two year contracts. It is conducive to convert new customers to longer contracts as this will decrease the likelihood that they will churn, increasing the customer's Lifetime Value.

### Pie Charts
The pie charts, from top to bottom, show the percentage of customers who churn, percentage of customers by Internet Service, percentage of churned customers by internet service, and percentage of retained customers by internet service. I felt this would give a good high-level overview of the customers and how they are segmented based on the important features in question. Some important insights from these pie charts include:

1. 26.54% of total customers churn
2. Most customers use Fiber Optic Internet (~43.96%)
3. 69.40% of customers who churn were using Fiber Optic Internet (Higher than the proportion of all customers who use Fiber Optic Internet)
4. 42.91% of customers are under a Month-to-month contract. Month-to-month contracts increase the likelihood of Customer Churn

#### These are just a few of many visualizations that can be done here. When working with a product manager or stakeholder, I would create many different visualizations exploring the most important features in determining customer churn. From there, I would present my findings, and iterate on certain metrics that the stakeholder may want to look deeper into. 
