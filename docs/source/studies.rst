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

:code:`Autocorrelation(obj: ALPHA, int: lags)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`CumulativeReturn(obj: ALPHA, obj: BETA, int: period, bool: vol_match)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`CalendarPerformance(obj: ALPHA, str: freq)`
++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`DynamicCTE(obj: ALPHA, obj: BETA, int: lookback, int: max)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`Hurst(obj: ALPHA, int: lags)`
+++++++++++++++++++++++++++++++++++++

:code:`InterestRateSensitivity(obj: ALPHA, str: API_KEY, str: mode)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`InterestSensitivityDuration(obj: ALPHA, str: API_KEY)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`ETFpca(obj: ALPHA, obj: exchange, int: components, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`QuantileQuantile(obj: ALPHA, obj: BETA, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`ReturnRegressions(obj: ALPHA, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`RollingBeta(obj: ALPHA, obj: BETA, int: window)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`SessionTurnover(obj: ALPHA, obj: exchange, bool: normalise)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`VWAP(obj: ALPHA, obj: exchange, bool: normalise)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`OpenVolume(obj: ALPHA, obj: exchange, bool: normalise)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`CloseVolume(obj: ALPHA, obj: exchange, bool: normalise)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`DecompSTL(obj: ALPHA, int: period)`
+++++++++++++++++++++++++++++++++++++++++++

:code:`RollingSharpe(obj: ALPHA, int: lookback)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`LinearRegression(obj: ALPHA, obj: BETA)`
++++++++++++++++++++++++++++++++++++++++++++++++

:code:`CTExplorer(obj: ALPHA, obj: BETA, int: lookback, int: multi)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

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

:code:`MCapTurnover(obj: ALPHA, obj: exchange, int: lookback)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`WklyMCT(obj: ALPHA, obj: exchange, int: lookback)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`VAR(obj: ALPHA, int: window, float: conf)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`HoldingVAR(obj: ALPHA, int: window, float: conf)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`WeekdayVolume(obj: ALPHA, obj: BETA, int: lookback, int: max)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`VolumePattern(obj: ALPHA, obj: BETA, int: lookback, int: max)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`IntradayPriceRange(obj: ALPHA, obj: BETA, int: lookback, int: max)`
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`NormalisedAccumulation(obj: ALPHA, obj: feed, int: days, int: norm)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

:code:`VolumeParticipation(obj: ALPHA, obj: feed, int: days, int: units)`
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Building your Own
-------------------