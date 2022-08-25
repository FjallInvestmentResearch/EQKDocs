Feeds
=============

Feeds are the main connectivity providers for EQKit, they enable the system to identify and retrieve the correct data upon request.
With modularity in mind, feeds were designed such that they can be easily modified, expanded or changed all-together; the key component being the
default feed (see below).
Feeds are necessary to download data using EQKit.

Default Feed
***************

::
    
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

YFinance
***************

This data feed provides connectivity to the Yahoo Finance API via the yfinance python library developed by [NAME]. It is unique as it does not
require an API_KEY and also has no request limit. This is recommended as the default datafeed. 

    Feed = eqkit.feeds.YFinance()

get_info(str: symbol)

get_ETF_info(str: symbol)

get_price(str: symbol)

get_DailyKlines(str: symbol)

get_BalanceSheet(str: symbol)

get_incomeStatement(str: symbol)

get_cashFlow(str: symbol)

get_Fund_Sectors(str: symbol)

get_Fund_Holdings(str: symbol)

get_ratings(str: symbol)

get_priceTargets(str: symbol)

get_news(str: symbol)

get_holders(str: symbol)

get_float(str: symbol)

get_mutualholders(str: symbol)

AlphaVantage
***************

API_KEY

get_info(str: symbol)

get_price(str: symbol)

get_DailyKlines(str: symbol)

get_BalanceSheet(str: symbol)

get_incomeStatement(str: symbol)

get_news(str: symbol)

get_macro_series(str: id)

check_limit()

valid_macro()

Federal Reserve (FRED)
***********************

API_KEY

get_macro_series(str: id, str: start)

Binance
********

API_KEY, SECRET_KEY

get_DailyKlines(str: symbol)

IEX Cloud
**********