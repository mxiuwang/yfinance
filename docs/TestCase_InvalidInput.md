# Test Case: test_IfPassingIncorrectInputDataWillRaiseException

### Purpose:

Test if an exception will be raised if incorrect data is passed into `analyst_recommendations()`. This test was marked as an "expected failure" because if an exception is thrown, it means that the function will crash when an invalid variable is passed. The original code works with no issue because it uses `except Exception: pass` to hide the bugs.

### Tester name:

Michelle Wang

### Date of Test:

March 25, 2021

### Operating System:

Windows 10, MacOS

### Required Configuration:

No special setup

### Test Script/Results

| Test | Input                      | Expected Result | Actual Result | Pass/Fail |
| ---- | -------------------------- | --------------- | ------------- | --------- |
| 1    | data = utils.get_json("{}/{}".format('https://finance.yahoo.com/quote', 'IWO'), None)                | ERROR 'upgradeDowngradeHistory'            | ERROR 'upgradeDowngradeHistory'          | Pass      |
| 2    | data = False               | ERROR 'bool' object is not subscriptable            | ERROR 'bool' object is not subscriptable          | Pass      |
| 3    | data = None                | ERROR 'NoneType' object is not subscriptable            | ERROR 'NoneType' object is not subscriptable          | Pass      |
| 4    | data = 'Wrong data format' | ERROR string indices must be integers            | ERROR string indices must be integers          | Pass      |
| 5    | data = [1, 2, 3]           | ERROR list indices must be integers or slices, not str            | ERROR list indices must be integers or slices, not str          | Pass      |
| 6    | data = 1                   | ERROR 'int' object is not subscriptable            | ERROR 'int' object is not subscriptable          | Pass      |

* Noted that this test case was marked as "expected failure" so the expected results of the test scripts are failure
