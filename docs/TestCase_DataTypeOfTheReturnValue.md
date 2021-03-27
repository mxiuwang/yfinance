# Test Case: test_if_dataframe

### Purpose:

Test the case where correctly formatted data is passed into `analyst_recommendations()`. Test if the data type of the return values is dataframe. / Test if `rec = _pd.DataFrame(data['upgradeDowngradeHistory']['history'])` is working correctly.


### Tester name:

Shelly Xue

### Date of Test:

March 26, 2021

### Operating System:

Windows 10, MacOS

### Required Configuration:

Install the pandas library

### Test Script/Results

| Test | Input                                            | Expected Result                                                   | Actual Result                                                     | Pass/Fail |
| ---- | ------------------------------------------------ | ----------------------------------------------------------------- | ----------------------------------------------------------------- | --------- |
| 1    | data = 'https://finance.yahoo.com/quote/MSFT', symbol = 'MSFT' | The data type of the return value is `pandas.core.frame.DataFrame` | The data type of the return value is `pandas.core.frame.DataFrame` | Pass      |
