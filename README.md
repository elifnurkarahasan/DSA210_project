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

***Accuracy, Confusion Matrix and RMSE scores of the Model:*** For accuracy scores, the cross-validation accuracy scores for the decision tree classifier range between 31% and 62%, with a mean accuracy of approximately 51.4%. This indicates moderate performance during validation and suggests that the model is somewhat effective at learning patterns in the training data. The test set accuracy is reported as 66.67%, which is notably higher than the mean cross-validation accuracy. This could indicate that the model performed better on the specific test set due to its composition or reduced data complexity. However, further evaluation, such as examining the confusion matrix and classification report, is necessary to validate this.

As for the classification report, it's precision provides high precision scores for genres such as Business Simulation (1.00), Card Game (1.00), and Simulation (1.00) indicating that when these genres are predicted, they are highly likely to be correct. Some genres, like Simulation, City-building, and Card Game, achieve a recall of 1.00, indicating that the model successfully identified all instances of these genres in the test set. The weighted average F1-score is 0.67, reflecting a balance between precision and recall. While it indicates reasonable performance, genres such as Action-adventure and Adventure have poor F1-scores of 0.00, signaling that the model struggles to predict these classes effectively.

As for the confusion matrix, genres such as Vehicle Simulation, Tactical Shooter, and Business Simulation show strong performance with minimal or no misclassifications.
However, significant misclassifications occur in genres with fewer data points, such as Survival and Survival Horror, which are confused with each other, likely due to overlapping feature characteristics.

For RMSE scores, the cross-validation RMSE scores range between 2.81 and 5.22, with a mean RMSE of 3.76. These values suggest moderately good performance in predicting game prices during training. The RMSE on the test set is 5.85, which is higher than the mean cross-validation RMSE. This indicates the model may not generalize as well on unseen data, though it is within an acceptable range given the complexity of price prediction.




**-Machine Learning Model Analysis 2: Random Forest Model**




***Purpose of the Visualization:*** The Random Forest model was also selected for its strength and flexibility in handling classification and regression tasks. Just like decision Tree model, the Random Forest model was employed to analyze two primary aspects of the data: genre prediction (classification) and price prediction (regression). This ensemble-based method combines the outputs of multiple decision trees, reducing overfitting and improving generalization. The primary reasons for choosing this model include the following: The ensemble nature of Random Forests typically yields better accuracy compared to single decision trees. Furthermore, the model provides clear feature importance rankings, offering valuable insights into which factors most influence predictions. Additionally, its ability to handle noise and outliers in the data (similar to deciion tree model) makes it suitable for datasets with mixed-quality attributes. The model’s adaptability to both classification and regression tasks was also an important advantage.

***Techniques Used & Stages of Analysis:*** Similar to decision tree model, Game genres were converted into numeric labels using LabelEncoder to enable model processing, and the SMOTE method was applied to balance the dataset, ensuring underrepresented genres were adequately sampled for training. While not critical for Random Forest, features were preprocessed to ensure compatibility with the machine learning pipeline. A Random Forest Classifier was trained to predict game genres. For cross-validation, a 5-fold Stratified K-Fold approach was used for classification, while standard K-Fold was used for regression, ensuring fair evaluation across subsets of the data. The model was configured with 100 estimators and class weights set to "balanced," enhancing its ability to manage class disparities. Just like Decision Tree model, this model's classifier was also evaluated using accuracy scores, a confusion matrix, and classification reports. The model was evaluated on the test set using a confusion matrix, which revealed its ability to distinguish between different genres effectively. A Random Forest Regressor was trained to estimate game prices. The regressor’s performance was assessed using RMSE (Root Mean Squared Error, as explained above). RMSE scores from cross-validation indicated the model’s predictive error, with a lower RMSE suggesting better performance. The Random Forest model identified Price/Hour as the most critical feature for predicting genres, followed by Time and Rating. This insight aligned with intuitive expectations, as cost efficiency and playtime are significant factors in game preferences. The model was tested with a hypothetical new game (Price/Hour = 0.20, Time = 50 hours, Rating = 90). The classifier predicted the genre, while the regressor estimated the game’s price, demonstrating the model’s real-world applicability.

***Accuracy, Confusion Matrix and RMSE scores of the Model:*** For the accuracy scores of this model, the cross-validation accuracy scores range between approximately 34% and 65%, with a mean cross-validation accuracy of 54.2%. This indicates moderate performance, with some variability in accuracy across the folds. The test set accuracy is 61.1%, which is slightly higher than the mean cross-validation accuracy. This suggests that the model generalizes reasonably well to unseen data, although there's room for improvement.

As for the classification report, the precision, recall, and F1-scores vary significantly across genres. Genres like "Card Game," "Simulation," and "Business Simulation" achieve perfect scores (precision, recall, and F1 = 1.0), indicating excellent prediction performance for these genres. Other genres, such as "Action-Adventure" and "Adventure," have scores of 0.0, meaning the model fails to predict them accurately. The weighted average F1-score is 58%, which is lower than the overall accuracy, reflecting imbalanced performance across classes.

The confusion matrix highlights the model's strengths and weaknesses, showing that genres such as "Vehicle Simulation" and "Tactical Shooter" are correctly classified in most instances, showing the model's ability to differentiate these categories. However, some genres like "Action-Adventure" and "Adventure" are consistently misclassified, indicating that the model struggles with these categories.

For the RMSE scores, the cross-validation RMSE scores range from approximately 2.49 to 4.72, with a mean RMSE of 3.57. These scores indicate that the model performs consistently well across folds. The test set RMSE is 5.19, which is slightly higher than the mean cross-validation RMSE. This suggests the model struggles slightly more with unseen data but still maintains reasonable performance.


**-Machine Learning Model Analysis 3: Naive Bayes Model**


***Purpose of the Visualization:*** I seleted the Naive Bayes algorithm for its efficiency, probabilistic nature, and interpretability. To explain; the Naive Bayes model is computationally lightweight and can quickly build models even with relatively small datasets. Furthermore, the model is particularly effective for classification tasks where feature independence is assumed, such as genre prediction. Additionaly, the underlying probabilistic calculations provide insights into how predictions are made, aligning well with my project’s goal of understanding gaming preferences. Another reason why I chose this model was because this model served as a complementary approach to the ensemble-based Random Forest, allowing for a comparison of performance and interpretability across models.

***Techniques Used & Stages of Analysis:*** Techniques used for this model include firstly to select numerical features such as Price/Hour, Time, and Rating for their relevance to predicting genres. Then, game genres were encoded into numeric values using LabelEncoder, enabling the model to process categorical labels. Features were scaled using StandardScaler to normalize their ranges, ensuring compatibility with the Naive Bayes algorithm. Similar to Random Forest and Decision Tree models, the dataset was augmented using SMOTE to address class imbalances. A Gaussian Naive Bayes Classifier was trained on the resampled data to predict game genres based on the selected features. For cross-validation, a 5-fold Stratified K-Fold cross-validation was implemented to evaluate model accuracy on various subsets of the data. Accuracy scores were computed during this 5-fold cross-validation, providing a reliable measure of the model's performance. The model was tested on unseen data, and results were summarized in a confusion matrix and a classification report, just like how it was done on Decision Tree and Random Forest models. Similarly, feature importance was approximated by analyzing the variances of input features, providing insights into which attributes influenced genre predictions. A hypothetical scenario was tested with a new game having specific attributes (Price/Hour = 0.20, Time = 50 hours, Rating = 90), the ame values used for Decision Tree and Random Forest models. However in this model, I chose not to use RMSE as it is a metric specific to regression tasks where the goal is to predict continuous values. In this model, the task was classification, aiming to predict category. For classification models like Naive Bayes, accuracy, confusion matrices, and classification reports are more appropriate metrics as they evaluate the correctness of categorical predictions rather than numerical errors.


***Accuracy and Confusion Matrix scores of the Model:*** For accuracy scores, the cross-validation accuracy scores range from 0.31 to 0.42, with a mean cross-validation accuracy of 0.38. These scores indicate that the model's generalization ability is relatively limited when tested on unseen data. The test set accuracy is 0.44, which means that the model correctly predicts the genre 44% of the time. While this performance is not particularly strong, it aligns with the simplicity of the Naive Bayes algorithm and the nature of the dataset.

As for classification report, genres such as Vehicle Simulation and Card Game have high precision, indicating that when the model predicts these genres, it is often correct. However, many genres, such as Action-Adventure and Adventure, have zero precision, reflecting poor performance for these classes. Recall is high for genres like Vehicle Simulation and Card Game, which means the model successfully captures most of these classes. Also, recall is zero for several underrepresented genres, indicating that the model is not strong in handling all classes. The F1-score, a harmonic mean of precision and recall, reflects similar trends. Genres with high precision and recall, such as Vehicle Simulation, show strong F1-scores, while others exhibit very low or zero F1-scores.

As for the confusion matrix, it reveals the breakdown of predictions for each genre. For example, Vehicle Simulation is accurately predicted with high consistency, as seen by its correctly predicted instances (diagonal values). Card Game also shows strong performance, with all its test cases correctly classified. Some genres, such as Action-Adventure and Adventure, are never correctly classified, resulting in zero correct predictions. This indicates that the Naive Bayes model struggles with genres that have overlapping features, leading to misclassification.


# Findings

In this section, findings derived from each of the visualizations and predictive models are given below.

**VISUALIZATION FINDINGS**

**-Finding 1: Pie Chart Visualization For Genre Distribution**

The pie chart reveals that Action RPG is the most played genre, accounting for 17.7% of my total playtime, followed by Simulation (12.9%) and City-Building (11.1%). These results highlight a preference for immersive and strategic gameplay experiences. Genres like Life Simulation (9.9%) and Survival (6.6%) also show moderate interest, while niche genres such as Turn-Based Strategy and Utility (Desktop Customization) make up less than 1% of my playtime. Overall, this analysis demonstrates a strong inclination towards genres with depth and replayability while reflecting less engagement with shorter or niche gameplay styles.


**-Finding 2: Visualization For Total Hours Spent Per Genre**

The bar chart illustrating total hours spent per genre provides valuable insight into my gaming preferences. Action RPG emerges as the most time-consuming genre, with nearly 500 hours of gameplay, reflecting my strong preference for immersive and story-driven experiences. Following closely are Simulation and City-Building, which collectively indicate a significant interest in strategic and creative gameplay elements. Genres such as Life Simulation and Survival Horror also stand out, showcasing their ability to engage me for extended periods. Interestingly, genres like Tactical Shooter, Flight Simulation, and Card Game appear at the bottom of the list, suggesting either a lack of appeal or limited availability within my game library. This visualization add on to my previous idea that I lean toward genres with high replayability and depth, while shorter, action-packed genres tend to take a backseat. These findings align with the broader theme of my gaming habits favoring strategy, exploration, and creativity over fast-paced gameplay.


**-Finding 3: Visualization For Total Money Spent Per Genre**

The bar chart of total money spent per genre reveals Action RPG as the genre I have invested the most in financially, surpassing other genres by a significant margin. This aligns with the findings from the hours-played visualization, highlighting a strong preference for immersive and narrative-rich experiences that tend to be more premium-priced. Survival and Action-Adventure also appear as genres with high monetary investment, suggesting that I am willing to pay for experiences that offer engaging challenges and exploration. Interestingly, genres such as Simulation, Business Simulation, and Construction and Management Simulation follow closely in terms of spending, indicating my inclination toward strategic and long-term planning games. These genres not only reflect my interest in depth and control but also justify their costs through extended playtime, as seen in the hours-played visualization. At the other end, genres like Multiplayer Online Battle Arena (MOBA), Card Game, and Utility (Desktop Customization) receive minimal financial investment, possibly reflecting their lower price points or limited appeal to my gaming preferences.

From these findings, I can deduce that my spending habits align with my enjoyment of genres offering immersive, complex, and replayable experiences. It also shows that while I may explore different genres, my primary financial commitment goes toward games that provide long-term value and personal satisfaction. One could also question the probability that Action RPG games in general are very expensive and it does not correlate to my gaming preferences. This would be a valid question if I had not visualized my total hours played per genre data. Visualizing that data showcased that the genres I play the most end up mostly being the genres I pay for the most. Therefore it can be deried that there is a correlation between my spending behavior and the genres of games I play the most.

**-Finding 4: Correlation Heatmap Visualization Among Numerical Features**

The correlation heatmap provides valuable information on the relationships between the numerical features in the dataset: Price, Time, Rating, and Price/Hour. One important observation is the moderately positive correlation between Price and Price/Hour (0.31), suggesting that games with higher hourly costs also tend to have higher purchase prices. This makes sense as premium-priced games often offer unique features or experiences that justify their cost per hour.
Interestingly, there is a slight negative correlation between Time and Price/Hour (-0.20). This implies that games played for longer durations tend to have lower hourly costs, aligning with the idea that the more time invested in a game, the better the value for money. However, this relationship is not strong, indicating variability in individual preferences and play styles. 
The weak positive correlation between Rating and Time (0.16) suggests that higher-rated games tend to be played slightly more, but the influence of rating on playtime appears limited. Similarly, the near-zero correlation between Price and Rating (-0.01) indicates that the price of a game does not directly reflect its popularity or quality as measured by ratings.
These findings highlight that while cost considerations such as price and hourly rate influence my gaming habits, they are not absolute determinants. Factors like enjoyment, genre preference, and replayability likely play a more significant role in shaping my playtime and spending patterns.


**-Finding 5: Average Rating Per Genre Visualization**

This bar chart displays the average ratings for each game genre, offering insights into the perceived quality and popularity of games in my collection. Genres like Utility (Desktop Customization), Metroidvania, and Vehicle Simulation emerge as the top-rated, indicating that these games resonate well with the player base or excel in their execution. On the other hand, genres like Transportation Simulation, Card Game, and Action-Adventure have lower average ratings, suggesting that they may not consistently meet player expectations or have polarizing features.
One significant observation is that genres with higher average ratings do not necessarily correspond to those I play the most. For example, Action RPG, a genre I have spent significant time playing, has a comparatively lower average rating. Also, in my former visualizations, the Utility genre appeared to be on the lowest side of my attention/interest focus, however, in this visualization it turned out to be a really popular genre. This disconnect highlights that my gaming preferences are not necessarily influenced by critics but mostly by personal enjoyment.


**-Finding 6: Number of Games Per Genre Visualization**

This bar chart illustrates the distribution of the number of games I own across different genres. Simulation dominates my collection, indicating a strong preference or interest in games that simulate real-world systems or activities. Genres like Adventure, Business Simulation, and Survival Horror also feature often, reflecting a varied focus on immersive and strategic experiences. Interestingly, genres such as Metroidvania, Role-playing, and Factory Simulation appear less frequently in my collection. This could signify a limited exploration of these genres or a more selective approach when purchasing games within these categories. The findings suggest a balanced gaming habit, where I actively engage with both complex simulation genres and story-driven or strategy-heavy games. However, the significant presence of simulation games also highlights a potential bias toward genres that offer long-term engagement or creative freedom.
This visualization reveals that my purchasing decisions lean heavily toward genres I find either engaging or replayable. It also provides that I may have an inclination to explore underrepresented genres like Metroidvania or Role-playing, which could offer fresh perspectives and expand my gaming experience.

**-Finding 7: Efficiency Analysis Scatter Plot Visualization**

This scatterplot provides insights into the relationship between the price paid per hour of gameplay and the total hours spent playing games across genres, this values aree then turned into an efficiency metric: This data can be interpreted as an 'efficiency' measure as the more time I spend for a game that costs less money per hour, the more efficient it becomes.  Genres like Simulation and Action RPG are positioned at the lower end of the price-per-hour scale while showing significant total hours played, indicating these genres offer high value for money. Conversely, genres such as Flight Simulation or Utility (Desktop Customization) have a higher price per hour but lower total hours, suggesting a lower efficiency or niche interest.
The visualization helps me understand which genres deliver the most engagement relative to cost. It also emphasizes the importance of balancing price and playtime when purchasing games, revealing my tendency to favor genres that provide longer-lasting entertainment.

**-Finding 8: Number of Games Per Genre Visualization**

This summary table provides an overview of my gaming habits, with numerical value representations into total hours played, total money spent, average ratings, and price-per-hour for each genre. Action RPG stands out as the genre with the highest total hours played (509 hours) and total spending ($80.34), reflecting its dominance in both time investment and monetary commitment. Simulation follows closely in total hours (372.1 hours), showing its significance in my gaming preferences despite a lower total spending of $36.86, indicating a high value-to-cost ratio. Overall, this table is important in understanding how I allocate time and money across different genres, which I can then use as information points for future gaming preferences.



**MACHINE LEARNING MODEL FINDINGS**

**-Finding 1: Decision Tree Model**

The Decision Tree model provided meaningful insights into my gaming habits and preferences by analyzing the relationships between gameplay metrics. The model's classification performance was reflected in its test set accuracy of 66.67%, along with moderate precision and recall scores for certain genres like "Business Simulation" and "Tactical Shooter." These results indicate that while the model can reliably predict some genres, others—such as "Action-adventure" and "Adventure" were harder to classify, possibly due to insufficient data or overlapping characteristics between genres.

The model highlighted the importance of features like "Rating" and "Time," which were identified as the most influential in predicting game genres. This finding aligns with the idea that my perception of a game's quality and the time I spend playing are closely tied to its genre. For example, genres like "Simulation" and "Vehicle Simulation" were predicted with high accuracy, suggesting that these are well-represented and distinct in my dataset.

The regression aspect of the Decision Tree provided further insights into my spending patterns. With an RMSE of 5.85 and an average test set price of 6.70 USD, the model demonstrated a fair ability to predict the price of a game based on features like "Price/Hour," "Time," "Rating," and "Genre." When predicting for a hypothetical new game with a "Price/Hour" of 0.20, 50 hours of gameplay, and a rating of 90, the model classified the genre as "Simulation" and estimated the price at approximately 7.86 USD. This prediction suggests that I might be inclined to spend a reasonable amount on highly engaging and well-rated games, especially within specific genres.

These findings reveal my inclination toward certain types of games that I consider high-value based on engagement and ratings. They align with the my findings about myself derived from visualizations, as they also indicate that I have a high interest in Simulation games. Overall, the Decision Tree model provided valuable information into both my gaming and purchasing preferance.

**-Finding 2: Random Forest Model**

The Random Forest model provided some intriguing insights into both classification and regression tasks. For the classification task, the model achieved a test set accuracy of 61%, which is moderate and highlights the complexity of predicting gaming genres based on the features provided. The confusion matrix indicates that while genres like "Vehicle Simulation" and "Card Game" were correctly classified with high precision and recall, others like "Action-adventure" and "Adventure" were misclassified frequently, possibly due to overlapping characteristics or insufficient distinguishing features. This suggests that my preferences in certain genres might not be as distinct as expected or that the features used for training the model do not entirely capture the intensity of these categories.

For regression, the model achieved a mean RMSE of approximately 5.19, with the test set prediction being reasonably close to the average price. When predicting the price of a new game based on the input features, the model estimated a price of $8.20 for a "Vehicle Simulation" game. While the predicted genre seems plausible given the features provided, it is important to reflect on whether the genre aligns with personal preferences or if it's a result of bias in the training data. In the viusalizations above, I had derived that although I had some interest in them, vehicle simulation games were not a significant preference of mine. This inconsistency could signify either a broader interest across multiple genres or that specific patterns in the data influenced the prediction disproportionately. Overall, the Random Forest model underscored my preference for highly rated games and emphasized that time investment in games correlates with perceived value. 

**-Finding 3: Naive Bayes Model**

The Naive Bayes model offers unique insights with noticeable limitations compared to other models. The overall accuracy of the Naive Bayes classifier on the test set is approximately 44.4%, which is significantly lower than the Decision Tree and Random Forest models. The mean cross-validation accuracy of 38.2% further suggests that this model struggles with the dataset's complexity, likely due to its assumptions of feature independence, which may not align well with the interdependent relationships in the data.

From the confusion matrix, we see that some genres, such as Vehicle Simulation, are predicted perfectly with high recall and precision. Similarly, Card Game achieves strong performance metrics, reflecting the model's ability to recognize specific genres with distinct characteristics. However, many genres, including Action-adventure, Adventure, and Simulation, have zero recall and precision, indicating that the model fails to identify these classes. This could stem from limited training samples or insufficient feature separability for these genres.

The feature importance visualization highlights that Time is the most influential feature in predicting genres, closely followed by Rating and Price/Hour. This aligns with the idea that the amount of time spent on a game correlates strongly with its genre, reflecting my gaming preferences and habits. The lesser role of Price/Hour indicates that cost efficiency plays a less critical role in genre determination, at least for this model.

For a hypothetical new game with features such as a Price/Hour of 0.20, 50 hours played, and a rating of 90, the Naive Bayes model predicts the genre as Turn-based Strategy. While this prediction might align with the observed data, the model's overall low accuracy raises questions about its reliability for decisions. This prediction also does not align well with the information I derived from my visualizations. The Turn-based Strategy genre never really appeared to be on the higher side of my preferences, yet the naive bayes model predicted it to be the genre I will buy a game of.

In summary, the Naive Bayes model provides some insight into genre prediction, particularly for well-represented and distinct classes, but its limited overall accuracy and inconsistent predictions highlight the importance of exploring other models.

**SUMMARY OF FINDINGS:**

Through this detailed analysis of my gaming habits using visualizations and machine learning models, I have gained deeper insights into my preferences, behaviors, and decision-making patterns. I learned that Action RPGs, Simulations, and City-building games dominate my gaming hours, reflecting my interest for immersive, strategic, and engaging experiences. These genres likely appeal to my enjoyment of complex, open-ended gameplay and the sense of progression they offer. Similarly, genres like Survival Horror and Life Simulation, though less prominent, demonstrate my curiosity for diverse gaming styles.

Ratings emerged as a not-so significant factor in shaping my decisions, which suggests that I sometimes prioritize quality and critically acclaimed experiences when exploring new games. However, the Price per Hour analysis revealed that while cost-efficiency is not my primary focus, I do gravitate towards games that provide lasting value, which aligns with my tendency to spend significant time in highly engaging games.

The machine learning models provided interesting predictions, offering a glimpse into patterns in my gaming choices. The Decision Tree and Random Forest models identified  features like time spent and ratings as major predictors of my preferences, emphasizing the weight I place on personal engagement with games. These two models were in more alignment with the findings I derived from the visualizations about myself. Interestingly, the models Randem Forest and Naive Bayes predicted genres like Vehicle Simulation and Turn-based Strategy (which are not on the higher side of my prefernces visualizations), therefore reflecting a mix of alignment with my current habits and potential areas for exploration. The Naive Bayes model, while less accurate, reinforced these themes and highlighted the importance of balancing diverse predictors to understand my preferences.

Overall, this process taught me that my gaming choices are not solely based on instinct but are influenced by a blend of enjoyment, financial value, and critical reception. I also learned how much I value long-term engagement and high-quality experiences over temporary enjoyment, fast paced games or cost-saving measures. Additionally, these findings encourage me to explore my less-played genres to expand my horizons while staying true to my core preferences.

# Limitations and Future Work

***Limitations and Future Work: What Could Be Done Better?***

While this project provided valuable insights into my gaming habits and preferences, it is not without its limitations. One major limitation is the size and diversity of the dataset. A larger dataset, with more comprehensive information on different genres, games, and player metrics, could enhance the reliability and accuracy of the analyses. Additionally, the use of SMOTE for class imbalance, while helpful, may not have fully addressed the challenge of accurately predicting underrepresented genres. Future work could involve gathering data from a wider range of sources to create a more balanced and representative dataset.

In addition, another area for improvement is the influence of external factors that were not accounted for in the analysis. Elements such as the platform on which games are played, community influences, marketing efforts, or seasonal trends in gaming habits were not considered. Incorporating these external variables could provide a more holistic understanding of the preferences and patterns in my gaming behavior.

The machine learning models also revealed limitations. While the Decision Tree and Random Forest models performed relatively well, the Naive Bayes model struggled with accuracy due to its assumptions and oversimplification of relationships among features. Future iterations could involve experimenting with more advanced models such as Gradient Boosting or Neural Networks to improve predictive accuracy. Moreover, integrating user behavior data, such as session lengths or in-game decisions, could provide richer context and improve the models' understanding of preferences.

Another area for improvement is the feature engineering process. The reliance on core metrics like time spent, ratings, and price per hour was effective but limited. Including additional features, such as game difficulty, multiplayer vs. single-player modes, or community feedback, could yield more nuanced insights into my decision-making patterns.

### Future Plans About the Project

Looking ahead, I may plan to extend this project by exploring recommendation systems. Using the insights gained from this analysis, I can then aim to develop a personalized recommendation engine that could suggest games based on my historical preferences, maximizing engagement and enjoyment. For any implementation in the future, I also plan to explore interactive tables to make the findings more accessible and visually appealing, allowing for  filtering and exploration of gaming trends.

In addition, I would like to refine the models to make them stronnger and versatile, potentially applying them to other domains such as movie or book recommendations. By leveraging additional algorithms and advanced analytics, I hope to create a system that not only reflects my current habits but also inspires me to explore new genres and expand my interests. This project has given me an amazing opportunity for understanding my preferences, and I am excited to perhaps build on it to further explore how data-driven findings can enhance personal decision-making.



