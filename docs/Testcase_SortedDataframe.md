# Test Case: test_if_sorted

### Purpose:

Test the case where correctly formatted data is passed into `analyst_recommendations()`. Test if the index values of the recommendations are sorted in an ascending order. / Test if `sort_index()` in `self._recommendations = rec[['Firm', 'To Grade', 'From Grade', 'Action']].sort_index()` is working correctly.


### Tester name:

Shelly Xue

### Date of Test:

March 26, 2021

### Operating System:

Windows 10, MacOS

### Required Configuration:

No special setup

### Test Script/Results

| Test | Input                                            | Expected Result                                                   | Actual Result                                                     | Pass/Fail |
| ---- | ------------------------------------------------ | ----------------------------------------------------------------- | ----------------------------------------------------------------- | --------- |
| 1    | data = 'https://finance.yahoo.com/quote/MSFT', symbol = 'MSFT' | Index values are sorted in an ascending orders, i.e. `TickerBase.analyst_recommendations(self, data).index[i]` > `TickerBase.analyst_recommendations(self, data).index[i-1]` where i is in range (1, index_values.length - 1)| Index values are sorted in an ascending orders, i.e. `TickerBase.analyst_recommendations(self, data).index[i]` > `TickerBase.analyst_recommendations(self, data).index[i-1]` where i is in range (1, index_values.length - 1) | Pass      |
