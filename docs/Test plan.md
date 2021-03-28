# Quick Access

- [1 Introduction](#1-Introduction)
  - [1.1 Objectives](#11-objectives)
  - [1.2 Team Members](#12-Team-Members)
- [2 Risk](#2-Risk)
- [3 Research and Screening](#3-Research-and-Screening)
  - [3.1 Issues](#31-Issues)
  - [3.2 Pull Requests](#32-Pull-Requests)
- [4 Test Approach](#4-Test-Approach)
- [5 Test Environment](#5-Test-Environment)
- [6  Planned Test](#6-Planned-Test)

# 1 Introduction

The Test Plan has been created to communicate the test approach to team members. It includes the objectives, planned test, problems found during research, risks and approach.

## 1.1 Objectives
Ever since Yahoo! finance decommissioned their historical data API, many programs that relied on it to stop working. yfinance aims to solve this problem by offering a reliable, threaded, and Pythonic way to download historical market data from Yahoo! finance. The test team is responsible for isolating and testing analysts recommendation in “base.py” file lines 361 to 373.

## 1.2 Team Members

| Name          | Email               | Role   |
| ------------- | ------------------- | ------ |
| Anjesh        | anjesh@ualberta.ca  | Tester |
| Grace Fu      | chuqing@ualberta.ca | Tester |
| Michelle Wang | mxwang@ualberta.ca  | Tester |
| Shelly        | yuqing6@ualberta.ca | Tester |
| Wendy Chen    | cwchen@ualberta.ca  | Tester |

# 2 Risk
| # | Risk                                                                                                         | Impact | Trigger                               | Mitigation Plan                                                                                                                                                                                          |
|---|--------------------------------------------------------------------------------------------------------------|--------|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | Scope Creep – as testers become more familiar with the tool, they will want more functionality               | High   | Delayed implementation/release date   | Each iteration, functionality will be closely monitored. Priorities will be set and discussed by stakeholders. Since the driver is functionality and not time, it may be necessary to push the date out. |
| 2 | Changes to the functionality may negate the tests already written and we may lose test cases already written | High   | Loss of all test cases                | Run tests before pushing to Github, and only merge approved/tested PRs. Export data prior to any upgrade, massage as necessary and re-import after upgrade.                                              |
| 3 | Weekly delivery is not possible because the developer works remotely                                         | Medium | Product doesn't get delivered on time | Regular standups/meetings to communicate with all members, and discuss progress.                                                                                                                         |
| 4 | Overestimating or underestimating the project requirements and potentially cause scheduling errors           | Medium | Product doesn't get delivered on time | Break down the tasks needed to be done and go through upcoming tasks every member has to do at each weekly project meeting.                                                                              |
| 5 | Unable to install consistent testing environments across all OS/machines                                     | Medium | Tests only work on some machines      | Test on all systems (Windows, Linux, MacOS)                                                                                                                                                              |
| 6 | Unable to isolate/test some features                                                                         | High   | Incomplete test cases                 | Ask for help at office hours, collaborate with teammates to exchange ideas                                                                                                                               |

# 3 Research and Screening
This sections list all the pull requests and issues that are related to the piece of code.
## 3.1 Issues
- **Issue#167**: Attributes in yf.Ticker("MSFT") as dict
  - https://github.com/ranaroussi/yfinance/issues/167
  - The issue author was asking for the purpose of storing each value as an attribute instead of in a nested dictionary.
  - This issue is related to the piece of code to which we were assigned to because the value returned from our function was stored in `self._recommendations`, that is, an attribute, instead of a nested dictionary. 

- **Issue#329**: Analysis / Recommendations
  - https://github.com/ranaroussi/yfinance/issues/329
  - The issue author got an value error when trying to generate analysis recommendations. The author believed the reason of the error was 
    > Yahoo Finance has removed the table format from their Analysis tab.

    However, the author did not pose the details of the error. The description of this issue was not clear enough for investigation. 

## 3.2 Pull Requests
- **PR#309**: Integrate fixes from some forks, minor cleanups
  - https://github.com/ranaroussi/yfinance/pull/309
  - In this PR, a if condition was added to the function. The following block of statement will only be executed if the `data` passed in the function call contains `upgradeDowngradeHistory` and `history`.
  ```
  rec = _pd.DataFrame(
                    data["upgradeDowngradeHistory"]["history"]
                )
                rec["earningsDate"] = _pd.to_datetime(
                    rec["epochGradeDate"], unit="s"
                )
                rec.set_index("earningsDate", inplace=True)
                rec.index.name = "Date"
                rec.columns = utils.camel2title(rec.columns)
                self._recommendations = rec[
                    ["Firm", "To Grade", "From Grade", "Action"]
                ].sort_index()
  ```
  - This change implements a solution to one of the problems identified by our tests. Our tests discovered that an exception will be raised if the varaible passed in the function call does not contain `upgradeDowngradeHistory` and `history`. This PR solved this issue by checking if the variable contains `upgradeDowngradeHistory` and `history` before executing the function.

- **PR#321**: Fixed stock.financials/balance_sheet/cashflow . Added valuation indicators.
  - https://github.com/ranaroussi/yfinance/pull/321
  - In this PR, the varaible `data` was rename to `qssData`. This change would not affect our test cases.

- **PR#590**: change _get_fundamentals to keep QuoteSummaryStore in memory for later use
  - https://github.com/ranaroussi/yfinance/pull/590
  - In this PR, one more restriction was added to the `data` passed in the function. This change would affect our test cases because we might need to redefine what is the correct data format.

# 4 Test Approach

We will use doctests and unit testing to test the functionalities of the piece of code assigned to us. We will test whether the function behaves abnormally, whether there are errors in the data structure, whether the performance of the function are satisfied, etc. A test case sheet will be created for each test case identified during planning and added to Github.

# 5 Test Environment

Python 3.7 or later is required for running the application. The Python unittest library should also be installed in order to run the unit test files.

# 6 Planned Test
* Test the case where correctly formatted data is passed into analyst_recommendations(). Test if the titles of the output of analyst_recommendations(data) is correctly converted from camel case to title case. ([Details](TestCase_ConvertCamelTitles.md))
* Test the case where correctly formatted data is passed into analyst_recommendations(). Test if the returned value is in the DataFrame format.([Details](TestCase_DataFrame.md))
* Test the case where correctly formatted data is passed into analyst_recommendations(). When the var output is not None, the recommendation's index name should be updated to "Date".([Details](TestCase_IndexName.md))
* Test the case where correctly formatted data is passed into analyst_recommendations(). Test the case the order of the data returned in a ascending date order, oldest to newest date at the end.([Details](TestCase_SortedIndex.md))
* Test the case where correctly formatted data is passed into analyst_recommendations(). Test the case of the index values for the data is in datetime format.([Details](TestCase_ValidIndexFormat.md))
* Test if an exception will be raised if incorrect data is passed into analyst_recommendations(). This test was marked as an "expected failure" because if an exception is thrown, it means that the function will crash when an invalid variable is passed. The original code works with no issue because it uses except Exception: pass to hide the bugs. ([Details](TestCase_InvalidInput.md))
