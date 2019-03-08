## MatPlotLib 

- install matplotlib
- plot from CSVs
- run analysis on data

#### Plotting stock data 
I downloaded csv data for Google and Apple stock prices from Yahoo finance.

```
import matplotlib.pyplot as plt
import datetime
import csv

#extract google stock data
with open('googl.csv','r') as csv_file:
    reader = csv.DictReader(csv_file)
    data = {}
    for row in reader: #what is going on here
        for header, value in row.items():
            try:
                data[header].append(value)
            except KeyError:
                data[header] = [value]

googl_date = data['Date']
date = [datetime.datetime.strptime(i, '%m/%d/%Y') for i in googl_date]
googl_values = data['High']
googl_stock = [float(i.replace(',','')) for i in googl_values]

#extract apple stock data
with open('aapl.csv','r') as csv_file:
    reader = csv.DictReader(csv_file)
    data_2 = {}
    for row in reader:
        for header, value in row.items():
            try:
                data_2[header].append(value)
            except KeyError:
                data_2[header] = [value]

aapl_values = data_2['High']
aapl_stock = [float(i) for i in aapl_values]

fig, ax1 = plt.subplots()

ax1.set_xlabel('Date')
ax1.set_ylabel('USD')
ax1.plot(date, googl_stock,'b-',label='Google')

ax2 = ax1.twinx()
ax2.plot(date, aapl_stock,'c-',label='Apple')

ax1.legend(loc='upper left')
ax2.legend(loc='bottom left')
plt.title('Daily High')


plt.show()
```
![Output](https://github.com/potatoptty/PracticeBlog/blob/master/0308img.png?raw=true)
This works because the dates already line up, but have to figure out a way to index/match correct values to date.
