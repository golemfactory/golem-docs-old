# Golem Business Use Cases

In this document there are listed use cases that Golem is supposed to support or not. No details are given, just overview. The purpose is to point out main requirements, to categorize nd define areas of interest.

## Stock Market Backtester
Argentinian Economist want to use Golem in stock market analysis. There are one file per day called Tape that contains every tick for every market symbol. He want to test buy/sell strategies on historical data. Such test is called backtest.

Requirements:
- Tapes are kept in Golem Network
- multiple users (clients) test their strategies from random locations
- new Tapes must be inserted into network, possibly by central server
- number and size of Tapes?
- strategies takes form of small programs executed only on Tapes
- there is no connection between calculations on adjacent Tapes (days), in other words are network operation needed?
- what is CPU consumption for single backtest?

