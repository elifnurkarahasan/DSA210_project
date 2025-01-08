# DSA210 PROJECT REPORT

# Motivation

**-Project Idea & Motivation:**

Throughout my years of playing games, I always had difficulties in finding games that suit my liking. Although I am not someone who plays games all the time, I have played quite a lot of games. However, due to the rising game prices in the Steam application, it has become much more important to buy games that are actually worth the money you are paying for them. I have thought on this and decided that the way to decide if a game is worth buying is to understand what I like and how many hours I play a game for (in other words, how long the game keeps me entertained). Therefore my goal is to analyze my historical gaming data to predict future preferences, including identifying favorite genres, estimating genres of future game purchases along with their (predicted) prices, analyzing purchase trends, understanding patterns, and evaluating preferences.


# Data Source

**-Dataset Collection:**

I got this data by utilizing Steam's "Steam DB" feature. Steam DB is one of Steam's qualities which offers its users to see their gaming data in a tabular manner. Various gaming data of users are listed in this page, and users can easily access the data they are trying to find about their account.

I collected the data by copying the rows of data in my Steam DB one by one and pasting them into an excel file I created. I had modified the excel file so that it contains the associated column names in the Steam DB. I transfered each row of data into the excel file and achieved an extensive steam account dataset. To use this data for my project's visualization and prediction modeling stage, I included a section at the start of my code that enabled uploading documents.

**-Dataset Description:**

The dataset focuses on my personal Steam profile to then help me visualize and analyze gaming preferences and behavior patterns. The attributes that will be presented in the dataset include game title, genre, playtime (hours), game rating, price, and price per hour.


# Project Plan

1) Data Collection: Gather and preprocess data from my Steam profile. Prepare the dataset, its attributes and their values accordingly.

2) Exploratory Data Analysis (EDA): Visualize and summarize patterns in the dataset.

3) Model Development: Build predictive models for analyzing stage, such as for finding out game preferences and future purchase estimations.

4) Insight Generation: Derive actionable insights from the analysis.

5) Documentation and Reporting: Present findings with visualizations and a detailed report.

6) Deliverables: Structured dataset, analysis report, predictive model, GitHub repository with code, visualizations.


# Data Analysis

In this section of the report, I will be giving the techniques used and different stages of analysis one by one, starting with each of my visualizations and moving onto each of the machine learning models I have implemented to predict future choices. I will explain the data analysis by seperating my analysis into 2 parts: visualization stage and prediction stage. Inside each part, I will explain the techniques used, stages of analysis, the analyzed data, what was intended to be derived by implementing them, and extensive explanations.

**VISUALIZATION PART**




**-Analysis 1: Pie Chart Visualization For Genre Distribution**

***Purpose of the Visualization:*** The main objective of this visualization was to gain insights into the distribution of genres in my Steam account. By using a pie chart, I intended to identify which genres occupied the largest share of the total genres existing in my account and to understand my genre preferences at a glance. This would allow me to evaluate whether my gaming habits are dominated by a specific genre or spread across diverse categories.

***Techniques Used & Stages of Analysis:*** For this visualization, I employed a pie chart for illustrating proportional distributions, this technique was chosen because it provides a clear and visually engaging way to represent proportional data. To create this visualization, I first preprocessed the dataset to calculate the total time spent playing games for each genre. This involved grouping the data by genre and summing up the respective playtimes. The resulting genre_summary DataFrame served as the input for the pie chart. Using Python’s Matplotlib library, I customized the chart with additional visual enhancements, such as exploding small slices (slices having less than 5% contribution) for better differentiation and diagonal annotations to avoid label overlaps. These adjustments were necessary to improve readability and effectively present the data since there are many genre values to visualize in my dataset.




**-Analysis 2: Visualization For Total Hours Spent Per Genre**



***Purpose of the Visualization:*** The purpose of this visualization was to quantify and visually present the amount of time I have spent playing games in each genre. Unlike the pie chart, which highlights proportional representation, this bar chart provides a precise view of the absolute playtime for each genre. My intention was to determine which genres have consumed the most of my gaming hours and which ones have played a smaller role. This information would help me reflect on my gaming habits and preferences with greater granularity.

***Techniques Used & Stages of Analysis:*** For this visualization, I utilized a bar chart ass it is an effective technique for comparing quantitative values across different categories. By employing Seaborn’s barplot function, I designed a horizontal bar chart that allows for easy comparison of total hours spent across all game genres in my dataset. The chart was further enhanced by sorting the genres in descending order of playtime, ensuring that the most-played genres are displayed at the top for clarity. I grouped the data by genre and summed the total hours played for each category. This data (stored in the genre_summary DataFrame) served as the foundation for the visualization. I used the viridis palette to provide a professional appearance to the chart. Additionally, I adjusted the axis labels, font sizes, and layout to ensure the chart remained readable and visually appealing.




**-Analysis 3: Visualization For Total Money Spent Per Genre**



***Purpose of the Visualization:*** This visualization was created to analyze my spending habits on game genres. It helps identify which genres I have invested the most money in and which ones have been relatively inexpensive. By combining these insights with other visualizations, such as total hours played (Visualization 2) and proportional genre distribution (Visualization 1), I aimed to uncover patterns in my spending behavior. For example, do I spend more money on genres I play the most, or do I purchase expensive games that I rarely play? The results would help me answer such questions. Similar to Visualization 2, I chose to visualize this data as a bar chart in order to provide a representation of absolute values, as it enables a more accurate understanding of how much I’ve spent on different genres.

***Techniques Used & Stages of Analysis:*** This visualization was done with almost an identical manner to Visualization 2. The only difference were the metrics used; I utilized the 'Price' values for the visualization of this bar chart whereas in Visualization 2, I had used the 'Time' values. Still, to give a brief explanation, it can be stated that a bar chart was employed by using Seaborn’s barplot function. By sorting the genres in descending order based on the total money spent (Price), the visualization was designed to highlight the most and least expensive genres in my collection. A horizontal bar chart format was chosen for better readability of genre names, especially since some genres have longer titles. The coolwarm color palette was used to emphasize the variations in spending, providing a clear visual contrast between high and low spending categories.




**-Analysis 4: Correlation Heatmap Visualization Among Numerical Features**




***Purpose of the Visualization:*** This heatmap was created to identify any significant relationships between features in my dataset. Understanding correlations is essential to gaining insights into how different variables interact. For example; does the time I spend playing games correlate with the price of those games? Is there a relationship between game ratings and their Price/Hour efficiency? The heatmap served as a foundation for interpreting patterns and behaviors in my gaming habits, and undeerstanding this information was crucial in the analysis of my data. It allowed for quick identification of patterns and anomalies, making it easier to explore how different variables interact and influence one another.

***Techniques Used & Stages of Analysis:*** For this visualization, I created a correlation heatmap using Seaborn’s heatmap function. The heatmap was designed to analyze the relationships between the features in my dataset: Price, Time, Rating, and Price/Hour. By calculating the correlation coefficients for all feature pairs using Pandas’ .corr() method, I aimed to explore both positive and negative correlations. The coolwarm color palette was chosen for this visualization to clearly distinguish between positive correlations (red) and negative correlations (blue). As a more in-depth explanation of the stages of this analysis: firstly I selected the relevant numerical columns from my dataset: Price, Time, Rating, and Price/Hour. Missing values in the selected columns were dropped using Pandas’ .dropna() method to ensure the calculations were accurate. The correlation matrix was calculated using Pandas’ .corr() method. This method computes Pearson correlation coefficients, which range from -1 (strong negative correlation) to +1 (strong positive correlation), with 0 indicating no correlation. The correlation matrix was visualized using Seaborn’s heatmap function. Each cell in the heatmap represents the correlation coefficient between a pair of features. The diagonal cells always have a value of 1.0, as each feature is perfectly correlated with itself. The annot=True parameter was used to display the correlation coefficients directly on the heatmap for easy interpretation. The figure size was set to ensure all labels and annotations were visible and easy to read.




**-Analysis 5: Average Rating Per Genre Visualization**




***Purpose of the Visualization:*** This visualization was designed to provide insight into the popularity level of the games within each genre based on their ratings. The average rating serves as a metric for how well-received the games in each genre are by the general gaming community. By analyzing this data, I intended to: Determine which genres consistently have highly-rated games, explore whether there is a relationship between the genres I prefer to play and their average ratings, and to see how much of the games in the genres I play are popular games and how much of them is not. A bar chart was chosen for this visualization because it compares the average ratings across genres, making it easy to identify the highest and lowest-rated categories. 

***Techniques Used & Stages of Analysis:*** For this visualization, I employed a bar chart to showcase the average rating of games I’ve played in each genre. The bar chart was created using Seaborn’s barplot function, with the genres sorted in descending order based on their average rating values. Firstly for data preparation, I used the genre_summary dataset, which already contained pre-aggregated values for the average rating (Rating) of games grouped by genre. Genres were sorted in descending order of their average ratings using Pandas’ .sort_values() method. A horizontal bar chart was created using Seaborn’s barplot function. This orientation was chosen to ensure that genre names were fully visible and easy to read.
The cubehelix color palette was applied to ensure differentiation between bars without distracting from the data itself. The tight_layout() function ensured that no elements overlapped or were cut off in the final visualization.




**-Analysis 6: Number of Games Per Genre Visualization**

***Purpose of the Visualization:*** This visualization aimed to provide insights into the popularity of genres in my gaming collection by analyzing the number of games per genre. By observing these counts, I intended to: Identify which genres dominate my collection, understand my preferences based on the genres I tend to buy more frequently, and compare the results with other visualizations (like time spent per genre or total money spent per genre) to uncover trends in my gaming habits.

***Techniques Used & Stages of Analysis:*** For this visualization, I employed a horizontal bar chart to display the count of games for each genre in my collection. Using Seaborn's barplot function, the genres were ordered based on the number of games they contained. The muted color palette was chosen to maintain visual clarity. The Genre column from the dataset was analyzed using the .value_counts() method to compute the number of games in each genre. The resulting counts were stored in a new DataFrame named genre_counts with columns Genre and Game Count for clarity. A horizontal bar chart was chosen because it is ideal for comparing discrete categories (genres) against a numerical value (game count). The barplot function from Seaborn was used, and the genres were sorted in descending order of the number of games to highlight the most prevalent categories. The tight_layout() function ensured that all elements of the chart were properly spaced and readable.




**-Analysis 7: Efficiency Analysis Scatter Plot Visualization**




***Purpose of the Visualization:*** The primary goal of this visualization was to analyze the efficiency of my gaming experience, where efficiency is defined as the time I spend playing a game relative to its cost per hour. With this visualization I intended to: explore the relationship between Price/Hour (cost-efficiency) and Total Hours Played for each genre,
identify genres that provide the most value for money by offering high playtime at a low cost per hour, and highlight genres that might be less efficient in terms of cost relative to time spent. The reeason behind why I chose to implement a scatter plot was because it effectively displays the relationship between two continuous variables (Price/Hour and Total Hours Played) while accommodating additional dimensions (genre and rating). The ability to visualize multiple aspects of the data in a single chart made this technique particularly useful for analyzing efficiency.

***Techniques Used & Stages of Analysis:*** For this visualization, I used a scatter plot to explore the relationship between Price Per Hour and Total Hours Played across different genres. Seaborn's scatterplot function was utilized to plot the data, with distinct colors for genres, bubble sizes representing average game ratings, and a clear labeling system to highlight the dimensions of the data. A distinct colormap (tab20) was chosen to ensure visual clarity and to differentiate between the genres effectively. The data was grouped by Genre, and key metrics such as Total Hours Played, Price Per Hour, and Rating were extracted from the dataset to form the basis of the analysis. The x-axis represents Total Hours Played, indicating how much time I dedicated to games in each genre. The y-axis represents Price Per Hour, signifying the monetary cost of playing games in each genre on a per-hour basis. The size of the points corresponds to the average game rating, adding an extra layer of information about the quality of games in each genre. Each genre was assigned a unique color for easier identification.




**-Analysis 8: Number of Games Per Genre Visualization**

***Purpose of the Visualization:*** For this visualization, I implemented an interactive summary table. The goal of this visualization was to provide an overview of my total gaming investment in terms of time, money, and game quality for each genre. This summary table helped me clearly visualize the following in a tabular manner: The total time I spent playing games belonging to each genre, the cumulative amount of money I invested in purchasing games of each genre, an the average popularity or quality of games within each genre, derived from their ratings. This summary allowed me to see the overall distribution of my gaming habits and spending patterns.

***Techniques Used & Stages of Analysis:*** The interactive summary table was implemented by using the DataTable library in Google Colab. This table puts key metrics for each genre into a structured format, making it easy to compare and analyze numerical data at a glance. Metrics such as Total Hours Played, Total Money Spent, and Average Rating were aggregated for each genre using the groupby and agg functions. Column names were updated to improve clarity, ensuring that each column succinctly described the data it represented. The metrics were displayed in an interactive table format using DataTable. I selected this technique to make the data filterable in order to enhance accessibility for better analysis of my data.




**MACHINE LEARNING MODELS PART**




**-Machine Learning Model Analysis 1: Decision Tree Model**




***Purpose of Choosing the Model:*** The Decision Tree model was implemented to predict two aspects of gaming preferences: genre prediction and price prediction. These predictions were made in each machine learning model I implemented. The Decision Tree model was chosen for its interpretability and efficiency in handling both classification and regression tasks. Its hierarchical structure allowed for a clear understanding of decision-making processes, which was crucial for deriving actionable insights from the data. Furthermore, the model's capability to handle mixed data types and its strength with outliers made it a suitable choice for this dataset. This model was particularly appealing because it could clearly identify relationships between features such as playtime, cost efficiency, and ratings. Also, it can highlight which features were most influential in predicting the genre and price of games, and it can provide interpretable outputs like feature importance scores and decision boundaries, making the results more accessible and understandable. Additionaly, since my data is limited, using cross validation could be a good appraoch to evaluate the impact.

***Techniques Used & Stages of Analysis:*** Firstly for data preprocessing, features such as Price/Hour, Time, and Rating were used for both classification and regression tasks. Genres were encoded numerically using the LabelEncoder for machine learning compatibility. For genre prediction, I used a classification approach to identify the most likely genre of a new game based on its attributes. For price prediction, I employed a regression approach to estimate the price of a game within a specific genre based on the same features. To handle class imbalances in genre data, the SMOTE method was applied. This ensured that underrepresented genres were adequately sampled during training, improving model fairness and strength. Both the classifier and regressor were validated using stratified K-fold and standard K-fold cross-validation to ensure performance consistency across different data splits. The contribution of each feature was measured using the inherent importance metric of the Decision Tree model. Classification accuracy, confusion matrix, and RMSE (a metric that quantifies the error between predicted and actual prices) were used to evaluate to what extent the classifier and regressor models were accurate or erroneus. The model was tested with a hypothetical new game (Price/Hour = 0.20, Time = 50 hours, Rating = 90). The classifier predicted the genre, and the regressor estimated the price for this new game, showcasing the model's ability to generalize to unseen data.




**-Machine Learning Model Analysis 2: Random Forest Model**




***Purpose of the Visualization:*** The Random Forest model was also selected for its strength and flexibility in handling classification and regression tasks. Just like decision Tree model, the Random Forest model was employed to analyze two primary aspects of the data: genre prediction (classification) and price prediction (regression). This ensemble-based method combines the outputs of multiple decision trees, reducing overfitting and improving generalization. The primary reasons for choosing this model include the following: The ensemble nature of Random Forests typically yields better accuracy compared to single decision trees. Furthermore, the model provides clear feature importance rankings, offering valuable insights into which factors most influence predictions. Additionally, its ability to handle noise and outliers in the data (similar to deciion tree model) makes it suitable for datasets with mixed-quality attributes. The model’s adaptability to both classification and regression tasks was also an important advantage.

***Techniques Used & Stages of Analysis:*** Similar to decision tree model, Game genres were converted into numeric labels using LabelEncoder to enable model processing, and the SMOTE method was applied to balance the dataset, ensuring underrepresented genres were adequately sampled for training. While not critical for Random Forest, features were preprocessed to ensure compatibility with the machine learning pipeline. A Random Forest Classifier was trained to predict game genres. For cross-validation, a 5-fold Stratified K-Fold approach was used for classification, while standard K-Fold was used for regression, ensuring fair evaluation across subsets of the data. The model was configured with 100 estimators and class weights set to "balanced," enhancing its ability to manage class disparities. Just like Decision Tree model, this model's classifier was also evaluated using accuracy scores, a confusion matrix, and classification reports. The model was evaluated on the test set using a confusion matrix, which revealed its ability to distinguish between different genres effectively. A Random Forest Regressor was trained to estimate game prices. The regressor’s performance was assessed using RMSE (Root Mean Squared Error, as explained above). RMSE scores from cross-validation indicated the model’s predictive error, with a lower RMSE suggesting better performance. The Random Forest model identified Price/Hour as the most critical feature for predicting genres, followed by Time and Rating. This insight aligned with intuitive expectations, as cost efficiency and playtime are significant factors in game preferences. The model was tested with a hypothetical new game (Price/Hour = 0.20, Time = 50 hours, Rating = 90). The classifier predicted the genre, while the regressor estimated the game’s price, demonstrating the model’s real-world applicability.




**-Machine Learning Model Analysis 2: Naive Bayes Model**




***Purpose of the Visualization:*** I seleted the Naive Bayes algorithm for its efficiency, probabilistic nature, and interpretability. To explain; the Naive Bayes model is computationally lightweight and can quickly build models even with relatively small datasets. Furthermore, the model is particularly effective for classification tasks where feature independence is assumed, such as genre prediction. Additionaly, the underlying probabilistic calculations provide insights into how predictions are made, aligning well with my project’s goal of understanding gaming preferences. Another reason why I chose this model was because this model served as a complementary approach to the ensemble-based Random Forest, allowing for a comparison of performance and interpretability across models.

***Techniques Used & Stages of Analysis:*** Techniques used for this model include firstly to select numerical features such as Price/Hour, Time, and Rating for their relevance to predicting genres. Then, game genres were encoded into numeric values using LabelEncoder, enabling the model to process categorical labels. Features were scaled using StandardScaler to normalize their ranges, ensuring compatibility with the Naive Bayes algorithm. Similar to Random Forest and Decision Tree models, the dataset was augmented using SMOTE to address class imbalances. A Gaussian Naive Bayes Classifier was trained on the resampled data to predict game genres based on the selected features. For cross-validation, a 5-fold Stratified K-Fold cross-validation was implemented to evaluate model accuracy on various subsets of the data. Accuracy scores were computed during this 5-fold cross-validation, providing a reliable measure of the model's performance. The model was tested on unseen data, and results were summarized in a confusion matrix and a classification report, just like how it was done on Decision Tree and Random Forest models. Similarly, feature importance was approximated by analyzing the variances of input features, providing insights into which attributes influenced genre predictions. A hypothetical scenario was tested with a new game having specific attributes (Price/Hour = 0.20, Time = 50 hours, Rating = 90), the ame values used for Decision Tree and Random Forest models. However in this model, I chose not to use RMSE as it is a metric specific to regression tasks where the goal is to predict continuous values. In this model, the task was classification, aiming to predict category. For classification models like Naive Bayes, accuracy, confusion matrices, and classification reports are more appropriate metrics as they evaluate the correctness of categorical predictions rather than numerical errors.




# Findings


# Limitations and Future Work





