Studies
========

Methods
--------

:code:`run()`
+++++++++++++++

:code:`calc()`
+++++++++++++++

:code:`plot()`
+++++++++++++++

Calling from Objects
---------------------

.. code-block::

    stock.study(EQKit.studies.Drawdown)


Included Studies
-----------------

:code:`RollingSharpe(obj: ALPHA, int: lookback)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`LinearRegression(obj: ALPHA, obj: BETA)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`Correlation(obj: ALPHA, obj: BETA)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`Monthly(obj: ALPHA)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`Seasonality(obj: ALPHA)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`Drawdown(obj: ALPHA, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`Distributions(obj: ALPHA, obj: BETA, int: window)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`RollingReturn(obj: ALPHA, int: lookback)`
+++++++++++++++++++++++++++++++++++++++++++++++++

:code:`RollingSharp(obj: ALPHA, int: lookback)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`InterestRateSensitivity(obj: ALPHA, str: API_KEY)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`QuantileQuantile(obj: ALPHA, obj: BETA, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`Autocorrelation(obj: ALPHA, int: lags)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`ReturnRegressions(obj: ALPHA, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`RollingBeta(obj: ALPHA, obj: BETA, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`VAR(obj: ALPHA, int: window, float: conf)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`HoldingVAR(obj: ALPHA, int: window, float: conf)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`ETFpca(obj: ALPHA, obj: exchange, int: components, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`DynamicCTE(obj: ALPHA, obj: BETA, int: lookback, int: max)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`MCapTurnover(obj: ALPHA, obj: exchange, int: lookback)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`WklyMCT(obj: ALPHA, obj: exchange, int: lookback)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`WeekdayVolume(obj: ALPHA, obj: BETA, int: lookback, int: max)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`VolumePattern(obj: ALPHA, obj: BETA, int: lookback, int: max)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`IntradayPriceRange(obj: ALPHA, obj: BETA, int: lookback, int: max)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Building your Own
-------------------