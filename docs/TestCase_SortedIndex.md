# Test Case: test_if_sorted

### Purpose:

Test the case the order of the data returned in a ascending date order, oldest to newest date at the end.

### Tester name:

Anjesh Shrestha

### Date of Test:

March 26, 2021

### Operating System:

Windows 10

### Required Configuration:

No special setup

### Test Script/Results

| Test | Input                                            | Expected Result                                                   | Actual Result                                                     | Pass/Fail |
| ---- | ------------------------------------------------ | ----------------------------------------------------------------- | ----------------------------------------------------------------- | --------- |
| 1    | data = 'https://finance.yahoo.com/quote/MSFT', symbol = 'MSFT' | Index values are sorted in an ascending orders, i.e. `TickerBase.analyst_recommendations(self, data).index[i]` > `TickerBase.analyst_recommendations(self, data).index[i-1]` where i is in range (1, index_values.length - 1)| Index values are sorted in an ascending orders, i.e. `TickerBase.analyst_recommendations(self, data).index[i]` > `TickerBase.analyst_recommendations(self, data).index[i-1]` where i is in range (1, index_values.length - 1) | Pass      |
