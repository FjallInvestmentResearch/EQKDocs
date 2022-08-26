Equity object
==============

The Equity Object is the primary object necessitated for operation of the library. It contains the timeseries (OHLC) data alongside the ticker, overview information,
financials and others. Through this object it is possible to construct

Supported Data Types
---------------------

Timeseries Data
++++++++++++++++

:code:`Overview()`
+++++++++++++++++++

:code:`IncomeStatement()`
+++++++++++++++++++++++++

:code:`BalanceSheet()`
+++++++++++++++++++++++

:code:`CashFlow()`
+++++++++++++++++++

:code:`Ratings()`
+++++++++++++++++++

:code:`Holders()`
+++++++++++++++++++

:code:`Float()`
+++++++++++++++++++

:code:`News()`
+++++++++++++++++++

:code:`MutualFunds()`
+++++++++++++++++++++

Quantitative Summary
---------------------


Valuation
----------

Study
------

Plotting
---------

Plotting Price
++++++++++++++++

:code:`plot_balancesheet(str: parameter)`
++++++++++++++++++++++++++++++++++++++++++

:code:`plot_incomestatement(str: parameter)`
++++++++++++++++++++++++++++++++++++++++++++

:code:`plot_cashflow(str: parameter)`
++++++++++++++++++++++++++++++++++++++++++

:code:`plot_holders(str: parameter)`
++++++++++++++++++++++++++++++++++++++++++

Save-State
-----------

:code:`save(str: path)`
++++++++++++++++++++++++

:code:`load(str: path)`
++++++++++++++++++++++++

Architecture
-------------