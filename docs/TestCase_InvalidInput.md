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

### Test Script/Results (Before Software Fixing)

#### 1. Unit Tesing
| Test | Input                      | Expected Result | Actual Result | Pass/Fail |
| ---- | -------------------------- | --------------- | ------------- | --------- |
| 1    | data = utils.get_json("{}/{}".format('https://finance.yahoo.com/quote', 'IWO'), None)                | An Exception is raised            | ` KeyError: 'upgradeDowngradeHistory'`          | Pass      |
| 2    | data = False               |An Exception is raised            | `TypeError: 'bool' object is not subscriptable`          | Pass      |
| 3    | data = None                | An Exception is raised            | `TypeError: 'NoneType' object is not subscriptable`          | Pass      |
| 4    | data = 'Wrong data format' | An Exception is raised            | `TypeError: string indices must be integers`          | Pass      |
| 5    | data = [1, 2, 3]           | An Exception is raised            | `TypeError: list indices must be integers or slices, not str`          | Pass      |
| 6    | data = 1                   | An Exception is raised            | `TypeError: 'int' object is not subscriptable`          | Pass      |

* Noted that this test case was marked as "expected failure" so the expected results of the test scripts are failure. If all the test scripts fail, the program will return success as no bugs were found in the program. If all the test scripts pass, the program will return failure as there are bugs in the program.

#### 2. Doctests

| Test | Input                      | Expected Result | Actual Result | Pass/Fail |
| ---- | -------------------------- | --------------- | ------------- | --------- |
| 1    | data = utils.get_json("{}/{}".format('https://finance.yahoo.com/quote', 'IWO'), None)                | None            | ` KeyError: 'upgradeDowngradeHistory'`          | Fail      |
| 2    | data = False               | None            | `TypeError: 'bool' object is not subscriptable`          | Fail      |
| 3    | data = None                | None            | `TypeError: 'NoneType' object is not subscriptable`          | Fail      |
| 4    | data = 'Wrong data format' | None            | `TypeError: string indices must be integers`          | Fail      |
| 5    | data = [1, 2, 3]           | None            | `TypeError: list indices must be integers or slices, not str`          | Fail      |
| 6    | data = 1                   | None           | `TypeError: 'int' object is not subscriptable`          | Fail      |

### Test Script/Results (After Software Fixing)
#### 1. Unit Tesing
| Test | Input                      | Expected Result | Actual Result | Pass/Fail |
| ---- | -------------------------- | --------------- | ------------- | --------- |
| 1    | data = utils.get_json("{}/{}".format('https://finance.yahoo.com/quote', 'IWO'), None)                | An Exception is raised            | None          | Fail      |
| 2    | data = False               |An Exception is raised            | None          | Fail      |
| 3    | data = None                | An Exception is raised            | None          | Fail      |
| 4    | data = 'Wrong data format' | An Exception is raised            | None          | Fail      |
| 5    | data = [1, 2, 3]           | An Exception is raised            | None          | Fail      |
| 6    | data = 1                   | An Exception is raised            | None          | Fail      |

* Noted that this test case was marked as "expected failure" so the expected results of the test scripts are failure. If all the test scripts fail, the program will return success as no bugs were found in the program. If all the test scripts pass, the program will return failure as there are bugs in the program.

#### 2. Doctests

| Test | Input                      | Expected Result | Actual Result | Pass/Fail |
| ---- | -------------------------- | --------------- | ------------- | --------- |
| 1    | data = utils.get_json("{}/{}".format('https://finance.yahoo.com/quote', 'IWO'), None)                | None            | None          | Pass      |
| 2    | data = False               | None            | None          | Pass      |
| 3    | data = None                | None            | None          | Pass      |
| 4    | data = 'Wrong data format' | None            | None          | Pass      |
| 5    | data = [1, 2, 3]           | None            | None          | Pass      |
| 6    | data = 1                   | None           | None          | Pass      |
