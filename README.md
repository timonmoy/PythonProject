

import pandas as pd
import numpy as np
missing_values = ['na','s']

df = pd.read_csv('https://raw.githubusercontent.com/CunyLaguardiaDataAnalytics/datasets/master/2014-15_To_2016-17_School-_Level_NYC_Regents_Report_For_All_Variables.csv', na_values = missing_values)

school_2015 = df[((df['School Name']=='James Madison High School')) & (df['Year']==2015)]
school_2015 = school_2015[['School Name','Year','Total Tested','Regents Exam','Number Scoring Below 65','Number Scoring 65 or Above']]
school_2015.drop_duplicates(keep='first',inplace=True)

#Filter for James Madison High School for Total Test Taken
school_2015.groupby(['School Name'])['Total Tested'].sum().plot(kind='bar').set_title('Year 2015 Total Test Taken')

#Filter for James Madison High School for total of each Subject
school_2015.groupby(['School Name','Regents Exam'])['Total Tested'].sum().plot(kind='bar').set_title('Total Regent Subjects for Year 2015 Taken')

#Filter for James Madison High School for each Subject with Test Scores Below 65
school_2015.groupby(['School Name','Regents Exam'])['Number Scoring Below 65'].sum().plot(kind='bar').set_title('Year 2015 People Score Below 65')

#Filter for James Madsion High School for each Subject with Test Scores Above 65
school_2015.groupby(['School Name','Regents Exam'])['Number Scoring 65 or Above'].sum().plot(kind='bar').set_title('Year 2015 People Score Above 65')


#Test Variables
#school_2015
