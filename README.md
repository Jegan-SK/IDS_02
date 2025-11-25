# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.


STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
        
        <<INCLUDE YOUR CODING AND OUTPUT SCREENSHOTS>>
        
    import numpy as np
    import pandas as pd
    import matplotlib.pyplot as plt
    import seaborn as sns
    data=pd.read_csv("titanic_dataset.csv")
    df=pd.DataFrame(data)
    df
    
<img width="1322" height="448" alt="image" src="https://github.com/user-attachments/assets/0c40c019-497e-4243-821f-900500545185" />

    sns.heatmap(df.isnull())

<img width="877" height="647" alt="image" src="https://github.com/user-attachments/assets/f42b9f53-e5c5-4cf5-9289-87598b3820ba" />

    df.isnull().sum()

<img width="468" height="286" alt="image" src="https://github.com/user-attachments/assets/31786485-01da-4369-823b-b0b04936dfb1" />

    # Use mean for numeric and mode for categorical values 
    for column in data.columns: 
        if df[column].dtype == 'object': 
            df[column] = df[column].fillna(df[column].mode()[0])  # Fill with mode 
        else: 
            df[column] = df[column].fillna(df[column].mean())  # Fill with mean 
 
    print(" Missing values handled.")
    df

<img width="1347" height="597" alt="image" src="https://github.com/user-attachments/assets/05ddb4ad-8ce2-4d3e-bbcd-1b4d6b3f6e55" />

    sns.boxplot(x=df['Age']) 
    plt.title("Boxplot - Salary") 
    plt.xlabel("Salary") 
    plt.show()

<img width="825" height="575" alt="image" src="https://github.com/user-attachments/assets/964b074b-08ce-4e4f-aa5a-054ae788d086" />

    def remove_outliers_iqr(df, column): 
    Q1 = df[column].quantile(0.25) 
    Q3 = df[column].quantile(0.75) 
    IQR = Q3 - Q1 
    lower = Q1 - 1.5 * IQR 
    upper = Q3 + 1.5 * IQR 
    return df[(df[column] >= lower) & (df[column] <= upper)] 
    # Apply IQR method on 'Age' 
    data = remove_outliers_iqr(df, 'Age') 
    print("Outliers removed using IQR method.")

<img width="1336" height="603" alt="image" src="https://github.com/user-attachments/assets/915c4cb9-eb3a-499c-a0ca-193acf8c1aa2" />

    sns.countplot(x='Embarked', data=df) 
    plt.title("Countplot - Embarked Distribution") 
    plt.show()

<img width="887" height="576" alt="image" src="https://github.com/user-attachments/assets/e1c405fc-2984-43ad-86da-c00147faa8f7" />

    sns.displot(data['Age'], kde=True)
    plt.title("Displot - Age Distribution")
    plt.xlabel("Age") 
    plt.ylabel("Frequency") 
    plt.show() 

<img width="1046" height="642" alt="image" src="https://github.com/user-attachments/assets/4ca95e81-358b-4f99-beb9-2d4b784e10fc" />

    crosstab_result = pd.crosstab(df['Pclass'], df['Sex']) 
    print("\nCross Tabulation Result:") 
    print(crosstab_result) 
    
<img width="669" height="154" alt="Screenshot 2025-11-25 134540" src="https://github.com/user-attachments/assets/82c745c0-08ec-4909-be1b-83e16db4cf86" />


    correlation_matrix = data.corr() 
    sns.heatmap(correlation_matrix, annot=True ) 
    plt.title("Correlation Heatmap") 
    plt.show()

<img width="1133" height="632" alt="image" src="https://github.com/user-attachments/assets/95aff9b0-757b-4099-899b-eb4a920b7f01" />

# RESULT:

Thus the program to implement the exploratory data analysis has been successfully completed. 
