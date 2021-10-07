### PROJECT ON OLYMPIC 2021 TOKYO

In this project, we'll work with a dataset containing the names and countries of all those who participated in the Olympic games that was hosted in Tokyo Japan, including all categories of disciplines.

The objective of this project is to establish the most popular discipline among the olympic participants, and the country that had the highest representation in the 2021 Olympic games .



#### Importing the relevant libraries for data wrangling and analysis. 


```python
#Import pandas and matplotlib libraries
import pandas as pd
import matplotlib.pyplot as plt
```


```python
# Reading the excel file into a pandas DataFrame, 
# and assigning it to a variable called olympic_2021.
olympic_2021 = pd.read_excel('Athletes.xlsx')
olympic_2021
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>NOC</th>
      <th>Discipline</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AALERUD Katrine</td>
      <td>Norway</td>
      <td>Cycling Road</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ABAD Nestor</td>
      <td>Spain</td>
      <td>Artistic Gymnastics</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ABAGNALE Giovanni</td>
      <td>Italy</td>
      <td>Rowing</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ABALDE Alberto</td>
      <td>Spain</td>
      <td>Basketball</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ABALDE Tamara</td>
      <td>Spain</td>
      <td>Basketball</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>11080</th>
      <td>ZWICKER Martin Detlef</td>
      <td>Germany</td>
      <td>Hockey</td>
    </tr>
    <tr>
      <th>11081</th>
      <td>ZWOLINSKA Klaudia</td>
      <td>Poland</td>
      <td>Canoe Slalom</td>
    </tr>
    <tr>
      <th>11082</th>
      <td>ZYKOVA Yulia</td>
      <td>ROC</td>
      <td>Shooting</td>
    </tr>
    <tr>
      <th>11083</th>
      <td>ZYUZINA Ekaterina</td>
      <td>ROC</td>
      <td>Sailing</td>
    </tr>
    <tr>
      <th>11084</th>
      <td>ZYZANSKA Sylwia</td>
      <td>Poland</td>
      <td>Archery</td>
    </tr>
  </tbody>
</table>
<p>11085 rows × 3 columns</p>
</div>



### Data Exploration


```python
olympic_2021.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 11085 entries, 0 to 11084
    Data columns (total 3 columns):
     #   Column      Non-Null Count  Dtype 
    ---  ------      --------------  ----- 
     0   Name        11085 non-null  object
     1   NOC         11085 non-null  object
     2   Discipline  11085 non-null  object
    dtypes: object(3)
    memory usage: 259.9+ KB


From the above exploration, its established that the dataset has no missing values, and its generally a tidy dataset.

It's a dataset that has 11085 rows, and 3 columns.

### Data Analysis


```python
# Counting the number of participants from each country
olympic_2021['NOC'].value_counts()
```




    United States of America         615
    Japan                            586
    Australia                        470
    People's Republic of China       401
    Germany                          400
                                    ... 
    South Sudan                        2
    Dominica                           2
    Nauru                              2
    St Vincent and the Grenadines      2
    Vanuatu                            2
    Name: NOC, Length: 206, dtype: int64




```python
olympic_2021['NOC'].value_counts().tail(10)
```




    United Republic of Tanzania      2
    Myanmar                          2
    Andorra                          2
    Saint Kitts and Nevis            2
    Mauritania                       2
    South Sudan                      2
    Dominica                         2
    Nauru                            2
    St Vincent and the Grenadines    2
    Vanuatu                          2
    Name: NOC, dtype: int64




```python
# Filtering the top 10 countries with the most number of participants
olympic_2021['NOC'].value_counts().head(10)
```




    United States of America      615
    Japan                         586
    Australia                     470
    People's Republic of China    401
    Germany                       400
    France                        377
    Canada                        368
    Great Britain                 366
    Italy                         356
    Spain                         324
    Name: NOC, dtype: int64




```python
olympic_2021['NOC'].count()
```




    11085




```python
# Calculating the percentage of participants from each country.
((olympic_2021['NOC'].value_counts() / olympic_2021['NOC'].count())*100).head(10)
```




    United States of America      5.548038
    Japan                         5.286423
    Australia                     4.239964
    People's Republic of China    3.617501
    Germany                       3.608480
    France                        3.400992
    Canada                        3.319802
    Great Britain                 3.301759
    Italy                         3.211547
    Spain                         2.922869
    Name: NOC, dtype: float64



From the above filters, we can establish that The United States of America had the highest number of particiants,at 615, reprenting approximately 5.55%, then Japan that sent 586 participants, translating to appoximately 5.28%,followed by Australia at 4.24% of all the articipants.


```python
# Working out the number of participants per discipline
olympic_2021['Discipline'].value_counts()
```




    Athletics                2068
    Swimming                  743
    Football                  567
    Rowing                    496
    Hockey                    406
    Judo                      373
    Handball                  343
    Shooting                  342
    Sailing                   336
    Rugby Sevens              283
    Basketball                280
    Wrestling                 279
    Volleyball                274
    Boxing                    270
    Water Polo                269
    Fencing                   249
    Equestrian                237
    Canoe Sprint              236
    Baseball/Softball         220
    Cycling Track             208
    Cycling Road              190
    Weightlifting             187
    Artistic Gymnastics       187
    Tennis                    178
    Table Tennis              164
    Badminton                 164
    Diving                    133
    Taekwondo                 123
    Archery                   122
    Golf                      115
    Triathlon                 106
    Artistic Swimming          98
    Rhythmic Gymnastics        95
    Beach Volleyball           90
    Canoe Slalom               78
    Skateboarding              77
    Karate                     77
    Cycling Mountain Bike      74
    Modern Pentathlon          69
    3x3 Basketball             62
    Marathon Swimming          49
    Cycling BMX Racing         43
    Surfing                    38
    Sport Climbing             37
    Trampoline Gymnastics      31
    Cycling BMX Freestyle      19
    Name: Discipline, dtype: int64




```python
olympic_2021['Discipline'].count()
```




    11085




```python
# Calculating the percentage of participants per each discipline.
(olympic_2021['Discipline'].value_counts() / olympic_2021['Discipline'].count())*100
```




    Athletics                18.655841
    Swimming                  6.702751
    Football                  5.115020
    Rowing                    4.474515
    Hockey                    3.662607
    Judo                      3.364908
    Handball                  3.094272
    Shooting                  3.085250
    Sailing                   3.031123
    Rugby Sevens              2.553000
    Basketball                2.525936
    Wrestling                 2.516915
    Volleyball                2.471809
    Boxing                    2.435724
    Water Polo                2.426703
    Fencing                   2.246279
    Equestrian                2.138024
    Canoe Sprint              2.129003
    Baseball/Softball         1.984664
    Cycling Track             1.876410
    Cycling Road              1.714028
    Weightlifting             1.686964
    Artistic Gymnastics       1.686964
    Tennis                    1.605774
    Table Tennis              1.479477
    Badminton                 1.479477
    Diving                    1.199820
    Taekwondo                 1.109608
    Archery                   1.100586
    Golf                      1.037438
    Triathlon                 0.956247
    Artistic Swimming         0.884078
    Rhythmic Gymnastics       0.857014
    Beach Volleyball          0.811908
    Canoe Slalom              0.703654
    Skateboarding             0.694632
    Karate                    0.694632
    Cycling Mountain Bike     0.667569
    Modern Pentathlon         0.622463
    3x3 Basketball            0.559314
    Marathon Swimming         0.442039
    Cycling BMX Racing        0.387912
    Surfing                   0.342806
    Sport Climbing            0.333784
    Trampoline Gymnastics     0.279657
    Cycling BMX Freestyle     0.171403
    Name: Discipline, dtype: float64




```python
olympic_2021['Discipline'].value_counts().head(10)
```




    Athletics       2068
    Swimming         743
    Football         567
    Rowing           496
    Hockey           406
    Judo             373
    Handball         343
    Shooting         342
    Sailing          336
    Rugby Sevens     283
    Name: Discipline, dtype: int64



We can establish that Athletics had the highest number of particiants,at 2068, reprenting approximately 18.66%, then Swimming which had 743 participants, translating to appoximately 6.70%,followed by Football and Rowing at 5.12% and 4.47% respectively, of all the articipants. Trampoline and Cycling BMX Freestyle disciplines had the least numbers, with only 31 and 19 participants respectively.

### Data Visualization


```python
# Representing the top 10 disciplines interms of participants using pie-chart

Discipline = [2068,743,567,496,406,373,343,342,336,283]

my_labels = 'Athletics','Swimming','Football','Rowing','Hockey','Judo','Hsndball','Shooting','Sailing','rugby Sevens'
plt.pie(Discipline,labels=my_labels,autopct='%1.1f%%')
plt.title('The Top 10 Disciplines In The 2021 Tokyo Olympics', fontsize=14)
plt.axis('equal')
plt.show()
```


    
![png](output_20_0.png)
    


The Olympic Games that were held in Tokyo,Japan in August 2021 had very interesting details that I'd wish to share with the lovers of the Olympic Games: 

There were a total of 206 NOCs nations that participated in the recently concluded Tokyo Olympic Games with 11,085 paricipating athletes. The United States of America had the highest number of particiants,at 615, reprenting approximately 5.55%, then Japan that sent 586 participants, translating to appoximately 5.28%,followed by Australia at 4.24% of all the articipants. Out of the 206 NOCs nations, 17 of them only had 2 participants each.

There were a total of 47 disciplines. Athletics had the highest number of particiants,at 2068, reprenting approximately 18.66%, then Swimming which had 743 participants, translating to appoximately 6.70%,followed by Football and Rowing at 5.12% and 4.47% respectively, of all the articipants. Trampoline and Cycling BMX Freestyle disciplines had the least numbers, with only 31 and 19 participants respectively.

The pie-chart shared only depicts the percentage share of participants among the first 10 disciplines.

The dataset used in the analysis and visualization was sourced from: https://www.kaggle.com/arjunprasadsarkhel/2021-olympics-in-tokyo





```python

```
