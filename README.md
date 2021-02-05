# Package-Pricing-At-Mission-Hospital
Built Predictive Model to estimate the price of treatment given the clinical factors at the time of admission.

### TABLE OF CONTENTS
* [Objective](#objective)
* [Conceptual Model](#conceptual_model)
* [Variable Selection](#variable_selection)
* [Data Exploration](#data_exploration)
* [Logistic Regression Model](#logistic_regression_model)
* [Results](#results)

## OBJECTIVE

Estimate the price of treatment given the clinical factors at the time of admission

## CONCEPTUAL MODEL 

![GitHub Logo](https://github.com/skotak2/Package-Pricing-At-Mission-Hospital/blob/main/Images/Conceptual_Model.JPG)

## Data Preparation

### Removed the following columns with insufficient observations as "1"

* CAD SVD
* CAD VSD
* Other general
* Confused state

### Numerical values were bucketed and One hot encoded for the following variables,

* Age Categories - <10, 11 25, 26 50, 50 and above (as per domain expertise)
* BP Ranges - Low, Normal, High, Critical (as per the medical charts)
* BMI - Underweight, Normal, Overweight, Obese (as per the medical charts)
• Hemoglobin "normal": Female 12 to 15.5, Men 13 to 17.5, any value outside these limits will be "abnormal"
• Urea "normal": 7 to 20 mg/dl any value outside these limits will be "abrnormal"

### Removing Variables based on avalability of data

• Removed Stay at hospital ICU and Ward.It is a reflective construct variable. Cannot predict length of stay accurately at the time of admission to compute total treatment cost.


• Considered ln(Total Cost) instead of Total Cost to Hospital(INR). Our variable has a right skew. Taking the log would make the distribution of our transformed variable appear more symmetric.

### Handling NULL Values

* BP Ranges Imputed 'Normal' BP range for null values which were Juvenile Patients
* Urea Imputed 'Normal' Urea level for 11 null values. Assumption: Urea measurement is not critical for that patient.

## Statistical Tests

T-Test and Anova was performed on specific variable to understand their effect on target variable. Code is available [here](https://github.com/skotak2/Package-Pricing-At-Mission-Hospital/blob/main/Code/Ttest_Anova.R)

T test was performed on variables with 2 categories. The following variables were removed as they proved insignificant,

• other-heart
• other-nervous
• other-tetralogy
• Diabetes
• Hypertension
• Hemoglobin

ANOVA test was done to test for variables with more than two levels and the following variables proved significant,

• Age 
• BMI
• BP Ranges












