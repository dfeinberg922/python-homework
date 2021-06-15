```python
# Importing csv module
import csv
# open and access the csv file
seperator = "-" * 64
with open('week_2_Week2_HW_PyBank_budget_data.csv', newline='') as csvfile:
    # declared spreadsheet variable and read the file
#     spreadsheet = csv.reader(csvfile, delimiter=' ', quotechar='|')
    spreadsheet = csv.reader(csvfile, delimiter=',')
    header = next(spreadsheet)
    print(header)
    print(seperator)
    count = 0
    total = 0
    average = []
    minimum = 999999999999
    maximum = -999999999999
    minimum_month = ""
    maximum_month = ""
    previous_month = 0
    
    
    


    # looped through the spreadsheet

    for row in spreadsheet:
        count += 1
        row[1] = int(row[1])
        total += row[1]
        if count >1 :
            change = row[1]-previous_month
            average.append(change)
            if change < minimum:
                minimum = change
                minimum_month = row[0]
            if change > maximum:
                maximum = change
                maximum_month = row[0]
        
        
        previous_month = row[1]



print(row)
print("Count:", count)
print("Total:", total)

```

    ['Date', 'Profit/Losses']
    ----------------------------------------------------------------
    ['Feb-2017', 671099]
    Count: 86
    Total: 38382578



```python
len(average)
```




    85




```python
ret = f'''
Financial Analysis
----------------------------
Total Months: {count}
Total: ${total:,.0f}
Average  Change: ${sum(average)/len(average):,.4f}
Greatest Increase in Profits: {maximum_month} (${maximum:,.0f})
Greatest Decrease in Profits: {minimum_month} (${minimum:,.0f})
'''
print(ret)
```

    
    Financial Analysis
    ----------------------------
    Total Months: 86
    Total: $38,382,578
    Average  Change: $-2,315.1176
    Greatest Increase in Profits: Feb-2012 ($1,926,159)
    Greatest Decrease in Profits: Sep-2013 ($-2,196,167)
    



```python

```
