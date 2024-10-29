# Active Product Sales Analysis Python Project
This project provides an insightful analysis of sales activity, focusing on transaction patterns across different hours of the day. Through data manipulation and visualization, this analysis identifies peak sales hours, aiding strategic decision-making for business promotions.

This project uses Python’s data analysis libraries to perform a structured exploration of transactional data, delivering data-driven insights. It includes steps from data preprocessing and time-based analysis to visualizations that can help shape sales strategies.

**Table of Contents**

* Installation
* Dataset Overview
* Project Workflow
* Data Visualization
* Insights and Conclusion

**Installation**

To initiate the project first install the following Python packages:

      numpy
      pandas
      matplotlib

Install them using:

      pip install numpy pandas matplotlib

**Dataset Overview**

The dataset, **Order_details-masked.csv**, contains transaction records, including transaction dates. The primary focus here is to analyze the frequency of transactions occurring at different hours of the day, using Python for data preprocessing and visualization.

**Project Workflow**

**1. Data Preparation**

* Import the necessary libraries:**numpy**, **pandas**, and **matplotlib**.
* Load the dataset into a pandas DataFrame to make it easier to process and analyze.

      import numpy as np
      import pandas as pd
      import matplotlib.pyplot as plt

      Order_Details = pd.read_csv(r"path_to_file/Order_details-masked.csv")
      Order_Details.head()

**2. Time Column Creation**

* Convert the **Transaction Date** column into DateTime format and extract the hour for each transaction.
* This helps identify the specific time of day each transaction took place, aiding in hour-based analysis.

      Order_Details['Time'] = pd.to_datetime(Order_Details['Transaction Date'])
      Order_Details['Hour'] = Order_Details['Time'].dt.hour

**3. Finding the Busiest Hours**

* Use value counts to calculate the frequency of transactions per hour, allowing us to identify peak sales hours.
* For illustration purposes, we select the top 24 hours based on transaction frequency.

      timemost1 = Order_Details['Hour'].value_counts().index.tolist()[:24] 
      timemost2 = Order_Details['Hour'].value_counts().values.tolist()[:24]

**4. Combining Hourly Data**

* Stack the hour indices and transaction frequencies into a structured format for analysis and display.

      tmost = np.column_stack((timemost1, timemost2))
      print(" Hour Of Day" + "\t" + "Cumulative Number of Purchases \n")
      print('\n'.join('\t\t'.join(map(str, row)) for row in tmost))

**5. Data Visualization**

* Visualize the transaction frequency per hour to understand sales trends.
* A line plot shows the number of transactions for each hour, which can provide valuable insights into peak times for sales.

      plt.figure(figsize=(20, 10))
      plt.title('Sales Happening Per Hour (Spread Throughout The Week)',
                fontdict={'fontname': 'monospace', 'fontsize': 30}, y=1.05)
      plt.ylabel("Number Of Purchases Made", fontsize=18, labelpad=20)
      plt.xlabel("Hour", fontsize=18, labelpad=20)
      plt.plot(timemost1, timemost2, color='m')
      plt.grid()
      plt.show()

![image](https://github.com/user-attachments/assets/b55cacce-7d5c-4ed5-bfc8-d682e6d9a44e)

**Insights and Conclusion**

The analysis indicates a clear trend in sales activity, with late evening hours showing a noticeable peak in purchases. This data insight could guide business strategies, such as timing product promotions during high-activity periods. By leveraging these results, businesses can better align their marketing and operational efforts with customer behavior patterns.

This project demonstrates how data-driven analysis can unlock actionable insights from transaction data, providing an excellent foundation for further exploration of customer habits and preferences.



