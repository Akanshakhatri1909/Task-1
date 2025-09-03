# Task-1
Data Cleaning and Preprocessing
I loaded my data into a Pandas DataFrame.
Used df.isnull().sum() to get a count of missing values in each column. This helped me see where the biggest gaps were.
I examined rows with missing data using df[df.isnull().any(axis=1)] to understand the context of the missingness. Are the missing values clustered in certain categories?
Based on the situation, I chose a treatment approach:
If a feature had only a few missing values and its absence could be treated as a "default" or "NA", and it didn't introduce bias, I filled them with a placeholder value using df.fillna(). Examples included filling numerical columns with 0 or the mean/median, or filling text columns with "Unknown".
If missing values represented an actual absence of data, I considered imputation using forward filling or backward filling if the order of records mattered, else considered predictive mean imputation for numerical columns, or mode imputation for categorical features.
If a large proportion of rows in a column had missing values, or I couldn't confidently impute them without introducing bias, I might have considered dropping the column entirely (with caution). Or I may have decided to remove the rows with missing values using df.dropna(). It’s important to be cautious, and ensure to only remove rows if the feature isn't critically important.
