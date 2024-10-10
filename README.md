# Financial-Data-Analysis-of-Merged-Companies
Financial Data Analysis of Merged Companies
1. Introduction
The primary goal of this project is to analyze a dataset of merged company financial data. The analysis aims to identify key trends, relationships, and patterns among different companies in terms of their revenue, dividend yield, earnings, and market capitalization. Using visualizations like line charts, pie charts, donut charts, stacked bar charts, and bubble charts, we explore these financial metrics in detail.

2. Data Understanding
We started with a dataset consisting of several important financial metrics for various companies, such as:

Revenue (TTM)
Earnings (TTM)
Market Capitalization
Dividend Yield (TTM)
P/E Ratio
After loading the dataset, we needed to explore the columns and clean any inconsistencies, including handling missing data and checking for columns that might be named differently.

Challenges Encountered:
Column Name Mismatch: Initially, we expected columns like marketcap, earnings_ttm, and pe_ratio_ttm, but they were not present or named differently. We adjusted the analysis by excluding these columns and using alternatives like revenue_ttm and dividend_yield_ttm.
3. Key Questions Explored
Q1: What is the distribution of revenue across companies?
We started by analyzing the Revenue (TTM) of various companies using a line chart. This helped in understanding the spread of revenue among companies, identifying top performers.

python
Kopiera kod
sorted_data = merged_data.dropna(subset=['revenue_ttm'])
plt.plot(sorted_data['Name'], sorted_data['revenue_ttm'], marker='o', linestyle='-', color='b')
plt.title('Revenue by Company')
Q2: How is revenue distributed across different countries?
A pie chart was used to visualize the total revenue distribution across countries. We grouped the data by country and summed the revenue for each country to get a holistic view of the financial influence of companies in different regions.

python
Kopiera kod
revenue_by_country = merged_data.groupby('country')['revenue_ttm'].sum()
plt.pie(revenue_by_country, labels=revenue_by_country.index, autopct='%1.1f%%')
Q3: Which companies contribute the most to the total revenue?
To identify the top contributors to overall revenue, we created a donut chart for the top 5 companies by revenue. This visualization helped focus on the key players in the market.

python
Kopiera kod
top_5_revenue = merged_data.nlargest(5, 'revenue_ttm')
plt.pie(top_5_revenue['revenue_ttm'], labels=top_5_revenue['Name'], autopct='%1.1f%%')
Q4: How do companies compare in terms of dividend yield?
To explore the dividend yield, a stacked bar chart was created. This helped to compare the dividend yield of companies side-by-side.

python
Kopiera kod
merged_data_clean = merged_data.dropna(subset=['dividend_yield_ttm'])
plt.bar(merged_data_clean['Name'], merged_data_clean['dividend_yield_ttm'], label='Dividend Yield')
Q5: What is the relationship between revenue and dividend yield?
Finally, a bubble chart was used to explore the relationship between revenue and dividend yield, with bubble size representing the revenue. This provided an intuitive way to see which companies had a higher revenue and how that compared to their dividend yield.

python
Kopiera kod
plt.scatter(merged_data['revenue_ttm'], merged_data['dividend_yield_ttm'], s=merged_data['revenue_ttm'] / 1e9)
4. Data Visualization Techniques
The following visualizations were employed:

Line Chart: For exploring trends and distributions of revenue across companies.
Pie Chart: For visualizing the total revenue distribution by country.
Donut Chart: For highlighting the top 5 companies contributing to total revenue.
Stacked Bar Chart: For comparing dividend yields across companies.
Bubble Chart: For analyzing the relationship between revenue and dividend yield, with revenue influencing the bubble size.
5. Insights Gathered
Revenue Dominance: Certain companies emerged as dominant players in terms of revenue, contributing significantly to the total.
Geographic Revenue Distribution: The pie chart revealed that some countries hosted a majority of revenue-heavy companies, influencing global financial markets.
Top 5 Contributors: The top 5 companies contributed a substantial portion of the overall revenue, underscoring their market power.
Dividend Yield Comparison: The stacked bar chart helped in identifying companies with particularly high or low dividend yields, which could interest investors focused on dividend income.
Revenue-Dividend Relationship: The bubble chart showed a weak or strong correlation between revenue size and dividend yield, offering insights into how companies manage profits and shareholder returns.
6. Challenges and Adaptations
Several columns were not available or named differently in the dataset, such as marketcap, pe_ratio_ttm, and earnings_ttm. We adapted by excluding these and focusing on columns like revenue_ttm and dividend_yield_ttm, adjusting the analysis to maintain relevance.

7. Conclusion
This analysis provided key insights into the financial landscape of various companies, from revenue distributions to dividend yields. The visualizations offered an intuitive understanding of the data, and the challenges we faced were resolved through adjustments in data exploration and visualization techniques. Despite some missing or unavailable columns, we derived meaningful interpretations from the data.

