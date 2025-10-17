-Global-University-Rankings-Data-Analysis

The primary goal of this project is to clean, process, and analyze the QS World University Rankings 2025 dataset to derive insights, identify top-performing universities, explore global distribution, and perform conditional hypothesis testing on key performance indicators.


  🛠️ Technologies Used
  
   - Python
   - Pandas (Data manipulation and cleaning)
   - NumPy (Numerical operations and imputation)
   - JyputerNoteBook

  🚀 Analysis Steps and Key Findings
  
  1. Data Loading and Initial Inspection:-
    - The dataset is loaded into a pandas DataFrame, and initial checks are performed to understand its structure and                content.
    - Data Source: qs-world-rankings-2025.csv
    - Initial Check: The DataFrame contains 1503 entries and 16 columns.
    - Data Types: Initial dtypes are: 9 float64 and 7 object.

  2. Missing Value Analysis and Imputation:-
    - Missing values are identified, counted, and imputed using appropriate strategies.

      (i) Missing Value Counts:-
        - International Faculty: 100 missing values (6.65% of total).
        - International Students: 58 missing values (3.86% of total).
        - 2024 Rank: 21 missing values (1.40% of total).
        - Sustainability: 19 missing values (1.26% of total).
        - International Research Network: 1 missing value (0.07% of total).
    
      (ii) Imputation Strategy:-
        - Numerical Columns (International Faculty, International Research Network, International Students, Sustainability):             Missing values were imputed with the median of their respective columns.
        - Categorical Column (2024 Rank): Missing values were imputed with the string 'Unknown'.
        - Result: All columns now have 0 missing values after imputation.

      (iii) Data Type Conversion for QS Overall Score:-
         - The QS Overall Score column was initially of object type and contained non-numeric characters, which needed                    cleaning and conversion to a numeric type
         - Initial Type: object.
         - Cleaning Steps: Non-numeric characters (e.g., '*', non-digit/dot characters, whitespace) were removed.
         - Conversion and Imputation: The column was converted to float64 , resulting in 903 NaN values from non-                         convertible entries. These new NaN values were imputed with the column's median score.
         - Final Type: float64.

      (iv) Feature Engineering (Z-Score):-
         - A new feature, 'QS Overall Score Z-Score', was calculated to standardize the scores and facilitate outlier                     detection.
           - Mean QS Overall Score: $38.54.
           - Standard Deviation QS Overall Score: $12.18.
           - Formula: Z-score = (Score - Mean) / Standard Deviation.
           - Result: The final DataFrame has 17 columns, including the new Z-Score column, and all columns have 1503 non-null               entries.
       (v) Data Analysis and Insights:-
         - Top 10 Countries by Ranked Universities
           The United States (US) leads with the highest number of ranked universities, followed by the United Kingdom (UK)
            and China (CN).

        Location	            Count
           US	                 197 
           UK	                 90 
           CN	                 71 
           JP	                 49 
           DE	                 48

        - Correlation Analysis
           A correlation matrix was calculated for key scoring columns:


             Names                 QS Overall 	    Academic 	    Int. Reseearch
                                     Score         Reputation       Network
          
           QS Overall Score         1.000000                         0.801470           0.359102

           Academic Reputation      0.801470         1.000000        0.588874

           Int. Research Network    0.359102         0.588874        1.000000

        - There is a strong positive correlation ($0.80$) between QS Overall Score and Academic Reputation.
    
        - Outlier Identification
           Outliers were identified as universities with a QS Overall Score Z-Score greater than 3 in magnitude                           (|Z - Score| > 3).

        - A total of 54 universities were identified as top outliers, starting from Massachusetts Institute of Technology                (MIT) (Z-Score: 5.04) down to University of Bristol (Z-Score: 3.03).
    
        - Conditional Hypothesis Test (Top 10 vs. All Universities)
         (i) Faculty Student Ratio Score:
            - Average Faculty Student Score (Top 10): 93 
            - Average Faculty Student Score (All Universities): 28
            - Conclusion: The top 10 universities have a significantly higher average Faculty Student score.

        (ii) International Faculty Score:
            - Average International Faculty Score (Top 10): 94 
            - Average International Faculty Score (All Universities): 30
            - Conclusion: The top 10 universities have a significantly higher average score for International Faculty.
