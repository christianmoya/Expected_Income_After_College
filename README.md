# Are Colleges Worth It?

## Business Understanding  
According to a survey conducted by LendEDU, about 7,000 college students expected a median salary of $60,000 after graduating. 52% of college students take out student loans to attend college, and of that number, 17% have trouble paying for it. This makes us question, is college worth attending? 

I looked at over 900 schools and 10 features for each, testing to see what features lead their graduates to a expected income of $60,000 or more. 

Our <b>null hypothesis</b> claims that features do not have any impact on expected income. 
Our <b>alternate hypothesis</b> claims that features do have an impact on expected income. 

## Data Understanding 
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

<b>PayScale</b> offered data on expected income for early career and mid-career, the percentage of alumni that found their work meaningful, and the percentage of degrees awarded related to science, technology, engineering and math. School type was all in one list, so we spent some time creating a new columns consisting of booleans, indicating whether a college fell under a certain school type of not. 

<b>Data.World</b> offered additional data on enrollment of minority groups, tuition costs. I had to pivot the DataFrame in order to calculate the enrollment percentages for each minority group. 

<b>US News & Reports</b> offered school rankings. Because not all schools fell on the list, we had to bin the schools into groups of 50, and signify if a school was not in the top 250 list. 



For our target, we find that only about 10% of schools actually have an expected income of $60,000 or more. <i>Additional distributions for our features can be found in the Colleges_EDA notebook.</i>
