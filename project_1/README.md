
# Project 1: An Analysis of SAT & ACT Policy For College Admission
---
### Overview
For this project, I examined the trends in SAT and ACT test-optional policy as part of college or university admission requirement. Test-optional policy implementation duration varies by institutions. The objective for this project is to provide better visibility and directions for necessary requirements for college application processes, whether SAT & ACT should be dropped as an admission requirement.

The SAT has two sections of the test: Evidence-Based Reading and Writing and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). They have different score ranges, which you can read more about on their websites or additional outside sources (a quick Google search will help you understand the scores for each test):
* [SAT](https://collegereadiness.collegeboard.org/sat)
* [ACT](https://www.act.org/content/act/en.html)

Standardized tests have long been a controversial topic for students, administrators, and legislators. Since the 1940's, an increasing number of colleges have been using scores from sudents' performances on tests like the SAT and the ACT as a measure for college readiness and aptitude ([*source*](https://www.minotdailynews.com/news/local-news/2017/04/a-brief-history-of-the-sat-and-act/)). Supporters of these tests argue that these scores can be used as an objective measure to determine college admittance. Opponents of these tests claim that these tests are not accurate measures of students potential or ability and serve as an inequitable barrier to entry. Lately, more and more schools are opting to drop the SAT/ACT requirement for their Fall 2021 applications ([*read more about this here*](https://www.cnn.com/2020/04/14/us/coronavirus-colleges-sat-act-test-trnd/index.html)).

According to Lovell and Mallinson (2022), the COVID-19 pandemic has induced numerous colleges and universities to implement test-optional admission policies. It was implemented out of safety measures during the pandemic. However, pre-pandemic era has seen various colleges and universities practiced this policy as a way to promote diversity and equity on campus. [[source]](https://www.urban.org/research/publication/how-test-optional-college-admissions-expanded-during-covid-19-pandemic) This includes the optional submission for SAT and ACT scores for students university admission. (Bhardwa, 2022) [[source]](https://www.timeshighereducation.com/student/advice/what-does-test-optional-mean-us-university-applications). In addition, the number of universities and colleges with test-optional policies has nearly doubled from 713 to 1,350 since spring 2020. Therefore, many universities are inching towards the test-optional admission requirement as part of the new normal. Also, it could also lead to a more diverse pool of applicants. (Lovell and Mallinson, 2022)


Research has also shown that GPA or grades are the best predictor of college performance and are not as heavily influenced as standardized exams by socioeconomic backgrounds such as income, parent education levels and race. (Kurlaender and Cohen, 2019) [[source]](https://edpolicyinca.org/publications/predicting-college-success-how-do-different-high-school-assessments-measure-2019). To validate the statement, a number of university-admitted student GPAs have been collected and inputted manually to the csv file as attached above. Due to data availability constraint, only student GPAs admitted to University of California campuses were collected to be investigated. [[source]](https://admission.universityofcalifornia.edu/campuses-majors/freshman-admit-data.html). This dataset will be used to understand the correlation between GPA and SAT scores particularly for UC universities.

The data used for this project are from the following sources: 
- [*2019 SAT Scores by Intended College Major*](https://reports.collegeboard.org/pdf/2019-total-group-sat-suite-assessments-annual-report.pdf)
- [*Ranges of Accepted ACT & SAT Student Scores by Colleges*](https://www.compassprep.com/college-profiles/)
- [*Ranges of Accepted Student GPA by all University of California campuses*](https://admission.universityofcalifornia.edu/campuses-majors/freshman-admit-data.html)

---
### Datasets
sat_2019_by_intended_college_major.csv : 2019 SAT Scores by Intended College Major

sat_act_by_college.csv : Ranges of Accepted ACT & SAT Student Scores by Colleges

gpa_by_UC_college.csv :Ranges of Accepted Student GPA by all University of California campuses

 ### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**intended_college_major**|*object*|College Board 2019 SAT Annual Report|Student's intended college majors (total of 38 majors)| 
|**num_sat_takers_int**|*integer*|College Board 2019 SAT Annual Report|Number of test takers corresponding to the intended college major|
|**percent_of_majors_float**|*float64*|College Board 2019 SAT Annual Report|Percent(%) of test takers choosing the intended majors| 
|**total_sat_score**|*integer*|College Board 2019 SAT Annual Report| Mean total SAT score (max 1600) |
|**mean_sat_reading_writing**|*integer*|College Board 2019 SAT Annual Report|Mean reading writing SAT score (max 800).| 
|**mean_sat_math**|*integer*|College Board 2019 SAT Annual Report|Mean math SAT score (max 800)|

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**school**|*object*|Compass Education Group SAT and ACT Policies with Score Ranges|College or university name| 
|**test_optional**|*object*|Compass Education Group SAT and ACT Policies with Score Ranges|Test-optinal policy implementation ( Yes or No)|
|**class_years**|*object*|Compass Education Group SAT and ACT Policies with Score Ranges|Class years that are elligible| 
|**policy_details**|*object*|Compass Education Group SAT and ACT Policies with Score Ranges|Details of test optional policy|
|**number_of_applicants_int**|*integer*|Compass Education Group SAT and ACT Policies with Score Ranges|Number of applicants to each school| 
|**acceptance_rate_float**|*float64*|Compass Education Group SAT and ACT Policies with Score Ranges|Percentage(%) of students who are accepted|
|**sat_total_middle_range**|*object*|Compass Education Group SAT and ACT Policies with Score Ranges|Range of 25th and 75th percentile SAT scores accepted by the school|
|**act_total_middle_range**|*object*|Compass Education Group SAT and ACT Policies with Score Ranges|Range of 25th and 75th percentile ACT scores accepted by the school|
|**policy_check**|*object*|Compass Education Group SAT and ACT Policies with Score Ranges|Policy buddy check if 'test_optional' is correctly inputted based on sentiment)|
|**sat_25th_percentile**|*float64*|Compass Education Group SAT and ACT Policies with Score Ranges|25th percentile of school's accepted SAT scores|
|**sat_75th_percentile**|*float64*|Compass Education Group SAT and ACT Policies with Score Ranges|75th percentile of school's accepted SAT scores|
|**act_25th_percentile**|*float64*|Compass Education Group SAT and ACT Policies with Score Ranges|25th percentile of school's accepted ACT scores)|
|**act_75th_percentile**|*float64*|Compass Education Group SAT and ACT Policies with Score Ranges|75th percentile of school's accepted ACT scores)|

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**school**|*object*|University of California Freshman Admit Data|College or university name| 
|**high_school_gpa_middle_range**|*float64*|University of California Freshman Admit Data|Range of 25th and 75th percentile high school GPA accepted by the school|
|**gpa_25th_percentile**|*float64*|University of California Freshman Admit Data|25th percentile of school's accepted high school GPA|
|**gpa_75th_percentile**|*float64*|University of California Freshman Admit Data|75th percentile of school's accepted high school GPA|

---
 ### Executive Summary
 **1.** **Majority of colleges or universities implement test-optional policy**
- 46% pilot-test the policy on 2021
- 38% has long-term and permanent test-optional policy
- Only 6% has not implemented test-optional policy

Popular schools such as University of California Los Angeles California, University of California San Diego and other University of California campuses have implemented test-optional policy

 **2.** **Both SAT and ACT test scores have inverse relationship to college acceptance rate**

 Notoriously low acceptance rate schools such as Standford University, Harvard College, etc tend to have students with high SAT or ACT scores while high acceptance rate schools such as University of Wyoming and University of Texas El Paso have students with low SAT or ACT scores

**3.** **Both SAT and ACT test scores have positive relationship to high school GPA scores**

Based on popular schools such as University of California Los Angeles, University of California San Diego and other University of California campuses, higher high school GPA students have higher SAT scores, indicating high school GPA as a legit indicator for academic performance

**4.** **SAT scores vary greatly with people from different backgrounds or their intended college major**

Students who wish to study math stats or physical sciences have high SAT scores of 1200 while students who study culinary services or family sciences have low SAT scores oF 930. Most students from culinary services background will not be shortlisted for their dream school if their dream school implements strict SAT rules. Thus, universities will have less pool of diverse talents

---
### Conclusions and Recommendations
It is recommended that both SAT and ACT tests should be optional for a college or university admission process. As high school GPA is positively correlated to SAT scores, high school GPA can be used as a gauge in determining students' academic performance. Although the correlation analysis is done only on University of California campuses, they are still the popular schools that students apply as reflected from their number of test takers. As such, the data is representative to be used to correlate high school GPA to SAT scores. Furthermore, majority of the universities have implemented test-optional policy for their university admission.

While it can be observed that both SAT and ACT scores have negative correlation to acceptance rate, higher high school GPA tend to result in higher SAT scores. Thus, if SAT and ACT are a standardized measure test for academic performance, high school GPA can also be a good metric in which it measures the students' performance of whole academic year rather than depending on a particular test.

There are a number of research done on the reasons why ACT and SAT should be abolished. Reasons are as follows:

- There are social inequities as it is heavily influenced by socioeconomic backgrounds, income and race [[source]](https://edpolicyinca.org/publications/predicting-college-success-how-do-different-high-school-assessments-measure-2019)
- Test preparations have become a multi-billion dollar businesses. Many New York families spend over $$20,000 on SAT prep and top tutors charge over $600 and hour [[source]](https://www.nytimes.com/roomfordebate/2015/03/31/how-to-improve-the-college-admissions-process/colleges-should-get-rid-of-the-sat-and-act-and-abolish-preferences)
- Test anxiety leads to underperformance [[source]](https://digitalcommons.usf.edu/cgi/viewcontent.cgi?referer=https://www.google.com/&httpsredir=1&article=7397&context=etd)
 
Additional data that might be helpful:
- Universities SAT and ACT scores accross different years
- Other statistics that may have affect SAT or ACT scores (income, race, lifestyle, etc)

---
### Sources
- ACT org. (2022). ACT test scores: Understanding your scores. Retrieved from https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html
- Carr, A. (2016). An exploratory study of test anxiety as it relates to the national clinical mental health counseling examination. Retrieved from https://digitalcommons.usf.edu/cgi/viewcontent.cgi?referer=https://www.google.com/&httpsredir=1&article=7397&context=etd
- Hernandez,M. (2015). Colleges should get rid of the SAT and ACT and abolish preferences. Retrieved from https://www.nytimes.com/roomfordebate/2015/03/31/how-to-improve-the-college-admissions-process/colleges-should-get-rid-of-the-sat-and-act-and-abolish-preferences
- Kurlaender,M. and Cohen,K. (2019). Predicting college success. Retrieved from https://edpolicyinca.org/publications/predicting-college-success-how-do-different-high-school-assessments-measure-2019
- Lee, A. (2020). Colleges consider the unthinkable: Dropping SAT and ACT requirements for next year's applicants. Retrieved from https://edition.cnn.com/2020/04/14/us/coronavirus-colleges-sat-act-test-trnd/index.html
- Lovell,D. and Mallionson,D.(2022). How test-optional college admissions expanded during the covid-19 pandemic. Retrieved from https://www.urban.org/research/publication/how-test-optional-college-admissions-expanded-during-covid-19-pandemic
- The Priceton Review. (2022). SAT Sections. Retrieved from https://www.princetonreview.com/college/sat-sections
- University of California Admissions. (2021). Freshman admit data. Retrieved from https://admission.universityofcalifornia.edu/campuses-majors/freshman-admit-data.html