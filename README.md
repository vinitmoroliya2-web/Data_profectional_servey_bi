Data Professional Survey Analytics 

Tech Stack:Power BI, Power Query, Advanced Excel, DAX, Data Modeling


1. Project Background & Business Case

In the modern tech landscape, attracting and retaining data talent requires precise market intelligence. However, raw human resources and sentiment data are notoriously messy, heavily reliant on free-text survey responses, and difficult to quantify.

This project delivers an end-to-end Business Intelligence solution that transforms raw, unstandardized survey data from 630 international data professionals into an executive-ready dashboard. By engineering a robust data cleaning pipeline and designing an intuitive, self-service UI, this dashboard surfaces critical benchmarks regarding global compensation hierarchies, technology adoption, workforce demographics, and employee sentiment metrics.



2. Advanced Data Engineering Pipeline (Power Query)

To ensure data integrity and analytical accuracy, a Minimum Viable Data Cleaning pipeline was architected within Power Query to handle complex edge cases, text variants, and messy survey inputs:

A. Categorical Normalization & Schema Optimization

Algorithmic Job Title Consolidation: The primary role field (“Which title fits you best”) was flooded with disparate free-text entries. By applying text-transformation scripts and splitting strings via the opening parenthesis delimiter `(`, noisy variations were stripped away, strategically consolidating dozens of disjointed roles into 6 to 7 clean, high-level operational job families.

Tech Stack Isolation:The "Favorite programming language" column contained fragmented text combinations. String manipulation via a colon delimiter `:` successfully isolated core programming languages from non-standard survey noise.


Schema Pruning: Dropped non-essential dimensional attributes to streamline memory usage, optimizing the dashboard's cross-filtering performance.

B. Numeric Transformation & Salary Normalization Pipeline

The original "Current yearly salary" data was captured as non-numeric text ranges (e.g., "106-125K", "225K+"). To unlock mathematical aggregation and statistical analysis, an extraction pipeline was built:

1. String Stripping: Engineered steps to strip alphanumeric characters (`K`, `-`, `+`) to isolate raw numeric lower and upper boundaries.
2. Outlier & Edge-Case Handling: Implemented logical overwrites for open-ended ranges (e.g., transforming "225K+" using its base value) to prevent mathematical distortion in the model.
3. Calculated Column Generation: Generated an accurate Average Salary metric for every respondent using a calculated column workflow:

$$\text{Average Salary} = \frac{\text{Low Salary} + \text{High Salary}}{2}$$
<img width="367" height="280" alt="image" src="https://github.com/user-attachments/assets/e75f8595-adac-4aa0-b4d8-143d84159843" />


3. High-Level Metrics & Core Cohort Demographics

Total Talent Sample Size (n):630 Data Professionals
Average Professional Age: ~30 Years Old (Representing a highly mobile, mid-career talent pool)


4. Key Business Insights & Analytical Deep-Dives

A. Global Compensation Benchmarking

A cross-sectional analysis of average salaries by core data functions exposed a clear financial hierarchy in the market:

| Job Title | Average Salary (USD) | Market Distribution Insight |
| --- | --- | --- |
| **Data Scientist** | **$93,000** | Commands the highest financial premium in the tech sector. |
| **Data Engineer** | **$65,000** | Positioned as a core infrastructure necessity with stable mid-tier pricing. |
| **Data Architect** | **$63,000** | High-level strategic role showcasing specialized data management value. |
| **Data Analyst** | **$55,000** | Represents the absolute majority volume of the talent pool, serving as the market's operational foundation. |
<img width="475" height="280" alt="image" src="https://github.com/user-attachments/assets/1c3c9ad8-9ccb-426c-bfe4-089b2557b101" />


B. Technology Ecosystem Dominance

Analysis of language popularity metrics indicates that Python is the dominant programming language within the data ecosystem. It outpaced competing languages (including JavaScript, Java, C++, and R) by a substantial margin, highlighting its status as an essential skill for modern data teams.

C. Macroeconomic & Geographic Wage Disparities

By utilizing an interactive Treemap, the dashboard dynamically illustrates how local costs of living and regional economic factors drastically skew compensation across geographies, even when normalized to USD:

United States: Data Scientist Avg: $139,000 | Data Analyst Avg: $80,000
India: Data Scientist Avg: $68,000 | Data Analyst Avg: $26,000

D. Qualitative Sentiment & Market Friction Metrics

The Retention Risk Indicator: Utilizing dual KPI gauges (0-10 scale), the data reveals a critical corporate risk. While Work-Life Balance scores a moderate ~5.74, Salary Satisfaction scores significantly lower. This gap signals a widespread market sentiment that compensation has not kept pace with inflation and role responsibilities.
Gender Pay Equity: In this specific global sample, Females commanded a slightly higher average salary (~$55,000) relative to Males (~$53,000).
Market Entry Barriers: A psychologically color-coded Pie Chart demonstrates that incoming professionals perceive breaking into the data space as a highly competitive, friction-heavy process, signaling a tight screening environment for entry-level roles.



5. UI/UX Design & Dashboard Usability

To transition the dashboard from a basic tool to an executive-ready application, specific design guidelines were enforced:
<img width="1112" height="627" alt="image" src="https://github.com/user-attachments/assets/c904813d-5255-4026-83c5-ed9a4cfeac2a" />


Muted Color Psychology:Replaced standard stark white backgrounds with a natural, muted color palette to minimize visual fatigue during long analysis sessions.
Intuitive Layout Hierarchy: Positioned critical KPI cards and titles ("Data Professional Survey Breakdown") on the left and top areas to match natural reading patterns.
Dynamic Cross-Filtering: Enabled full self-service BI capability, allowing HR leaders and hiring managers to click any country in the Treemap or any slice of the Donut chart to instantly filter salaries, languages, and satisfaction scores across the entire canvas.

