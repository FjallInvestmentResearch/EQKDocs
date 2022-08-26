Data Feeds
=============

Feeds are the main connectivity providers for EQKit, they enable the system to identify and retrieve the correct data upon request.
With modularity in mind, feeds were designed such that they can be easily modified, expanded or changed all-together; the key component being the
default feed (see below).
Feeds are necessary to download data using EQKit.

.. note:: 

    At this time, EQKit only supports daily prices as valid OCHL input. This is due to the accessibility & common use of such data. 


+---------------------------+------------------------------------------------+
| Supported Data            |    Included Data Feeds                         |
+-------------+-------------+----------+--------------+------+-----+---------+
|Asset Class  | Data Point  | YFinance | AlphaVantage | FRED | IEX | Binance |
+-------------+-------------+----------+--------------+------+-----+---------+
| **Equity**  | OCHL        |  Yes     | Yes          | No   | Yes | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | Overview    | Yes      | Yes          | No   | Yes | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | Fundamental | Yes      | Premium      | No   | Yes | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | Ratings     | Yes      | No           | No   | No  | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | Holders     | Yes      | No           | No   | No  | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | News        | Yes      | Yes          | No   | Yes | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|  **ETF**    | OCHL        | Yes      | Yes          | No   | Yes | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | Overview    | Yes      | No           | No   | No  | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | Sectors     | Yes      | No           | No   | No  | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | Holdings    | Yes      | No           | No   | No  | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | News        | Yes      | Yes          | No   | Yes | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
|   **Macro** | Timeseries  | No       | Yes          | Yes  | Yes | No      |
+-------------+-------------+----------+--------------+------+-----+---------+
| **Crypto**  | OCHL        | No       | Yes          | No   | No  | Yes     |
+-------------+-------------+----------+--------------+------+-----+---------+
|             | Overview    | No       | No           | No   | No  | Yes     |
+-------------+-------------+----------+--------------+------+-----+---------+
|             |             |          |              |      |     |         |
+-------------+-------------+----------+--------------+------+-----+---------+
| **Cost**    | --          | Free     | Free & Paid  | Free | Paid| Free    |
+-------------+-------------+----------+--------------+------+-----+---------+


Using DataFeeds
******************************

Selecting the right DataFeed is mainly based on user preference as well as the use-case and goal. The Included data feeds can enable a researcher
to perform most if not all relevant operations. Generally, certain data feeds are designed to cater to a data type; :code:`yfinance` is great for equities, 
and :code:`Binance` great for crypto. This means that not all data feeds support all data types, as we show above.

**Correct Usage**

This example shows proper useage of a data feed

.. code-block:: 

    feed = eqkit.feeds.YFinance()
    stock = eqkit.Equity('AAPL', feed)
    
    stock.Overview()
    stock.News()

**Incorrect Usage**

This first Incorrect example showcases code where one is using an :code:`Equity` only function using a :code:`Crypto` data feed. This action
returns an error.

.. code-block:: 

    feed = eqkit.feeds.Binance("KEY", "OTHER_KEY")
    feed.get_info('AAPL')

This second example presents a scenario which a user is more likely to encounter. Here although the data feed supports equities, we call a method - namely
:code:`Ratings()` which is not supported by the :code:`AlphaVantage` feed. 

.. code-block:: 

    feed = eqkit.feeds.AlphaVantage("KEY")
    equity = eqkit.Equity('AAPL', feed)
    equity.Ratings()


YFinance
***************

This data feed provides connectivity to the `Yahoo Finance API <https://policies.yahoo.com/us/en/yahoo/terms/product-atos/apiforydn/index.htm>`_ 
via the `yfinance python library <https://github.com/ranaroussi/yfinance>`_ developed by [NAME]. It is unique as it does not
require an API_KEY and also has no request limit. This is recommended as the default datafeed for Equity & ETF dsta for personal use. 

.. code-block:: 

    Feed = eqkit.feeds.YFinance()


:code:`get_info(str: symbol)`

Downloads overview information for an Equity object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_ETF_info(str: symbol)`

Downloads overview information for an ETF object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_price(str: symbol)`

Downloads and returns the current price as a float

**Requires:** str: symbol

**Returns:** float: price

:code:`get_DailyKlines(str: symbol)`

Downloads :abbr:`OHLC (Open-High-Low-Close)` data for the specified symbol. 

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_BalanceSheet(str: symbol)`

Downloads the Balance Sheet of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_incomeStatement(str: symbol)`

Downloads the Income Statement of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_cashFlow(str: symbol)`

Downloads the Cash Flow Statement of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_Fund_Sectors(str: symbol)`

Downloads the Sector Weights of a specified ticker and is only available through the :code:`ETF()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_Fund_Holdings(str: symbol)`

Downloads the Top Holdings of a specified ticker and is only available through the :code:`ETF()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_ratings(str: symbol)`

Downloads the Analyst Ratings of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_priceTargets(str: symbol)`

Downloads the Analyst Price Targets of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_news(str: symbol)`

Downloads the News feed of a specified ticker.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_holders(str: symbol)`

Downloads the Top Holders of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_float(str: symbol)`

Downloads the Float Composition of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_mutualholders(str: symbol)`

Downloads the Top Mutual Fund Holders of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame


AlphaVantage
***************

The AlphaVantage API provides access to quality global equity data and can be easily used in python. This wrapper has been created by us here at
Fjall Investment Research and directly uses :code:`requests` to communicate with the server. Through it we have packaged the most useful features
Included in the API for use in this library. 

 .. code-block:: 

    Feed = eqkit.feeds.AlphaVantage('YOUR-API-KEY-HERE')


Reference
++++++++++

API_KEY

get_info(str: symbol)

get_price(str: symbol)

get_DailyKlines(str: symbol)

get_BalanceSheet(str: symbol)

get_incomeStatement(str: symbol)

get_news(str: symbol)

get_macro_series(str: id)

check_limit(redAPI("YOUR-API-KEY-HERE")

valid_macro()



Federal Reserve (FRED)
***********************

This is a macro only data feed which can be used to add external data-points for research purpuses. We also recommended its use in retriving 
US Treasury Yields and relevant timeseries. The API is provided by the Federal Reserve of St. Louis and while requiring an API KEY is has very high limits as
it caters to academic use. Nontheless, the data is very valuable in this context too and the in-house wrapper using :code:`requests` was not too hard to build either.
In order for users to achive good results in using this feed, they must use the FRED website to retrive the data :code:`id` you'd like to retrieve.

.. code-block:: 

    feed = eqkit.feeds.FredAPI("YOUR-API-KEY-HERE")


Reference
++++++++++

API_KEY

get_macro_series(str: id, str: start)



Binance
********

Reference
++++++++++

API_KEY, SECRET_KEY

get_DailyKlines(str: symbol)

IEX Cloud
**********

Reference
++++++++++

Default Feed
***************

.. code-block:: 
    
    init()

Initialises the default feed.

**Requires:** None

**Returns:** None

::

    set_id(str: id)

Sets the exchange id. Used in internal methods.

**Requires:** str: id

**Returns:** self

    get_timeSeries(str: symbol)

Returns a :code:`timeseries` object with symbol and filled data, ready to be packaged in `Equity` or `ETF`.

**Requires:** str: symbol

**Returns:** obj: timeseries

    get_Overview(str: symbol)

Returns a pandas DataFrame containing the relevant Overview information for the :code:`Equity` as specified in :code:`get_info()`

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

    get_ETFOverview(str: symbol)

Returns a pandas DataFrame containing the relevant Overview information for the :code:`ETF` as specified in :code:`get_ETF_info()`

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

    get_Macro(str: id, str: axis)

Returns a :code:`timeseries` object with macroeconomic data, used to parse non-asset data inputs (see, FRED).
It requires the data identifier :code:`id` and the axis on which the data lie (if not 'price').

**Requires:** str: id, str: axis

**Returns:** obj: timeseries

    get_price(str: symbol)

Returns a :code:`float` price for the symbol selected.

**Requires:** str: symbol

**Returns:** float: price

    get_priceTargets(str: symbol)

Returns a Data Frame with the estimated analyst target prices; this is designed as a wrapper for functionality found in
yfinance library.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

    get_ratings(str: symbol)

Returns a Data Frame with the analyst ratings; this is designed as a wrapper for functionality found in
yfinance library.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

get_news(str: symbol)

Returns a Data Frame with the latest timestamped news.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

get_holders(str: symbol)

Returns a Data Frame with the largest institutional holders; this is designed as a wrapper for functionality found in
yfinance library.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame