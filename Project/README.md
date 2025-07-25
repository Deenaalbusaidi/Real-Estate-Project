# Real-Estate-Project
REAL ESTATE DATA COLLECTION AND CLEANING PROJECT

PROJECT OBJECTIVES
This project aims to simulate a real-world data science workflow by taking on the full data pipeline from data collection to exploratory modeling. I will be responsible for scraping property listings data from two real estate websites: Bayut Oman and Hilal Properties. The focus will be on rental properties, and I will extract key attributes such as title, location, price, size, number of rooms, and listing type.
Once the raw data is collected, I will clean and integrate it into a unified dataset, ensuring consistency in structure, formatting, and quality. I will then perform feature engineering to create meaningful variables that support analysis and potential predictive modeling. 
The final deliverables including all code, data files, and documentation will be organized in a public GitHub repository. This will include web scraping scripts, data cleaning and feature engineering code, and a README file outlining the project’s objectives, data sources, processing steps, and modeling approach.
In the sections that follow, I will briefly explain each step I took throughout the project, what I did, how I did it, and the reasoning behind my decisions at every stage of the workflow.

WEB SCRAPING
1.	Bayut Website 
Bayut is a popular online real estate platform primarily focused on the Middle East, including countries like Oman, UAE, and others. It allows users to search for properties available for rent or sale, including apartments, villas, offices, and more. Bayut provides detailed listings with information such as price, location, size, and property features, helping buyers, renters, and real estate agents connect efficiently. Here’s a detailed explanation of each part of your Bayut web scraping code, explaining what it does and why you included it:

•	Importing Libraries:
Importing necessary libraries for web scraping and data handling:
•	requests to send HTTP requests to the website and get HTML content.
•	BeautifulSoup to parse the HTML and extract data from it.
•	re (regular expressions) for flexible text matching and extraction.
•	time to pause execution between requests (politeness).
•	pandas for organizing the scraped data later into DataFrames.
Why:
These libraries are foundational for web scraping projects: you fetch pages, parse HTML content, extract relevant details, and store the data efficiently.



•	Setting Base URL and Headers
I have prepared the website address format to visit different pages and set headers to make our program look like a real browser to avoid blocks.
•	Preparing Storage
I have created empty lists to save property details like title, price, location, size, etc., as I find them.
•	Looping Through Pages 
I have told the program to visit each page of listings one by one, stopping if no more listings are found.
•	Finding Property Listings on Each Page 
I have found all the property ads on the current page so I can extract data from each.
•	Getting Basic Info from Each Listing
I have extracted the title, link, location, and price from each property listing on the page.
•	Extracting Location 
I have tried to guess it by looking inside the title using a text search.
•	Visiting Detail Pages for More Info 
For each property, I have opened its detailed page to find extra info like the number of bedrooms and size.
•	Collecting and Saving Data 
I have saved all the extracted details into our lists for later use.
•	Adding a Delay Between Requests  
I have waited 1 second between page visits to avoid overloading the website and prevent getting blocked.
•	Handling Errors 
If anything goes wrong during scraping, I have catched the error, print a message, and continue without stopping the whole program.
•	Ending Early if No Ads Found 
If a page doesn’t contain any listings, I stop scraping further pages to save time.
•	Checking Data Consistency 
I have checked to make sure all my lists have the same number of items so my dataset is complete and clean.
•	Converting to DataFrame 
At the end, Converts the dictionary into a table, and save it as CSV type of file.

2.	Hilal Website 
Hilal Properties (hilalprp.com.om) is a real estate website based in Oman that showcases properties available for rent and sale across various cities in the country. The platform offers listings for residential and commercial properties such as apartments, villas, offices, and shops. Each listing typically includes important details like price, location, size, number of rooms, and listing type. Hilal Properties serves as a bridge between property seekers and real estate agents or owners, helping users explore available options and make informed decisions. Here’s a detailed explanation of each part of your Hilal web scraping code, explaining what it does and why you included it:

•	Importing Libraries:
Importing necessary libraries for web scraping and data handling:
•	requests to send HTTP requests to the website and get HTML content.
•	BeautifulSoup to parse the HTML and extract data from it.
•	re (regular expressions) for flexible text matching and extraction.
•	time to pause execution between requests (politeness).
•	pandas for organizing the scraped data later into DataFrames.

•	Setting Base URL and Headers and Maximum Pages
I’m scraping property listings across multiple pages (up to page 18), and this structure lets me easily loop through them.
•	Creating the Data Storage Dictionary  
This allows me to collect structured data from each listing and organize it by category for easy conversion into a DataFrame.
•	Setting HTTP Headers 
To collect data from multiple pages automatically instead of manually going through them one by one.
•	Requesting the Web Page 
To get the page’s HTML content and make sure the page was loaded successfully before continuing.
•	Parsing and Finding All Listings 
Parsing and Finding All Listings.
•	Extracting Basic Property Info
These are important details for every property and are visible on the listing card.
•	Extracting Number of Rooms and Size 
To get more detailed features of the property that users usually care about.
•	Getting the Property Detail Page Link 
Some info (like location) is only available on the detail page, so we need this link to go deeper.
•	Extracting Location from the Detail Page   
Location is often not shown on the main listing card, so we go to the full page to find it accurately.
•	Saving All Extracted Data 
To keep all data organized and ready to be converted into a table or CSV later.
•	Delaying Between Requests 
Pauses for 1 second after each page.
•	Converting to DataFrame 
At the end, Converts the dictionary into a table, and save it as CSV type of file.

	Real Estate Project Jupyter Notebook
Setting The Environment
I have used several libraries which are:
1.	pandas
I used the pandas library to handle and manipulate my dataset efficiently. It allowed me to load data into DataFrames and perform operations such as filtering, grouping, and cleaning — essential steps before any analysis or model training.
2.	numpy
NumPy is a fundamental package for numerical computing in Python. It supports large, multi-dimensional arrays and provides efficient mathematical operations, which are essential for numerical tasks, statistical analysis, and working with matrix data in machine learning.
3.	seaborn
For data visualization, I used seaborn, which enabled me to create clear and informative plots with minimal code. This helped in exploring data distributions and relationships between features, which guided further preprocessing and model selection.
4.	matplotlib.pyplot
I also used matplotlib.pyplot to build custom visualizations and fine-tune aspects like plot titles, labels, and legends. This helped in presenting the data and model results more effectively.
5.	StandardScaler, MinMaxScaler, LabelEncoder (from sklearn.preprocessing)
To prepare the data for modeling, I used preprocessing tools from sklearn.preprocessing:
•	StandardScaler was used to standardize features, ensuring they had a mean of 0 and standard deviation of 1. This was important for models that are sensitive to feature scaling, like SVM or KNN.
•	MinMaxScaler was applied to normalize features within a specific range (usually 0 to 1), which is particularly useful for algorithms like neural networks or those using distance-based metrics.
•	LabelEncoder was used to convert categorical labels into numerical values, making them compatible with machine learning models that require numeric input.

Loading The Datasets
In this part of the project, I used the pandas library to read two CSV files containing the rental property data scraped from the Bayut and Hilal websites. The first file, bayut_properties_for_rent.csv, was loaded into a DataFrame called df, and it contains listings collected from the Bayut platform. Similarly, the second file, hilal_properties_for_rent.csv, was read into a DataFrame named df1, which holds the property data gathered from the Hilal website. Loading these files into pandas DataFrames allows me to easily explore, clean, analyze, and compare the datasets using various data science and visualization techniques.
Unfirming The Datasets Columns Names and Orders
In this section, I standardized and aligned the column names of both datasets to prepare them for comparison or merging. First, I defined a dictionary called rename_bayut to rename the column names in the Bayut dataset (df) so that they match the naming convention used in the Hilal dataset (df1). Before renaming, I normalized the column names in both DataFrames by converting them to lowercase and removing any leading or trailing spaces. This ensures consistency and avoids errors during renaming or merging. After renaming the Bayut columns, I checked whether the 'link' column existed in the Hilal dataset, and if it didn’t, I added it with None values to ensure both DataFrames have the same structure. Finally, I defined a list of final_columns to use as a standard format for both datasets moving forward. This step is crucial for clean data integration and further analysis.



Merging The Two Datasets 
To combine the two datasets into a single table, I used the pd.concat() function from the pandas library. Specifically, I merged the Bayut and Hilal DataFrames (df and df1) into a new DataFrame called df_merged. By setting ignore_index=True, I ensured that the row index was reset, resulting in a continuous sequence of index numbers in the combined DataFrame. This step was important to unify both datasets with matching column structures, allowing me to perform overall analysis, comparisons, and visualizations on all rental properties from both sources in one place.

Saving The Excel File In The Folder
After merging the Bayut and Hilal datasets into a single DataFrame called df_merged, I saved the combined data into two CSV files. The first line saves it as "merged_rent_listings.csv" in the current working directory, while the second line exports the same data to a specific location on my computer: C:\Users\bbuser\Desktop\Real Estate Project.csv. I set index=False in both cases to exclude the DataFrame index from being written into the CSV file. Saving the merged dataset ensures that I can easily access and analyze the combined rental property data later without needing to re-run the scraping and preprocessing steps.

PART 1: DATA CLEANING¶
Exploring the Data
To better understand the structure and content of the combined dataset, I performed some initial exploratory data analysis using pandas. The df_merged.shape command returns the number of rows and columns, giving me a quick overview of the dataset’s size. The df_merged.info() function provides detailed information about each column, including data types and the number of non-null values, helping identify missing or improperly typed data. I used df_merged.describe() to generate summary statistics for numeric columns such as price, size, or number of rooms, which helps identify trends, outliers, or inconsistencies. The df_merged.columns command lists all column names to confirm that they are correctly named and aligned. Finally, df_merged.head() and df_merged.tail() show the first and last few rows of the dataset, allowing me to preview the actual values and structure. Together, these commands are essential for gaining a quick and comprehensive understanding of the dataset before moving on to cleaning or analysis.

Exploratory Data Analysis (EDA)
To further analyze the contents of the merged dataset, I used several descriptive functions. First, df_merged. describe() provides summary statistics (such as count, mean, min, and max) for all numeric columns, helping me understand the distribution and range of numerical data like price, size, and number of rooms. Then, df_merged. describe(include='object') gives similar descriptive stats but for categorical (text) columns, such as property title, location, or listing type — showing details like the number of unique values and the most common entry. Lastly, df_merged.select_dtypes(include='number').columns returns a list of column names that have numeric data types, which is useful when I want to isolate numerical features for analysis, visualization, or modeling. These steps are key in understanding both the structure and the types of data in the dataset.


Converting Data Types From Object To Numeric 
I cleaned the number_of_rooms column by converting its values to strings, removing non-numeric characters, and then converting them back to numeric. This ensured the data is consistent and ready for analysis.
I cleaned the price column by converting all values to strings, removing any non-numeric characters like currency symbols or commas, and then converting the cleaned values back into numeric format. This ensures the price data is consistent and usable for numerical analysis.
I cleaned the size column by first converting all values to strings, then removing any non-numeric characters (such as units or symbols), and finally converting the cleaned values into numeric format. This step ensures the property size data is accurate and ready for analysis or visualization.

Handling Missing Columns 
After cleaning the number_of_rooms, price, and size columns, I used df_merged.isnull().sum() to check for missing values in the dataset. The output showed that while columns like property_title, price, and listing_type have no missing values, others like location (5 missing), number_of_rooms (19 missing), size (181 missing), and especially link (173 missing) contain gaps. These missing values likely resulted from issues during web scraping or data conversion (e.g., when non-numeric entries were coerced to NaN). This step is essential to identify which columns may need imputation, removal, or special handling before analysis.

Removing Null Values
I removed any rows from the dataset where the location column had missing values using dropna(subset=['location']). Since location is a critical feature for property analysis, keeping records without it would reduce data quality and usefulness. Dropping these rows ensures the dataset remains clean and reliable.

Filling Null Values 
To handle missing values in the dataset, I filled the number_of_rooms and size columns with their respective column means, ensuring these numerical fields remain usable for analysis without dropping valuable rows. For the link column, since it's a non-numeric field and might not be critical for analysis, I replaced missing values with the placeholder string 'NaN' to clearly indicate unavailable links without affecting the rest of the data. These steps improve data completeness and maintain dataset integrity for further exploration.

Checking For Null Values 
After applying the data-cleaning steps—dropping rows with missing location, filling missing values in number_of_rooms and size with their mean, and replacing missing link entries with the string 'NaN'—I ran df_merged.isnull().sum() again. This time, the result showed zero missing values across all columns. This confirms that the dataset is now complete and clean, with no NaN values remaining, and ready for analysis or modeling.






PART 2: DATA PREPPROCESSING
Outliers
To detect and handle outliers in the price column, I first examined the price distribution using describe() and a boxplot, which visually highlights extreme values. Then, I used the Interquartile Range (IQR) method to identify outliers. I calculated Q1 (25th percentile), Q3 (75th percentile), and the IQR (Q3 - Q1). Using this, I defined the lower and upper bounds for normal values as Q1 - 1.5*IQR and Q3 + 1.5*IQR. Any prices outside these limits were considered outliers. I printed these outliers for review and then filtered them out of the dataset to keep only the values within the acceptable range. This helps improve data quality by removing extreme values that could skew analysis or modeling.

Encoding
One Hot Encoding
To prepare the categorical data for machine learning models, I applied one-hot encoding using pd.get_dummies() on several columns: property_title, location, listing_type, and link. This technique converts each unique category in these columns into a separate binary (0 or 1) column, making them compatible with algorithms that require numerical input. By encoding these features, I transformed the dataset into a format suitable for analysis, modeling, and prediction tasks.

Feature Scaling (Normalization/Standardization)
To prepare the numerical features for modeling, I applied Min-Max Scaling using MinMaxScaler from sklearn.preprocessing. This technique transforms each value in the selected numeric columns—number_of_rooms, price, and size—to a range between 0 and 1, preserving the relative relationships between values. Scaling is essential for many machine learning algorithms (like KNN, SVM, etc.) that are sensitive to differences in scale. The result is stored in a new DataFrame called scaled_df, which contains the normalized versions of the original numeric data.

Feature Engineering
To enhance the dataset with more insightful variables, I created several new features:
1.	price_per_size – This calculates the cost per square meter by dividing price by size. It gives a better understanding of the property's value relative to its area.
2.	price_per_room – This is the average cost per room, obtained by dividing price by number_of_rooms. It helps compare affordability across listings with different room counts.
3.	room_density – Calculated by dividing number_of_rooms by size, this metric gives an idea of how densely rooms are distributed within the property’s area.
4.	location_frequency – This feature counts how often each location appears in the dataset. It reflects the popularity or data availability for each area, which can be valuable for modeling or weighting locations.
These engineered features provide more context for analysis and can improve model performance by capturing deeper patterns in the data.

Plotting 
1.	I created a bar chart to visualize the average rental price across different locations using Seaborn’s barplot. This chart helps identify which locations tend to have higher or lower average prices, providing valuable insights into regional market trends. The x-axis shows the property locations (rotated for better readability), and the y-axis represents the mean price for each location. The plot’s size and layout are adjusted for clarity and presentation, making it easier to compare pricing differences visually.
2.	I created a scatter plot to visualize the relationship between property size and price. Each point represents a property, showing how price changes with size. This plot helps identify trends, such as whether larger properties tend to have higher prices, and can also reveal any unusual patterns or outliers in the data.
3.	I created a box plot to show the distribution of property prices across different locations. This visualization displays the median, quartiles, and potential outliers for prices in each area, allowing us to compare price variability and spot extremes within locations. The x-axis represents locations (rotated for readability), and the y-axis shows the price range. This helps understand how prices vary not just on average but across the spread within each location.
4.	I used Seaborn’s pairplot to visualize the pairwise relationships between all numerical variables in the dataset. This plot creates scatterplots for each pair of features and histograms (or KDE plots) for individual feature distributions. It helps identify correlations, trends, and potential patterns between variables like price, size, and number of rooms, giving a comprehensive overview of how these features interact.
5.	I created a pairplot with hue='location' to visualize relationships between numerical variables while also highlighting differences across locations. By coloring data points based on their location, this plot helps to see how the distributions and correlations of features like price, size, and number of rooms vary between different areas. It’s a powerful way to spot location-specific patterns and clusters within the dataset.

Correlation Heatmap
know the numeric columns
I calculated the correlation matrix of the dataset using df_merged.corr(numeric_only=True). This matrix shows the strength and direction of linear relationships between the numerical features such as price, size, and number_of_rooms. Values range from -1 to 1, where values close to 1 indicate strong positive correlation, values near -1 indicate strong negative correlation, and values around 0 mean little to no linear relationship. This helps identify which features are related and can guide feature selection or engineering for modeling.
Creation of Heatmap
I created a heatmap to visually represent the correlation matrix of the numerical features in the dataset. Using Seaborn’s heatmap with annotations, it clearly shows the strength and direction of correlations between variables like price, size, and number_of_rooms. The color gradient (from cool to warm) helps quickly identify strong positive or negative relationships, making it easier to understand feature interactions and guide further analysis or modeling decisions.



Building and evaluating a Linear Regression model
•	Feature and target selection:
I prepared the dataset by selecting all columns except price as features (X). Since some features are categorical, I converted them into numeric format using one-hot encoding (pd.get_dummies), which creates binary columns for each category, dropping the first to avoid multicollinearity. The price column is set as the target variable (y).
•	Data splitting:
The data was split into training and testing sets using an 80-20 split (train_test_split). This allows the model to learn patterns on the training data and be evaluated on unseen test data, helping to assess generalization.
•	Model training:
I created a Linear Regression model (LinearRegression) and trained it on the training set (X_train, y_train). This model tries to find the best linear relationship between features and the rental price.
•	Prediction:
After training, the model predicts prices on the test set (X_test).
•	Evaluation:
I calculated two key metrics to assess model performance:
•	Mean Squared Error (MSE): 
Measures the average squared difference between actual and predicted prices. Lower values indicate better predictions.
•	R-squared (R2): 
Shows how well the model explains the variance in prices (ranges 0 to 1, higher is better).

These metrics help to understand how accurately the model predicts rental prices based on property features.

