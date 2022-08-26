Data Feeds
=============

Feeds are the main connectivity providers for EQKit, they enable the system to identify and retrieve the correct data upon request.
With modularity in mind, feeds were designed such that they can be easily modified, expanded or changed all-together; the key component being the
default feed (see below).
Feeds are necessary to download data using EQKit.

.. note:: 

    At this time, EQKit only supports daily prices as valid OCHL input. This is due to the accessibility & common use of such data in the equities space. 


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
******************

In normal operation, a user would not call the data feed directly, but instead use it on an instanciated object like an :code:`Equity`. However, data feeds are a key feature
for users looking to download and aggregate financial data through EQKit. The structure of the relationship between the data feed and object means that the data feed package is easy 
expandable to other providers or to include new features. Although, the most important aspect of the library in this regard is interoperability across data feeds. This is possible as 
the objects are exchange agnostic while the :code:`Scanner` aggregation tool accounts for the set data feed. 

**What API keys do I need?**
You can test most functionality without a key, simply by using the :code:`YFinance()` data feed. However, for full functionality we recommend that users acquire at least a key for the 
:code:`FredAPI()` and :code:`Binance()` data feeds to cover the Macro and Crypto data inputs. 
If you are using another data provider, you can easily build a new data feed to cover your needs!

**Correct Usage**

This example shows proper useage of the :code:`YFinance()` data feed; the requested symbol is that of an equity and the retrival methods are both supported by the feed. 

.. code-block:: 

    feed = eqkit.feeds.YFinance()
    stock = eqkit.Equity('AAPL', feed)
    
    stock.Overview()
    stock.News()

**Incorrect Usage**

This first incorrect example showcases code where one is using an :code:`Equity`-only function using a :code:`Crypto` data feed. This action
returns an error.

.. code-block:: 

    feed = eqkit.feeds.Binance("KEY", "OTHER_KEY")
    feed.get_info('AAPL')

This second example presents a scenario which a user is more likely to encounter. Here although the data feed supports equities, we call a method - namely
:code:`Ratings()` which is not supported by the :code:`AlphaVantage` feed. This will also return an error.

.. code-block:: 

    feed = eqkit.feeds.AlphaVantage("KEY")
    equity = eqkit.Equity('AAPL', feed)
    equity.Ratings()

**How does the data feed know what the ticker is?**

*It doesn't!* The data feed is 'raw' and results without proper validation of the retieved asset data might be problematic and should be kept in mind. 
In normal operation users should not break the data feeds given that only certain data is supported by each major data object.  

YFinance
***************

This data feed provides connectivity to the `Yahoo Finance API <https://policies.yahoo.com/us/en/yahoo/terms/product-atos/apiforydn/index.htm>`_ 
via the `yfinance python library <https://github.com/ranaroussi/yfinance>`_ developed by Ran Aroussi. It is unique as it does not
require an API_KEY and also has no request limit. This is recommended as the default datafeed for Equity & ETF dsta for personal use. 

* `Documentation <https://github.com/ranaroussi/yfinance>`
* **Supported Version:** 0.1.74
* **Needs API Key?** No

.. code-block:: 

    Feed = eqkit.feeds.YFinance()


:code:`get_info(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads overview information for an :code:`Equity()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_info('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_ETF_info(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads overview information for an :code:`ETF()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_ETF_info('SPY')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_price(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads and returns the current price as a float.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_price('AAPL')

**Requires:** str: symbol

**Returns:** float: price

:code:`get_DailyKlines(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads :abbr:`OHLC (Open-High-Low-Close)` data for the specified symbol. 

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_DailyKlines('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_BalanceSheet(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Annual Balance Sheet of a specified ticker and is only available through the :code:`Equity()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_BalanceSheet('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_incomeStatement(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Annual Income Statement of a specified ticker and is only available through the :code:`Equity()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_incomeStatement('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_cashFlow(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Annual Cash Flow Statement of a specified ticker and is only available through the :code:`Equity()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_cashFlow('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_Fund_Sectors(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Sector Weights of a specified ticker and is only available through the :code:`ETF()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_Fund_Sectors('SPY')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_Fund_Holdings(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Top Holdings of a specified ticker and is only available through the :code:`ETF()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_Fund_Holdings('SPY')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_ratings(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Analyst Ratings of a specified ticker and is only available through the :code:`Equity()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_ratings('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_priceTargets(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Analyst Price Targets of a specified ticker and is only available through the :code:`Equity()` object.

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_priceTargets('AAPL')

:code:`get_news(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the News feed of a specified ticker.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_news('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_holders(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Top Holders of a specified ticker and is only available through the :code:`Equity()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_holders('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame


:code:`get_float(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Float Composition of a specified ticker and is only available through the :code:`Equity()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_float('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame

:code:`get_mutualholders(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Downloads the Top Mutual Fund Holders of a specified ticker and is only available through the :code:`Equity()` object.

.. code-block:: 

    from eqkit.feeds import YFinance as feed

    feed().get_mutualholders('AAPL')

**Requires:** str: symbol

**Returns:** obj: pandas.DataFrame


AlphaVantage
***************

The `AlphaVantage API <https://www.alphavantage.co/>` provides access to quality global equity data through both a free and paid API. Users get a 500 call-a-day limit and can download a 
plethora financial data, such as OCHL, fundamentals and, macroeconomic timeseries. The API data feed is connected using the :code:`requests` library and is 
built in-house. 

* `Documentation <https://www.alphavantage.co/documentation/>`
* **Supported Version:** 0.1.74
* **Needs API Key?** `Yes [FREE] <https://www.alphavantage.co/support/#api-key>`

 .. code-block:: 

    Feed = eqkit.feeds.AlphaVantage('YOUR-API-KEY-HERE')


:code:`get_info(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:code:`get_price(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:code:`get_DailyKlines(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:code:`get_BalanceSheet(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:code:`get_incomeStatement(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:code:`get_news(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:code:`get_macro_series(str: id)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:code:`check_limit()`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:code:`valid_macro()`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


Federal Reserve (FRED)
***********************

This is a macro only data feed which can be used to add external data-points for research purpuses. We also recommended its use in retriving 
US Treasury Yields and relevant timeseries. The API is provided by the Federal Reserve of St. Louis and while requiring an API KEY is has very high limits as
it caters to academic use. Nontheless, the data is very valuable in this context too and the in-house wrapper using :code:`requests` was not too hard to build either.
In order for users to achive good results in using this feed, they must use the FRED website to retrive the data :code:`id` you'd like to retrieve.

.. code-block:: 

    feed = eqkit.feeds.FredAPI("YOUR-API-KEY-HERE")


:code:`get_macro_series(str: id, str: start)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


Binance
********

API_KEY, SECRET_KEY

:code:`get_DailyKlines(str: symbol)`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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