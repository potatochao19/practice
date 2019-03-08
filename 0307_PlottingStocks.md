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
with open('googl.csv','r') as csv_file:
    reader = csv.DictReader(csv_file)
    data = {}
    for row in reader:
        for header, value in row.items():
            try:
                data[header].append(value)
            except KeyError:
                data[header] = [value]

googl_date = data['Date']
x = [datetime.datetime.strptime(i, '%m/%d/%Y') for i in googl_date]
googl_values = data['High']
y = [float(i.replace(',','')) for i in googl_values]

plt.plot(x,y)
plt.title('Google Stock - Daily High')
plt.xlabel('Date')
plt.ylabel('USD')

plt.show()
```

Next step: importing Apple stock data and matching with correct dates on existing chart
