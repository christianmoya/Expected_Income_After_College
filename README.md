# Are Colleges Worth It?
![alt text](https://rmlefcu-blog.org/wp-content/uploads/2018/05/shutterstock_210355270-604x270.jpg)

## Business Understanding  
According to a survey conducted by LendEDU, about 7,000 college students expected a median salary of $60,000 after graduating. 52% of college students take out student loans to attend college, and of that number, 17% have trouble paying for it. This makes us question, is college worth attending? 

I looked at over 900 schools and 10 features for each, testing to see what features lead their graduates to a expected income of $60,000 or more. 

Our <b>null hypothesis</b> claims that features do not have any impact on expected income. 
Our <b>alternate hypothesis</b> claims that features do have an impact on expected income. 

## Data Understanding (College_EDA Notebook) 
Data was taken from PayScale.com, data.world, and US News & Report, offering the following features: 

1. Meaning Percentage (continuous) - how many graduates find their work meaningful?
2. STEM Percentage (continuous) - what percentage of degrees were STEM related (Science, Technology, Engineering, Mathematics) 
3. School Type (categorical) - engineering, private, religious, art, for sports fans, party school, liberal arts, state, research university, business, sober, ivy league
4. State (categorical) 
5. Type (categorical) - private, public, or for-profit 
6. Degree Length (categorical) - 2 year, 4 year 
7. Tuition (continuous) - includes in-state, out-of-state, and room-and-board
8. Total Enrollment (continuous) - how many students are enrolled in the school?
I took a look at 1,500 colleges around the U.S. and its expected salary to determine which schools have an expected early career income of $60,000 or more, and what features contribute to that. With that, I build a logistic regression model that predicts whether a college will over $60,000 or more upon graduation, with the hope that it can offer high school seniors or college transfers insight on if a potential college is worth attending or not. 
9. Diversity Enrollment (continuous) - what's enrollment like for minority groups (Asian, Black, Hispanic, Native Hawaiian/ Pacific Islander, Native American/ Alaskan Native, women, and non-residents) 
10. School Rank (categorical) - We binned rank by Top 50, Top 100, Top 150, Top 200, Top 250, and Over 250

Below, we find a count of the types of schools in our DataFrame. 

![alt text](https://github.com/christianmoya/Expected_Income_After_College/blob/main/school_types_bar_graph.png)

<b>PayScale</b> offered data on expected income for early career and mid-career, the percentage of alumni that found their work meaningful, and the percentage of degrees awarded related to science, technology, engineering and math. School type was all in one list, so we spent some time creating a new columns consisting of booleans, indicating whether a college fell under a certain school type of not. 

<b>Data.World</b> offered additional data on enrollment of minority groups, tuition costs. I had to pivot the DataFrame in order to calculate the enrollment percentages for each minority group. 

<b>US News & Reports</b> offered school rankings. Because not all schools fell on the list, we had to bin the schools into groups of 50, and signify if a school was not in the top 250 list. 

For our target, we find that only about 10% of schools actually have an expected income of $60,000 or more. <i>Additional distributions for our features can be found in the Colleges_EDA notebook.</i>

![alt text](https://github.com/christianmoya/Expected_Income_After_College/blob/main/Target_hist.png)

## Data Preparation (College_Data_Preparation_and_Model) 
Because data came from multiple sources, a number of colleges varied in the spelling of their name (eg. Columbia University vs. Columbia College in the City of New York). This meant that DataFrames did not merge as smoothly as I'd hope, hence missing values in some columns. In the notebook, we actually deal with null values two different ways to test which might have a better recall score. 

## Model (College_Data_Preparation_and_Model) 
Because my predictive target is binary, I chose to go with a LogisticRegression model using Scikit Learn. After toying with test size and class weights, I moved over to a LogisticRegression model using statsmodels. Doing so allowed me to find the coefficients for each feature and narrow down the features based on p-value. 

## Evaluate (College_Data_Preparation_and_Model) 
Baseline model had an AUC score of .796, an accuracy score of 91%, and a recall score of 22%. This is problematic, because recall is more important, given we would want to classify false if they are false. It would just be sad if a student went to a school, thinking they're supposed to make $60,000, but they don't. It would be a surprise and delight if someone went to  a school, thinking it didn't classify with an expected income of $60,000, but it actually is. 

After multiple iterations. We have an AUC score of .929, an accuracy score of 95.3% and a recall score of 72.0%. 

## Conclusion and Recommendations

![alt text](https://github.com/christianmoya/Expected_Income_After_College/blob/main/feature_impact.png)<\n>

Based on our model, we found the features with the most impact on expected early career salary were non-resident enrollment, school rank (top 50 and top 100), engineering school, liberal arts, and for sports fans. Research universities had a negative impact on our value. With that, we would recommend that students, no matter what school they go to, do the following: 
1. Gain a global perspective: learn from people that have different experiences than you. 
2. Join a sport, and gain some school spirit. That can really build your network. 
