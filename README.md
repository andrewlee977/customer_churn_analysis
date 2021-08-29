# user_churn_analysis

The initial EDA in `customer_churn.ipynb` found that `tenure` (Number of months the customer has stayed with the company) and `InternetService` (Customer's internet service provider – DSL, Fiber Optic, or No) were the most important in accurately predicting customer churn. I then proceeded to dig deeper into these two features in Tableau to discover additional insight for the stakeholder (Link to dashboard in `About` section of this repo).

![Dashboard](/assets/dashboard.png?raw=true "Dashboard")

# More on the EDA Notebook:
Model Performance ~77% accuracy at the time of this writing. Precision and Recall are low for predicting churn, ~58% and ~46%, respectively. The most important features in predicting user churn are `tenure` and `InternetService` (Found using Permutation Feature Importances technique). Dropping columns that don't contribute to the model (features that contribute less than 1% increase to model performance) improved the accuracy of the model. If I wanted to improve the accuracy score further, I would tune the hyperparameters of Logistic Regression/Random Forest using Randomized Search to find important hyperparameters, then follow it up with brute force Grid Search on specific hyperparameters to optimize further.

For the purpose of this analysis, incremental accuracy improvements is not the goal. Understanding the patterns in the data and finding the most important features in correctly predicting churned users is. That way these features can be focused on when diving deeper into the analysis, visualizing, and communicating these insights using Tableau.

Next Step is to import this dataset into Tableau and focus on the top features (`tenure` and `InternetService`) that contribute to the accuracy of the model to try to find and visualize the relationships between these features and `Churn`. This will help us understand which users will likely churn in the future and how to create initiatives around decreasing churn and increasing the LTV of users.

# Graph Breakdown

### Avg Tenure by Internet Service & Churn
The key insight for this visualization is understanding the average tenure of a churned customer based on their Internet Service. For example, if a customer is using Fiber Optic internet service and plans on churning, we can expect their average tenure to be ~20 months. If this is something the stakeholder would want me to dive into, I would look into the policies of these Internet Services in order to find some significance in this average tenure. 

### Percent Churn by Tenure (0-5 yrs)
In my analysis, I found that the largest percentage of customer churn happens within the first 5 months. I wanted to dig deeper into when these customers are churning, specifically. The key insight in this chart is that the highest percentage of churn is happening in month 2 (61.99% churn rate). A possible initiative to combat this churn is to implement a customer retention program that kicks in around this time.

### Percent Churn by Tenure
The key insight here is the proportion of customers who churn is highest within the first five months of being a customer. The proportion of churn tapers off after this time. 

### Proportion of Churn & Internet Service by Tenure
I wanted to add another layer to the previous graph by adding Internet Service. I thought it would be important to visualize how most churned customers are Fiber Optic internet users. 

### Pie Charts
The pie charts, from top to bottom, show the percentage of customers who churn, percentage of customers by Internet Service, percentage of churned customers by internet service, and percentage of retained customers by internet service. I felt this would give a good high-level overview of the customers and how they are segmented based on the important features in question.
