# Task 28: Outlier Detection

## Overview
This project demonstrates basic outlier detection techniques in Python using data visualization (box plots) and mathematical analysis (Interquartile Range - IQR). The objective is to identify potential anomalies within a dataset without automatically removing valid extreme data points.

---

## Tools Used
* **Python**
* **Pandas** (Data Manipulation)
* **Matplotlib** (Data Visualization)
* **Jupyter Notebook**

---

## Dataset Description
A synthetic **Employee Salary Dataset** containing 54 employee records was generated. It consists of a standard normal distribution of salaries centered around $70,000, along with introduced extreme high and low salary values.

---

## Analysis & Findings

### 1. Interquartile Range (IQR) Calculation
Using the standard IQR outlier threshold formula:
$$\text{Lower Bound} = Q_1 - 1.5 \times \text{IQR}$$
$$\text{Upper Bound} = Q_3 + 1.5 \times \text{IQR}$$

* **First Quartile ($Q_1$):** $60,133.71
* **Third Quartile ($Q_3$):** $73,676.78
* **Interquartile Range ($\text{IQR}$):** $13,543.07
* **Lower Bound:** $39,819.09
* **Upper Bound:** $93,991.39

### 2. Identified Potential Outliers
Data points falling outside the interval $[39819.09, 93991.39]$ were flagged as outliers:

| Index | Employee_ID | Salary ($) | Reason |
|---|---|---|---|
| 50 | 51 | 18,000.00 | Below Lower Bound |
| 51 | 52 | 22,000.00 | Below Lower Bound |
| 52 | 53 | 160,000.00 | Above Upper Bound |
| 53 | 54 | 175,000.00 | Above Upper Bound |

---

## Data Visualization

Below is the box plot representing the distribution of employee salaries and highlighting the four detected outliers as individual circles.

<!-- PLACEHOLDER FOR SCREENSHOT -->
![Box Plot of Employee Salaries](Screenshot%202026-11-06%20171006.png)

---

## Summary of Findings
1. The majority of employee salaries fall cleanly within the $60,000 to $74,000 range.
2. Four extreme data points were detected: two lower outliers ($18,000 and $22,000) and two upper outliers ($160,000 and $175,000).
3. Outliers represent actionable insights in real-world scenarios—lower values could correspond to part-time/stipend roles, while upper values represent executive salaries.

---

## Interview Questions & Answers

### Q1: What is an outlier?
**Answer:**  
An outlier is a data point that differs significantly from other observations in a dataset. Outliers can occur due to experimental errors, data entry mistakes, or true natural variations within the underlying population (e.g., high-income earners or rare fraud instances).

### Q2: How can a box plot help identify outliers?
**Answer:**  
A box plot visually summarizes a dataset using a five-number summary (Minimum, $Q_1$, Median, $Q_3$, Maximum). The "box" contains the middle 50% of the data ($\text{IQR}$). Whiskers extend up to $1.5 \times \text{IQR}$ from the hinges. Any data points lying beyond the whiskers are plotted individually as points or circles, making potential outliers easily recognizable at a glance.

### Q3: Should every outlier be removed?
**Answer:**  
No, outliers should **never** be automatically removed without investigation. While erroneous outliers (such as data entry errors) should be cleaned or dropped, valid outliers often contain critical domain insights (e.g., financial fraud, executive pay, network attack spikes). Removing valid extreme data can introduce sampling bias and distort predictive models.
