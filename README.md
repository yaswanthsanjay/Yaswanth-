# Yaswanth-
1. Import Libraries
The program imports the pandas library, which is essential for handling and analyzing structured data in Python.

2. Define Functions
The program uses the following functions to perform specific tasks:

load_data(file_path, chunk_size=10000):

This function loads the data from a given file. It supports .csv and .json formats.

If the file is a CSV and exceeds the specified chunk size (default: 10,000 rows), it processes the file in chunks to handle large datasets efficiently.

For .json files, it reads the entire file directly.

It returns a DataFrame object containing the loaded data. If an error occurs (e.g., invalid file format or reading issue), it returns None.

clean_data(df):

This function performs basic data cleaning.

Specifically, it removes rows with missing values (NaN) using the dropna() method to ensure the dataset is ready for analysis.

summarize_data(df):

This function provides a summary of the dataset.

It uses describe() to display summary statistics (e.g., mean, min, max) for numerical columns.

It also lists the column names of the DataFrame.

3. main() Function
This serves as the entry point of the program. It follows these steps:

Specifies the file path of the dataset (e.g., "Global_AI_Content_Impact_Dataset.csv").

Calls load_data() to load the data from the file.

If the data is successfully loaded (i.e., not None), it cleans the data by calling clean_data() and summarizes it using summarize_data().

If the data loading fails, it prints an error message.

4. Execution
The program executes the main() function when run directly.

This is controlled by the conditional if __name__ == "__main__": statement, ensuring proper script execution.

5. Purpose
The program is a basic tool for processing and analyzing structured data.

It’s especially useful for handling large CSV files efficiently with chunking.
1. Libraries
The program uses the pandas library to handle and analyze structured data in DataFrames.

2. Functions Defined
load_and_clean_data(file_path)
This function performs the following:

Load Data: Reads a CSV file from the specified file_path.

Handle Missing Values: Drops rows with missing values using dropna(inplace=True).

Convert Percentages to Numeric: Converts certain columns containing percentage data (e.g., 'AI Adoption Rate (%)', 'Job Loss Due to AI (%)') into numeric format using pd.to_numeric. If conversion fails, the row is marked as NaN.

Drop Rows with Conversion Issues: Rows with invalid data after conversion are dropped to ensure data consistency.

Output: Returns a clean DataFrame.

avg_adoption_by_industry(df)
Groups the data by the column 'Industry' and calculates the average 'AI Adoption Rate (%)' for each industry.

Sorts the averages in descending order.

Output: A sorted list showing the average AI adoption rate per industry.

country_with_max_job_loss(df)
Identifies the country with the highest value in the column 'Job Loss Due to AI (%)'.

Extracts and returns the 'Country' and 'Job Loss Due to AI (%)' for the row with the maximum job loss.

correlation_adoption_revenue(df)
Calculates the correlation between 'AI Adoption Rate (%)' and 'Revenue Increase Due to AI (%)' using .corr().

Output: Returns the correlation coefficient, which indicates the strength and direction of the relationship between the two variables.

3. Main Function Logic
The main() function performs the following:

Specify File Path: Specifies the location of the dataset (e.g., "Global_AI_Content_Impact_Dataset.csv").

Load and Clean Data: Calls load_and_clean_data() to prepare the dataset.

Perform Analyses:

Displays the average AI adoption rate per industry by calling avg_adoption_by_industry().

Shows the country with the highest job loss due to AI using country_with_max_job_loss().

Prints the correlation coefficient between AI adoption and revenue increase using correlation_adoption_revenue().

4. Output
When the program is executed, it displays:

📊 Average AI Adoption Rate by Industry: A ranked list of industries by average AI adoption rates.

🚨 Country with Highest Job Loss Due to AI: The country with the largest percentage of job loss due to AI.

📈 Correlation between AI Adoption and Revenue Increase: A numeric value describing how strongly AI adoption and revenue growth are related.
1. Libraries Used
pandas: For data manipulation and analysis.

sklearn: Specifically, it uses train_test_split for splitting the data, RandomForestRegressor for building the machine learning model, and LabelEncoder for preprocessing categorical variables.

numpy: For numerical computations, such as calculating the square root.

sklearn.metrics: Provides methods like mean_squared_error and r2_score for evaluating the model.

2. Workflow Breakdown
Step 1: Load the Dataset
The program reads the dataset from a CSV file using pd.read_csv("Global_AI_Content_Impact_Dataset.csv").

The dataset is expected to contain information about the impact of AI, including features like country, industry, AI tools used, regulation status, and revenue increase due to AI.

Step 2: Encode Categorical Variables
Categorical columns like 'Country', 'Industry', 'Top AI Tools Used', and 'Regulation Status' are encoded into numerical values using LabelEncoder.

This step is necessary because machine learning models can only work with numeric data.

The LabelEncoder is stored in the dictionary label_encoders for later reference (e.g., converting numbers back to original categories).

Step 3: Define Features and Target
The program splits the dataset into:

Features (X): All columns except 'Revenue Increase Due to AI (%)'.

Target (y): The column 'Revenue Increase Due to AI (%)', which the model will predict.

Step 4: Split the Dataset
The dataset is split into training and testing subsets using train_test_split:

Training Set (X_train, y_train): Used to train the model.

Testing Set (X_test, y_test): Used to evaluate the model.

20% of the data is set aside for testing (test_size=0.2).

Step 5: Create and Train the Model
A RandomForestRegressor model is created and trained on the training set.

Random Forest is an ensemble learning method that uses multiple decision trees to make predictions. It is effective for regression tasks and handles nonlinear relationships well.

Step 6: Predict and Evaluate
The model predicts the target (y_pred) on the testing dataset (X_test).

Evaluation Metrics:

Root Mean Squared Error (RMSE): Measures the average error between predicted values and actual values. Lower RMSE indicates better model performance.

R² Score: Indicates how well the model explains the variance in the data. A score closer to 1 signifies better performance.

3. Output
The program prints:

RMSE: A numeric value showing the model's prediction error.

R² Score: A numeric value indicating the model's explanatory power.
1. Libraries Used
pandas: For handling and processing the dataset in tabular format.

matplotlib.pyplot: For creating static, publication-quality visualizations.

seaborn: A library built on matplotlib to simplify data visualization and produce aesthetically pleasing graphs.

2. Workflow Breakdown
Step 1: Load the Dataset
The program loads a CSV file ("Global_AI_Content_Impact_Dataset.csv") using pd.read_csv().

Step 2: Display Basic Information
The dataset's structure is explored using the following:

df.info(): Displays column names, data types, and the number of non-null entries in each column.

df.head(): Shows the first five rows to get a quick preview of the data.

Step 3: Handle Missing Values
Rows with missing values (NaN) are dropped using df.dropna(inplace=True) to ensure clean data.

Step 4: Analyze Impact Score by Region
If the columns 'Region' and 'Impact_Score' exist in the dataset:

Group and Calculate: Groups data by 'Region' and calculates the average 'Impact_Score' for each region using .groupby() and .mean().

Sort: Regions are sorted by their average impact score in descending order for easier comparison.

Step 5: Visualization
A horizontal bar chart is created using seaborn.barplot():

X-axis: Average impact scores.

Y-axis: Regions.

Palette: A color scheme ("viridis") for better visual differentiation.

The chart is customized with titles and labels for clarity and displayed using plt.show().

Step 6: Handle Missing Columns
If columns like 'Region' or 'Impact_Score' are missing, the program prints a message to inform the user that the dataset's structure needs to be verified.

3. Output
The program displays:

Basic metadata about the dataset.

The first five rows for preview.

A table of average impact scores grouped by region (if the required columns exist).

A horizontal bar chart visualizing the average impact scores across regions.
1. Libraries Used
pandas: For data manipulation and analysis.

print() and input(): For creating an interactive menu system where users can choose their desired analysis.

2. Workflow Breakdown
Step 1: Load the Dataset
The program loads the dataset from a CSV file (Global_AI_Content_Impact_Dataset.csv) using pd.read_csv().

The dataset is stored in the df variable as a DataFrame.

Step 2: Menu System
The show_menu() function displays a list of options for analysis:

View overall statistics.

Filter by country.

Filter by industry.

View correlation matrix.

Exit the program.

Step 3: Individual Functions
Each option is implemented as a separate function:

Overall Statistics (overall_stats())
Provides a statistical summary of all columns using df.describe(include='all').

This includes metrics like mean, median, and unique values, depending on the data type.

Filter by Country (filter_by_country())
Prompts the user to enter a country name.

Filters the dataset to include only rows where the 'Country' column matches the user’s input (case-insensitive).

Displays the filtered rows.

Filter by Industry (filter_by_industry())
Prompts the user to enter an industry name.

Filters the dataset to include only rows where the 'Industry' column matches the user’s input (case-insensitive).

Displays the filtered rows.

Correlation Matrix (correlation_matrix())
Selects numeric columns in the dataset using df.select_dtypes(include='number').

Calculates the correlation matrix (pairwise correlation coefficients between numeric columns) using .corr().

Displays the matrix, showing relationships between variables.

Step 4: Main Loop
The program uses a while True loop to repeatedly show the menu until the user chooses to exit.

The user's choice is captured with input():

If the input matches one of the options (1-5), the corresponding function is executed.

If the input is invalid, the program prints an error message and displays the menu again.

Choosing option 5 exits the program, with a goodbye message.

3. Output
Depending on the user's choice, the program performs the following:

Option 1: Prints overall statistics for the dataset.

Option 2: Filters and displays data for a specific country entered by the user.

Option 3: Filters and displays data for a specific industry entered by the user.

Option 4: Prints the correlation matrix for numeric columns, showing relationships between variables.

Option 5: Exits the program with a goodbye message.
1. Loading the Dataset
The program reads a CSV file named Global_AI_Content_Impact_Dataset.csv into a DataFrame using pd.read_csv().

This data serves as the foundation for all analysis in the program.

2. Menu System
The show_menu() function displays a menu with five options:

View overall statistics.

Filter by country.

Filter by industry.

View correlation matrix.

Exit the program.

The user interacts with this menu through an input loop, and their choice determines what action the program performs.

3. Functions for Analysis
Each menu option is implemented as a separate function:

Option 1: View Overall Statistics (overall_stats())
This function uses df.describe(include='all') to provide a summary of the dataset, including:

Statistical measures for numeric columns (e.g., mean, min, max).

Counts and unique values for non-numeric columns.

It gives users a comprehensive overview of the dataset.

Option 2: Filter by Country (filter_by_country())
Prompts the user to input a country name.

Filters rows in the dataset where the 'Country' column matches the input (case-insensitive).

Displays the filtered rows, showing all available data for the specified country.

Option 3: Filter by Industry (filter_by_industry())
Similar to the previous function, but it filters data based on the 'Industry' column.

Prompts the user to input an industry name and displays the filtered results.

Option 4: View Correlation Matrix (correlation_matrix())
Extracts only the numeric columns in the dataset using df.select_dtypes(include='number').

Computes the correlation matrix using .corr() to identify relationships between numeric variables.

Correlation values range from -1 to 1:

1: Strong positive relationship.

-1: Strong negative relationship.

0: No relationship.

Displays the matrix, which helps identify trends or dependencies between numeric columns.

Option 5: Exit
Exits the program with a polite goodbye message.

4. User Input and Main Loop
The program runs in a while True loop, continuously displaying the menu until the user chooses to exit.

Input (input()) is taken from the user:

Based on the input, the corresponding function is executed.

If the input is invalid, the program prompts the user to enter a valid choice (1-5).

5. Output
Depending on the user's choice, the program displays:

A detailed statistical summary for the dataset.

Filtered rows for a specific country.

Filtered rows for a specific industry.

A correlation matrix for numeric columns.

If the user selects 5
