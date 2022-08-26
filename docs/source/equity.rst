Equity
==============

The Equity Object is the primary object necessitated for operation of the library. It contains the timeseries (OHLC) data alongside the ticker, overview information,
financials and others. Through this object it is possible to construct

**How to Initialise?**

.. code-block:: 

    equity = eqkit.Equity(ticker='AAPL', datafeed=eqkit.feeds.YFinance())



Supported Data Types
---------------------

Timeseries Data
++++++++++++++++

:code:`Overview()`
+++++++++++++++++++

This method downloads the overview data from the specified :code:`datafeed`, it returns the DataFrame and also 
saves it onto the object. 

.. code-block:: 

    equity.Overview()

**Requires:** None
**Returns:** obj: pandas.DataFrame

:code:`IncomeStatement()`
+++++++++++++++++++++++++

.. code-block:: 

    equity.IncomeStatement()

**Requires:** None
**Returns:** obj: pandas.DataFrame

:code:`BalanceSheet()`
+++++++++++++++++++++++

.. code-block:: 

    equity.BalanceSheet()

**Requires:** None
**Returns:** obj: pandas.DataFrame

:code:`CashFlow()`
+++++++++++++++++++

.. code-block:: 

    equity.CashFlow()

**Requires:** None
**Returns:** obj: pandas.DataFrame

:code:`Ratings()`
+++++++++++++++++++

.. code-block:: 

    equity.Ratings()

**Requires:** None
**Returns:** obj: pandas.DataFrame

:code:`Holders()`
+++++++++++++++++++

.. code-block:: 

    equity.Holders()

**Requires:** None
**Returns:** obj: pandas.DataFrame

:code:`Float()`
+++++++++++++++++++

.. code-block:: 

    equity.Float()

**Requires:** None
**Returns:** obj: pandas.DataFrame

:code:`News()`
+++++++++++++++++++

.. code-block:: 

    equity.News()

**Requires:** None
**Returns:** obj: pandas.DataFrame

:code:`MutualFunds()`
+++++++++++++++++++++

.. code-block:: 

    equity.MutualFunds()

**Requires:** None
**Returns:** obj: pandas.DataFrame

Quantitative Summary
---------------------

.. code-block:: 

    equity.quant_summary(rfr=0)

**Requires:** None
**Returns:** obj: pandas.DataFrame


Valuation
----------

.. code-block:: 

    equity.value(valuation=eqkit.Model, **kwargs)

**Requires:** None
**Returns:** float: priceTarget

Study
------

.. code-block:: 

    equity.Study(study=eqkit.Study, **kwargs)

**Requires:** None
**Returns:** None -- plots instead

Plotting
---------

.. code-block:: 

    equity.plot(mode, )

**Requires:** None
**Returns:** obj: pandas.DataFrame

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