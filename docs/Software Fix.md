## Software Fix
The bugs we found: The function will throw an exception if the data passed to the function does not contain the required keys or the data type is not "dict". The original code use try-except statement to hide this bug.

* Is there a pull request that implements a solution to the problems identified by your tests?<br>
  Yes. The PR #309 tried to solve this problem by adding an if condition: ` if data ["upgradeDowngradeHistory"] ["history”] `. The function will only be executed if data contains the required key `upgradeDowngradeHistory` and `data[upgradeDowngradeHistory]` contains the key `history`.
  
* Is there a quick fix that could be proposed to the code so that the code passes the test?<br>
  Yes. We believe that this exception could be resolved by checking the type of data and testing if the data contains the required keys before executing the function. The fix has already been implemented in base.py.
  
  Code before fixing:
  ```
       try:
            rec = _pd.DataFrame(data['upgradeDowngradeHistory']['history'])

            rec['earningsDate'] = _pd.to_datetime(rec['epochGradeDate'], unit='s')
            rec.set_index('earningsDate', inplace=True)

            rec.index.name = 'Date'
            rec.columns = utils.camel2title(rec.columns)
            self._recommendations = rec[['Firm', 'To Grade', 'From Grade', 'Action']].sort_index()
        except Exception:
            pass
  ```
  
  Code after fixing:
  ```
        rec = _pd.DataFrame(data['upgradeDowngradeHistory']['history'])
        # test if the type of data is dict
        if isinstance(data, dict):
            # test if 'upgradeDowngradeHistory' exists in data.keys
            if 'upgradeDowngradeHistory' in data:
                # test if 'history' exists in data['upgradeDowngradeHistory'].keys
                if 'history' in data['upgradeDowngradeHistory']:
                    rec = _pd.DataFrame(data['upgradeDowngradeHistory']['history'])
                    # test if 'epochGradeDate' exists in dataframe.columns
                    if "epochGradeDate" in rec.columns:
                        rec['earningsDate'] = _pd.to_datetime(rec['epochGradeDate'], unit='s')
                        rec.set_index('earningsDate', inplace=True)
                        rec.index.name = 'Date'
                        rec.columns = utils.camel2title(rec.columns)

                        # test if "Firm", "To Grade", 'From Grade', "Action" exists in dataframe.columns
                        if all(i in rec.columns for i in ("Firm", "To Grade", 'From Grade', "Action")):
                            self._recommendations = rec[['Firm', 'To Grade', 'From Grade', 'Action']].sort_index()
  ```
