## SuperStore Individual Project

<img src="superstore_logo.png" title="superstore_logo" width="800" height="200" />

<hr style="border-top: 10px groove blueviolet; margin-top: 1px; margin-bottom: 1px"></hr>


# Project Summary
<hr style="border-top: 10px groove blueviolet; margin-top: 1px; margin-bottom: 1px"></hr>
Using a SuperStore dataset acquired through Kaggle.com, I built an OLS regression model that beat the baseline model in predicting Profit. My initial hypothesis that each City’s profit was independent of Texas Mean Profit, could not be tested as the dataset of each City was relatively small. Instead I tested by Category, Sub-Category, and Segment, and found that overall SuperStore is losing money in Texas, with Office Supplies consisting of 61% of sales. A T-test suggested there is no difference between profit generated from office supplies and the Texas Mean Profit.

## Project Goals
> - Find drivers for Profit using SuperStore data available in Texas.
> - Construct an ML Regression model that beats the baseline in predicting Profit.
> - Determine weak areas

## Executive Summary
> - Top Drivers were Category, Sub-Category, and Segment
> - The OLS Regression model beat our baseline in predicting Profit with an RMSE of 85.98 compared to the baseline RMSE of 259.47.
> - Overall Texas is losing money with Office Supplies consisting of 61% of sales. There is no difference between office supplies profit and Texas Mean Profit

#### Audience
> - SuperStore Data Science Team

#### Project Deliverables
> - A final report jupyter notebook 
> - All necessary modules to make my project reproducible
> - Github repository containing all my work
> - README file

#### Project Context
> - The SuperStore dataset I am using can be downloaded from https://www.kaggle.com/itssuru/super-store by signing in with a Kaggle account.


#### Data Dictionary

|Target|Datatype|Definition|
|:-------|:--------|:----------|
| Profit | float64 | Profit made through purchase of item(s) |

|Feature|Datatype|Definition|
|:-------|:--------|:----------|

 |  Ship Mode  |985 non-null   object | Mode of Shipping |
 |:-------|:--------|:----------|
 |   Segment                  |985 non-null    object   | Segment that made the purchase |
 |   Country                  |985 non-null    object   | Country where purchase was made|
 |   City                     |985 non-null    object   | City where purchase was made |
 |   State                    |985 non-null    object   | State where purchase was made |
 |   Postal Code              |985 non-null    int64    | Postal code where purchase was made |
 |   Region                   |985 non-null    object   | Region where purchase was made |
 |   Category                 |985 non-null    object   | Technology, Office Suplies, or Furnishings |
 |   Sub-Category             |985 non-null    object   | Items withing each Category |
 |   Sales                    |985 non-null    float64  | Cost * Quantity |
 |  Quantity                  |985 non-null    int64    | Number of Items sold |
 |  Discount                  |985 non-null    float64  | Percentage of cost removed |
 |  Profit                    |985 non-null    float64  | Money made by SuperStore from purchase |
 |  Category_Office Supplies  |985 non-null    uint8    | Whether an item falls within Office Supplies Category |
 |  Category_Technology       |985 non-null    uint8    | Whether an item falls within Technology Category | 
 |  Sub-Category_Accessories  |985 non-null    uint8    | Whether an item falls within Accessories Sub-Category |
 |  Sub-Category_Appliances   |985 non-null    uint8    | Whether an item falls within Appliances Sub-Category |
 |  Sub-Category_Art          |985 non-null    uint8    | Whether an item falls within Art Sub-Category |
 |  Sub-Category_Binders      |985 non-null    uint8    | Whether an item falls within Binders Sub-Category |
 |  Sub-Category_Bookcases    |985 non-null    uint8    | Whether an item falls within Bookcases Sub-Category |
 |  Sub-Category_Chairs       |985 non-null    uint8    | Whether an item falls within Chairs Sub-Category |
 |  Sub-Category_Copiers      |985 non-null    uint8    | Whether an item falls within Copiers Sub-Category |
 |  Sub-Category_Envelopes    |985 non-null    uint8    | Whether an item falls within Envelopes Sub-Category |
 |  Sub-Category_Fasteners    |985 non-null    uint8    | Whether an item falls within Fasteners Sub-Category |
 |  Sub-Category_Furnishings  |985 non-null    uint8    | Whether an item falls within Furnishings Sub-Category |
 |  Sub-Category_Labels       |985 non-null    uint8    | Whether an item falls within Labels Sub-Category |
 |  Sub-Category_Machines     |985 non-null    uint8    | Whether an item falls within Machines Sub-Category |
 |  Sub-Category_Paper        |985 non-null    uint8    | Whether an item falls within Paper Sub-Category |
 |  Sub-Category_Phones       |985 non-null    uint8    | Whether an item falls within Phones Sub-Category |
 |  Sub-Category_Storage      |985 non-null    uint8    | Whether an item falls within Storage Sub-Category |
 |  Sub-Category_Supplies     |985 non-null    uint8    | Whether an item falls within Supplies Sub-Category |
 |  Sub-Category_Tables       |985 non-null    uint8    | Whether an item falls within Tables Sub-Category |
 |  Segment_Consumer          |985 non-null    uint8    | Whether a buyer is from the Consumer segment |
 |  Segment_Corporate         |985 non-null    uint8    | Whether a buyer is from the Corporate segment |
 |  Segment_Home Office       |985 non-null    uint8    | Whether a buyer is from the Home Office segment |
 



#### Initial Hypotheses & Outcomes

> - **Hypothesis 1 -** Tech Cat Profit vs Texas Mean Profit
> - alpha = .05
> - $H_0$: There is no difference between Tehnology Category Profit and Texas Mean Profit.  
> - $H_a$: There is a difference between Technology Category Profit and Texas Mean Profit. 
> - Outcome: I rejected the Null Hypothesis; Therefore we reject that there is no difference between Technology Category Profit and Texas Mean Profit.

> - **Hypothesis 2 -** Office Cat Profit vs Texas Mean Profit
> - alpha = .05
> - $H_0$: There is no difference between "Office Supplies" Category Profit and Texas Mean Profit.  
> - $H_a$: There is a difference between "Office Supplies" Category Profit and Texas Mean Profit. 
> - Outcome: I fail to reject the Null Hypothesis; Therefore we fail to reject that there is no difference between "Office Supplies" Category Profit and Texas Mean Profit.


<hr style="border-top: 10px groove blueviolet; margin-top: 1px; margin-bottom: 1px"></hr>


### Pipeline Stages Breakdown

<hr style="border-top: 10px groove blueviolet; margin-top: 1px; margin-bottom: 1px"></hr>

##### Plan
- [x] Create README.md with data dictionary, project and business goals, come up with initial questions.
- [x] Acquire data from the Kaggle Database.
- [x] Clean and prepare data for the first iteration through the pipeline, MVP preparation. Create a function to automate the process, store the function in a wrangle.py module, and prepare data by importing and using the function.
- [x]  Clearly define hypotheses, set an alpha, run the statistical tests needed, reject or fail to reject the Null Hypothesis, and document findings and takeaways.
- [x] Establish a baseline and document well.
- [x] Train at least three different regression models.
- [x] Evaluate models on train and validate datasets.
- [x] Choose the model that performs the best and evaluate that single model on the test dataset.
- [x] Document conclusions, takeaways, and next steps. 

___

##### Plan -> Acquire
> - Acquire data from Kaggle Database by signing in. 
> - Plot distributions of individual variables.
___

##### Plan -> Acquire -> Prepare
> - Store functions needed to prepare the SuperStore data; make sure the module contains the necessary imports to run the code. The final function should do the following:
    - Split the data into train/validate/test.
    - Handle any missing values.
    - Handle erroneous data
    - Encode variables as needed.
    - Create any new features, if made for this project.
___

##### Plan -> Acquire -> Prepare -> Explore
> - Answer key questions, my hypotheses, and figure out the features that can be used in a regression model to best predict the target variable, Profit. 
> - Run at least 2 statistical tests in data exploration. Document my hypotheses, set an alpha before running the tests, and document the findings well.
> - Create visualizations and run statistical tests that work toward discovering variable relationships. The goal is to identify features that are related to Profit (the target), identify any data integrity issues, and understand 'how the data works'. If there appears to be some sort of interaction or correlation, assume there is no causal relationship and brainstorm (and document) ideas on reasons there could be correlation.
> - Summarize my conclusions, provide clear answers to my specific questions, and summarize any takeaways/action plan from the work above.
___

##### Plan -> Acquire -> Prepare -> Explore -> Model
> - Establish a baseline to determine if having a model is better than no model and train and compare at least 3 different models. Document these steps well.
> - Train (fit, transform, evaluate) multiple models, varying the algorithm and/or hyperparameters you use.
> - Compare evaluation metrics across all the models you train and select the ones you want to evaluate using your validate dataframe.
> - Feature Selection (after initial iteration through pipeline): Are there any variables that seem to provide limited to no additional information? If so, remove them.
> - Based on the evaluation of the models using the train and validate datasets, choose the best model to try with the test data, once.
> - Test the final model on the out-of-sample data (the testing dataset), summarize the performance, interpret and document the results.
___

##### Plan -> Acquire -> Prepare -> Explore -> Model -> Deliver
> - Summarize my findings through an Executive Summary.
> - Provide a neat and clear final notebook
> - Provide a README.md file

<hr style="border-top: 10px groove blueviolet; margin-top: 1px; margin-bottom: 1px"></hr>

### Reproduce My Project

<hr style="border-top: 10px groove blueviolet; margin-top: 1px; margin-bottom: 1px"></hr>

You will need your own kaggle account to download the data from the following link: https://www.kaggle.com/itssuru/super-store

You will also need to do the following:
- [x] Read this README.md
- [x] Download the wrangle.py and superstore_logo.png files into your working directory
- [x] Run the SuperStore_Individual_Project.ipynb notebook

