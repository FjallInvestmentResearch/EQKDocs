Quick Start Guide
==================

Equity
--------------------

Loading the Data
+++++++++++++++++

In EQKit, the `Equity` object uses a `DataFeed` connection to retrive data from an online source, such as *AlphaVantage*.
Users should be able to develop their own `DataFeed` objects as required.

::
    SPY = EQKit.Equity('SPY', EQKit.DataFeed.AlphaVantage('API-KEY'))

Using the above code snippet, the user creates an `Equity` object for the SPY ETF that has auto-filled OHLC values.
The timeseries is contained within the `timeseries` object, thus a user may access the raw OHLC pandas data as such:

::
    SPY.timeseries.data

Overview
+++++++++
Users can access basic information about the Equity using the `overview()` method. This requires the equity to contain an active
`DataFeed`.

::
    SPY.overview()

Quantitative Summary
+++++++++++++++++++++
We have included a basic quantitative statistic summarisation method accessible through the `Equity` object.

::
    SPY.quant_summary()
