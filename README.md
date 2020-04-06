# Coronavirus (COVID-19) statistics in China

A data set on COVID-19 pandemic in China, which covers daily statistics of confirmed cases (new and cumulative), recoveries (new and cumulative) and deaths (new and cumulative) at city level.
All data are extracted from Chinese government reports.
We have finished the data clean, so enjoy the dataset and have fun.

If you find this dataset useful in your research please consider citing:

    @article{liu2020coronavirus,
        title={Coronavirus disease 2019 (COVID-19) outbreak in China, spatial temporal dataset},
        author={Wenyuan Liu and Peter Tsung-Wen Yen and Siew Ann Cheong},
        year={2020},
        eprint={2003.11716},
        archivePrefix={arXiv},
        primaryClass={q-bio.PE}
    }

# File format
Each file contains 393 lines and 44 columns: the first row is the header, the name for each column, while other rows are the data for all cities/counties. For each row, the first four columns are names for city/county: the first cloumns is the name of city/county in English, the second column is the name of the provincial-level region this city/county belongs to in English, the third column is the name of city/county in Chinese, and the fourth column is the name of the provincial-level region this city/county belongs to in Chinese. The remaining columns are dates ranging from 20 January 2020 to Febraruy 29 2020 (in YYYY-
MM-DD format).  For example, in China_accumulated_infections.csv, for row 1, column 1 is "Beijing Municipality", whereas, column 20 (2020-02-04) is 253. This tells us that there are 253 confirmed cases reported in Beijing up till 24:00 4 Febraruy 2020.

# Gallery

```python
import pandas as pd
import matplotlib.pyplot as plt

new_infections = pd.read_csv("China_daily_new_infections.csv")
total_infections = pd.read_csv("China_accumulated_infections.csv")
Wenzhou = total_infections[total_infections['Prefectural level or Country level'] == "Wenzhou"]
dates = Wenzhou.columns[4:].tolist()
numbers = Wenzhou.iloc[0].tolist()[4:]

fig, ax = plt.subplots()
ax.bar(dates, numbers)
plt.xticks(dates, dates, rotation='vertical')
plt.title("Wenzhou")
```
![image](https://github.com/cheongsa/Coronavirus-COVID-19-statistics-in-China/blob/master/Wenzhou.png)

```python
province_data = new_infections.groupby('Provincial-level regions').sum().reset_index()
dates = province_data.columns[1:].tolist()
Anhui = province_data[province_data['Provincial-level regions'] == "Anhui"]
Guangdong = province_data[province_data['Provincial-level regions'] == "Guangdong"]
fig, ax = plt.subplots()
ax.plot(dates, Anhui.iloc[0][1:].tolist(), label="Anhui")
ax.plot(dates, Guangdong.iloc[0][1:].tolist(), label="Guangdong")
ax.set_xticklabels(dates, rotation='vertical')
plt.legend()
```
![image](https://github.com/cheongsa/Coronavirus-COVID-19-statistics-in-China/blob/master/Guangdong_Anhui.png)

![Test image](https://github.com/cheongsa/Coronavirus-COVID-19-statistics-in-China/blob/master/0201.png)
*Figure 1:  The number of new infections of COVID-19 of all cities in China on 1 Feb 2020.*

![image](https://github.com/cheongsa/Coronavirus-COVID-19-statistics-in-China/blob/master/0211.png)
*Figure 2:  The number of new infections of COVID-19 of all cities in China on 11 Feb 2020.*

![image](https://github.com/cheongsa/Coronavirus-COVID-19-statistics-in-China/blob/master/0221.png)
*Figure 3:  The number of new infections of COVID-19 of all cities in China on 21 Feb 2020.*

# Changelog

## [0.90] - 2020-04-06

## Changed

update China_daily_new_infections.csv

update China_daily_new_recoveries.csv

update China_daily_new_deaths.csv

update China_accumulated_infections.csv

update China_accumulated_recoveries.csv

update China_accumulated_deaths.csv

The information on Hubei, Liaoning and Henan has been added. 


delete China_daily_new_infections_old.csv

delete China_daily_new_recoveries_old.csv

delete China_daily_new_deaths_old.csv

delete China_accumulated_infections_old.csv

delete China_accumulated_recoveries_old.csv

delete China_accumulated_deaths_old.csv



## [0.70] - 2020-04-03

## Changed

update China_daily_new_infections.csv

update China_daily_new_recoveries.csv

update China_daily_new_deaths.csv

update China_accumulated_infections.csv

update China_accumulated_recoveries.csv

update China_accumulated_deaths.csv

The information on Hebei, Shanxi, Jilin, Heilongjiang, Zhejiang and Sichuan has been added.

## [0.60] - 2020-04-02

## Changed

update China_daily_new_infections.csv

update China_daily_new_recoveries.csv

update China_daily_new_deaths.csv

update China_accumulated_infections.csv

update China_accumulated_recoveries.csv

update China_accumulated_deaths.csv

The information on Inner Mongolia, Jiangsu, Hunan, Guangdong, Guangxi, Hainan, Guizhou, Yunnan, Shaanxi has been added.


## [0.40] - 2020-04-01

## Changed

rename China_daily_new_infections.csv as China_daily_new_infections_old.csv

rename China_daily_new_recoveries.csv as China_daily_new_recoveries_old.csv

rename China_daily_new_deaths.csv as China_daily_new_deaths_old.csv

rename China_accumulated_infections.csv as China_accumulated_infections_old.csv

rename China_accumulated_recoveries.csv as China_accumulated_recoveries_old.csv

rename China_accumulated_deaths.csv as China_accumulated_deaths_old.csv

### Added

China_daily_new_infections.csv

China_daily_new_recoveries.csv

China_daily_new_deaths.csv

China_accumulated_infections.csv

China_accumulated_recoveries.csv

China_accumulated_deaths.csv

(These files only includes Beijing, Tianjin, Shanghai, Anhui, Fujian, Jiangxi, Shandong, Chongqing, Tibet, Gansu, Qinghai, Ningxia, Xinjiang, HongKong and Macao.)

## [0.10] - 2020-03-22

### Added
China_daily_new_recoveries.csv

China_accumulated_recoveries.csv

### Changed
rename China_new_infections.csv as China_daily_new_infections.csv

rename China_total_infections.csv as China_accumulated_infections.csv

## [0.03] - 2020-03-20

### Added
China_new_infections.csv

### Changed
renamed China_total_cases_of_confirmed_infections.csv as China_total_infections.csv

## [0.02] - 2020-03-18

### Added
China_daily_new_deaths.csv
China_accumulated_deaths.csv

## [0.01] - 2020-03-16

### Added
China_total_cases_of_confirmed_infections.csv



# Contributors
LIU WENYUAN (Contributed equally)

Peter Tsung-Wen Yen (Contributed equally)

# Contact information
wenyuan.liu@ntu.edu.sg

peteryen2017@gmail.com
