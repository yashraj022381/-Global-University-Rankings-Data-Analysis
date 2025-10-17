# -Auto MPG--(Miles Per Gallons)--Data-Analysisby using ML Gardient Descent with Python Numpy & Pandas

This project involves a comprehensive data cleaning, exploration, and analysis workflow on a dataset containing global university rankings (such as those from QS, THE, or similar sources). 

The goal is to transform raw, messy ranking data into structured, actionable insights about the global higher education landscape, including regional performance, score distributions, and factors that correlate with top rankings.

The entire process, from data acquisition to final analysis, is performed using the powerful data manipulation capabilities of Pandas and the statistical functions of NumPy.

 Key Project Highlights:-
  - Complete Data Workflow: Demonstrated proficiency in the end-to-end data science process: Data Cleaning, Missing Value            Handling, Type Conversion, Grouping/Aggregation, and Exploratory Analysis.

  - String-to-Numeric Conversion: Successfully addressed a common real-world issue by cleaning non-numeric characters from           critical score columns (like QS Overall Score) to enable quantitative analysis.

  - Statistical Foundation: Calculated and interpreted key metrics (Mean, Median, Standard Deviation, Z-Scores) to normalize         data and identify statistically significant outliers.

  - Structured Aggregation: Used advanced Pandas groupby() and agg() techniques to summarize university performance across         categorical dimensions like Country and Region.

    🛠️ Technology Stack
        Tool	         Purpose
        Python	       Primary programming language.
        Pandas	       Data cleaning, manipulation, handling missing values, grouping, and aggregation.
        NumPy	         High-performance statistical and numerical computations (e.g., mean, standard deviation, Z-scores).
        Jupyter/IDE	   Interactive environment for development and documentation of the analysis.

    📊 Step-by-Step Analysis & Methodology
       The project followed a rigorous four-phase approach:-
    

       Phase 1: Data Cleaning & Type Conversion
       - The initial step focused on data integrity to ensure numerical scores could be analyzed correctly.

          1) Missing Value Quantification: Calculated the count and percentage of missing values (NaNs) per column to inform                the imputation strategy.

          2) String Imputation: Handled missing categorical data (e.g., Region, Affiliation) by filling with the Mode (most                 frequent) or the constant string "Unknown".

          3) Critical Type Conversion: The core challenge was addressed by:

          - Using regular expressions (.str.replace()) to remove non-numeric characters (e.g., *, +, non-standard text) from               score columns like QS Overall Score.

          - Converting the cleaned string column to a floating-point numeric type using pd.to_numeric(errors='coerce'), which              explicitly converted any remaining unparseable strings (like "Not Applicable") into $\text{NaN}$s.

          4) Numerical Imputation: Filled the resulting numerical NaN values in score columns using the Median to mitigate                  the influence of potential outliers.


         Phase 2: Numerical Metrics & Z-Score Calculation
          - Using the cleaned numerical data, key descriptive statistics were calculated using NumPy.

          1) Descriptive Statistics: Calculated the Mean, Median, Standard Deviation, Min, and Max for all score-based                      columns.

          2) Data Normalization (Z-Score): Created a new column for the Z-Score of the QS Overall Score using the formula: 
                             Z =    σ
                                  _____
                                   X−μ

             - This metric allows for standardized comparison, identifying how many standard deviations a university's score                  is from the global mean.


           Phase 3: Grouping and Aggregation
           - This phase summarized performance across key categories, providing high-level comparative insights.

          1) Simple Aggregation: Calculated the average QS Overall Score grouped by Region to quickly rank regional                         performance.

          2) Advanced Aggregation (.agg()): Grouped data by Country and calculated multiple metrics simultaneously, such as:

              - QS Overall Score: mean, median, max.

              - University Name: count (to determine institutional presence per country).

          3) Data Structuring: The resulting multi-level aggregated DataFrame was flattened and indexed to create a clean,                  report-ready table.
             

             Phase 4: Exploratory Data Analysis (EDA)
               - The final step involved interpreting the results of the previous phases.

              1) Distribution Analysis: Analyzed the value_counts() and distribution of categorical columns (Country, Region).

              2) Correlation Analysis: Calculated the correlation matrix for all core numeric scores (Teaching Score,                           Research Score, etc.) to identify the strongest predictors of the QS Overall Score.

              3) Outlier Identification: Filtered the DataFrame using the Z-Score column (e.g., universities with ∣Z∣>3) to                      identify institutions with performance levels significantly outside the norm.

              4) Conditional Hypothesis: Filtered data (e.g., Top 10 universities) to test specific hypotheses, such as                        comparing the average Faculty Count of elite universities against the overall population mean.
         


     🚀 How to Run the Project:-
    
       1) Clone the Repository:
           git clone https://github.com/yashraj022381/global-university-rankings-analysis.git
            cd global-university-rankings-analysis

       2) Install Dependencies and Libraries:
           pip install numpy
           pip install pandas
           pip install -r requirements.txt
          
       3) Execute the Analysis:
          Open and run the University_Rankings_Analysis.ipynb notebook in a Jupyter environment.
          
