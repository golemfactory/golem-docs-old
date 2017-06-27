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

## BOINC 
[BOINC](https://github.com/imapp-pl/golem_rd/wiki/BOINC) and [Pepesza's research on integration with Golem](https://github.com/imapp-pl/golem_rd/issues/20). Scientific calculations. 

Properties:
- Centralized Application Registry, it lists Requestors' servers, it is also trusted point: with BOINC Application Registry Providers recognize Requestors as trusted source of executable programs, it provides Requestors some kind of identity too
- Run by scientists and enthusiasts

Requirements:
- Results must be exact, usually
- It can execute with wrappers programs written in one of several technologies
- Jobs, which we call tasks or subtasks, must be taken separately, they are not grouped
- Size of Input and Output of jobs is moderate, up to megabytes or so
- Execution time of job takes up to one hour at most two
- It is also a working platform with working solutions, we must preserve it
