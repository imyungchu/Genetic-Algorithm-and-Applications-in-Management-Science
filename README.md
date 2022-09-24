# Genetic Algorithm and Applications in Management Science Course and Project

###### tags: `109下` `Industrial Engineering` `project` `Python` `course` `heuristic algorithm` `GA` `VRP`

✏️This note record our project and course materials of the NCTU course [Genetic Algorithm and Applications in Management Science](https://timetable.nycu.edu.tw/?r=main/crsoutline&Acy=109&Sem=2&CrsNo=1491&lang=zh-tw) in 2021 spring（109下學期）🏫 

## Final Project about Stock Portfolio Optimization Using Genetic Algorithm 

### Overview : The quick guide of the project

Copyright© of the project is belonged to our Project Member： Chen,Chun-yi Huang,I-Chen. Note that no one shall download, reprint, reproduce, distribute, publicly broadcast, publish or distribute the research content of our project research in any form without written consent.
Data downloaded from TEJ database as follows: https://drive.google.com/drive/folders/11pX59V9ezz417V02eqNrfNuHKpl2MKhX?usp=sharing
### Project 

#### 1. Research method

- Figure 1.  Schematic diagram of the research process
![](https://i.imgur.com/iwNHnhd.png)


This research collects stock prices from January 3, 2017 to May 21, 2021 from the TEJ database as the input data to optimize the portfolio with genetic algorithm. This experiment uses discrete row coding Carry out, select 100 groups of investment portfolios, which means 100 chromosomes, 20 stocks as units, that is, the chromosome length is 20, take a random number within the range of 20 as a chromosome, and optimize the genetic algorithm.

In the fitness function part, set a stock weight (wi) as the proportion of each stock price in the total price of the portfolio, calculate the variance of the portfolio,

![](https://i.imgur.com/E214EDn.png)

and the return rate of the portfolio is the weight of each stock multiplied by The total return rate of each stock is calculated, and the total price is the sum of the stock prices of 20 stocks.


This study is designed with three oriented penalty terms to avoid the problems of exceeding the budget of 1 million, the standard deviation of the return rate being too large, and selecting too many duplicate stocks. In the cost part, if it exceeds 1 million, the penalty item is2* (total cost-1000)/1000, hoping to control the cost of the combination within the range. The penalty term of the standard deviation is composed of (np.sqrt(total_var)-min_std)/(max_std-min_std). Finally, in order to avoid selecting too many identical stocks, set NUM_BIT - len(np.unique(x) ), to control the problem of stock duplication. Finally, according to the different weight ratios (return rate, cost, risk), the fitness function is calculated, which is :

>
    Total rate of return * rate of return ratio 
    - risk penalty term * risk proportion 
    - cost penalty term * cost proportion 
    - 0.1 * penalty term for repeated stock selection


Last but not least , in the target check, this research will visualize the results, which will make effective investment The portfolio, i.e. the rate of return that yielded the best results within the research range, was compared with the daily broad-market returns over the period and tested the portfolio from January 1, 2020 to May 21, 2021 Effect.


#### 2. Experiment setting The setting
The experiment setting of this experiment is to buy 20 stock portfolios with 1 million of capital. It will be considered in three aspects and divided into three aspects of weight (a, b, c). First, a is the weight of the rate of returnitem, which means the degree of emphasis on profit, then b is the weight item of cost, that is, the difference between the cost of the portfolio and1million, and  c is the weight item of risk, that is, the standard deviation of the rate of return, and the standard deviation of the rate of return refers to The size of the volatility of the stock, so if you want the portfolio to be more stable and less risky, the weight will be higher.

此實驗之設定為將100萬元的資本買20檔股票投資組合，會以三個面向來做考量，分成三個面向的權重(a,b,c)，首先 a 是報酬率之權重項，意即重視獲利的程度，接著 b 是成本之權重項，即組合成本與100萬的差距，最後 c 是風險之權重項，即報酬率的標準差，而報酬率的標準差就指股票波動的大小，因此若希望投資組合能夠越穩定，面對的風險越小的話，權重就會越高。

#### 3. Experimental results

![](https://i.imgur.com/NEuyjL6.png)

There is a straight line in the figure above. The left half of the straight line is the data of running the genetic algorithm, which is the rate of return of each stock from 2018 to 2020, and the right half is the rate of return from 2020 to the present. This data Used to observe the effectiveness of our genetic algorithm to run the portfolio.

This experiment is divided into three different weight combinations to run the genetic algorithm. First of all, the red line is the rate of return of the broader market, and the weight of the blue line is (3,1,1). It can be seen that the blue line is the most demanding rate of return and has the smallest risk ratio among the three portfolios, so its risk Tolerance is the highest. The orange line has a weight of (3, 1, 3), which means it not only seeks return, but also pays more attention to risk than the blue line. The weight of the green line is (2, 1, 3), that is, it attaches the most importance to risk, and among the three lines, its risk tolerance is the lowest.

From the experimental results, it is found that no matter which combination is used, the return rate is higher than that of the broader market. Looking at the right half of the black line in vertical section, it is found that the blue line has the best overall return, the orange line is the second best, and finally the green line. In terms of portfolio weight, both the blue line and the orange line have three returns, but the orange line has a higher risk weight than the blue line, so the overall return is not as good as the blue line, but at the same time, when it falls in 2021, the decline Also smaller than the blue line. The green line has the highest risk ratio among the three portfolios. Perhaps he pays more attention to the stability of the portfolio than profit, so the overall return rate is relatively low, and the decline in 2021 is also the smallest.

#### 4. Conclusion

This experiment uses the genetic algorithm to run the investment portfolio, and the results of the above set of experiments are in line with our expectations, so it is considered that the genetic algorithm to run the investment portfolio has potential. At the same time, in the experiment, we also tried different weight combinations and found that this experiment has room for improvement. Therefore, if this project is to be practically applied in the stock market and provide investors with a basis for reference, it is necessary to invest in improvement in the future. , for example, in the setting of rate of return and risk, the absolute rate of return and standard deviation were originally used to score, but we later observed the results of the experiment and found that this is not good, because rate of return and risk are actually relative, so maybe it will be better to change to a relative sharpe ratio.

本實驗是以基因演算法來跑投資組合，而上面這組實驗的結果是符合我們預期的，因此認為以基因演算法跑投資組合是有潛力的。同時在實驗中，我們亦嘗試了不同組權重組合後，發現此實驗是改善的空間，因此若要將本專案實際應用在股市上，提供投資人參考的依據的話，在往後還需要投入改進，像是在報酬率與風險的設定，原本是用絕對的報酬率跟標準差去評分，但我們後來觀察實驗的結果發現這樣做並不好，因為報酬率跟風險其實是相對的，因此或許可以改成相對的sharp ratio會更好。

## :notebook_with_decorative_cover: (Wrong link now) The Homeworks of the course 

Copyright© The homeworks and teaching materials is provided by the professor of the course,, and the answers in some code blocks is added by me.

| Homework : Grade   |  link              | 
| ----------------- |:----------------------- |
| Lab0 :Python basis | [:link:][6]|
| Lab1 :Genetic Algorithm，GA  | [:link:][1]  |
| Lab2 :Assignment Problem  | [:link:][2]  |
| Lab3 :Traveling Salesman Problem | [:link:][3]    | 
| Lab4 :Flow Shop Scheduling    | [:link:][4]     |
| Lab5 :Job Shop Scheduling | [:link:][5]     |
| Lab6 :Facility Location Problem | [:link:][6]|
| Lab7 :Packing Problem | [:link:][6]|
| Lab8 :Vehicle Routing Problem | [:link:][6]|
| Lab9 :Supply Chain Optimization| [:link:][6]|
    


[1]: https://github.com/imyungchu/Programming-course-and-project/tree/main/HW/HW1

[2]: https://github.com/imyungchu/Programming-course-and-project/tree/main/HW/HW2

[3]: https://github.com/imyungchu/Programming-course-and-project/tree/main/HW/HW3

[4]: https://github.com/imyungchu/Programming-course-and-project/tree/main/HW/HW4

[5]: https://github.com/imyungchu/Programming-course-and-project/tree/main/HW/HW5

[6]:https://github.com/imyungchu/Programming-course-and-project/tree/main/HW/HW6







- Watch MORE of my projects ➜ [My GitHub repositories](https://github.com/imyungchu?tab=repositories)

