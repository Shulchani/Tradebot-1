# Tradebot-1

Hello! I am Shulchani. This is my first trading algorithm. The plan is to make a trading bot that trades US stocks. I will do so by defining the strategy, coding it, testing it and analyzing it, and refining it as future prototypes!

Strategy Outline:
A random stock will be chosen through the Alpaca API. This is to ensure I don't use an algorithm that searches for stocks with the greatest drop in value. If I did that I fear I would face diversification risk in the chance a sector has a massive drop in value and I invest my whole portfolio in it and lose all my money. I believe randomly choosing a stock and analyzing it before choosing to buy is a safer option. In the future I plan to make a system that weights the stocks in my portfolio by industry sector according to what part of the business cycle the USA is in using macroeconomic analysis.
Once a random stock is picked, I will compare its 25 day moving average (calculated using historical data from the Alpaca API) to its current buy price. If it drops below 20% of its 25 day moving average it passes onto the next stage of analysis, if not a new stock is randomly chosen. In the future instead of having a flat 20% be chosen, I would define a function based on its sector beta (because some sectors are more stable like constructions, and others like biotech are more volatile).
Then I will attempt to buy the dip by using a function based on data from the Alpaca API to determine when the large volume sell orders stop and buying orders begin. This is to ensure I do not buy the stock as it is descending in price.
2% of my current allocated capital will be directed into this trade in order to be conservative with my funds. The take profit and stop loss orders will be defined by taking the stocks ATR and muliplying it by a constant (that varies based on the time of day the order occurs due to mornings and evenings having higher volatility) and adding or subtracting it, respectively, from the price it was bought at. This specific position will be held overnight if and only if the current listing price is a defined percentage above the bought price. If this threshold is not met, the position is liquidated whether it is minor profit or loss in order to minimize overnight risk.
This program is looped infinitely, as such multiple positions may be open at once.

Coding:
The program will be writen in Python and the data/order API used is the Alpaca API

Testing:
This algorithm will be tested on historical 2010-2025 data and a 2026 dataset. Once testing is complete, I will analyze its risk adjusted performance through the omega ratio. The omega ratio is chosen over the Sharpe ratio because the omega ratio does not discriminate against volatility that results in gains from going long.

Refining:
If my program does not "beat" the S&P 500, I will adjust the strategy and code until the best version of the bot I can make at my disposal is made. Beating the S&P 500 is defined as beating the S&P 500's omega ratio of approximately 1.49.