# Test Case: test_date_time_format

### Purpose:

Test the case where correctly formatted data is passed into `analyst_recommendations()`. Test if the data type of the index `Date` is converted from epoch to datetime. / Test if `pandas.to_datetime()` is working correctly.

### Tester name:

Shelly Xue

### Date of Test:

March 26, 2021

### Operating System:

Windows 10, MacOS

### Required Configuration:

Install python datetime module

### Test Script/Results

| Test | Input                                                              | Expected Result                                              | Actual Result | Pass/Fail |
| ---- | ------------------------------------------------------------------ | ------------------------------------------------------------ | ------------- | --------- |
| 1    | data = 'https://finance.yahoo.com/quote/MSFT', symbol = 'MSFT'     | All the values in the index column `Date` are displayed in the required format: `YYY/MM/DD HH:MM:SS`. I.e. the data type of all the values in the index column `Date` is `datetime.datetime`. | All the values in the index column `Date` are displayed in the required format: `YYYY/MM/DD HH:MM:SS`. I.e. the data type of all the values in the index column `Date` is `datetime.datetime`. | Pass      |
