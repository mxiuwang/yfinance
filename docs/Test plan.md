# Quick Access

- [1 Introduction](#1-Introduction)
  - [1.1 Objectives](#11-objectives)
  - [1.2 Team Members](#12-Team-Members)
- [2 Risk](#2-Risk)
- [3 Problems found during research](#3-Problems-found-during-research)
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

# 3 Problems found during research

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
