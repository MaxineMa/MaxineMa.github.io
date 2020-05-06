Mediocre Social Network Apps Incorporated Has Had a Rocky Couple of Years, Stock Price Seemingly Settling Down
--------------------------------------------------------------------------------------------------------------

*By Adele Shen, Jane Zhang, and Maxine Ma*

 

Mediocre Social Network Apps Incorporated has seen plummeting stock prices since
January 2015, when it IPOed on January 2nd at a lofty \$39.02. The excitement
lasted into the following week, when the share price climbed to \$39.78. This
would end up to be Mediocre Apps’ highest recorded price to date, as the company
quickly hopped on a near-linear decreasing track in the following years, hitting
a \$20.48 share price on September 30, 2019. In the same month a few weeks back,
September 6, 2019, the market closed with Mediocre Apps at its lowest stock
price ever, \$19.30.

![](https://lh5.googleusercontent.com/exPFTJWHi6_HsvVg_kJnY5CYr0p1xO5tFbwZdFHGxI0WwsGbzOIi1xJmiN3nML_nmrxJ1CPX3mmytLV_FR8ldIQy7oScMLBLYu6usoZwSbyF-NKTEw-shxhkRWNzrf-5IYqByDiY)

 

**We want to see where this crashing and burning company is headed, so we set
out to forecast its stock prices for the next 10 days. **

 

However, this set of market data obviously would not include data points on days
the market was closed: weekends and holidays. To remedy this, we generated from
the original data a “padded” dataset using splines, which is a form of
interpolation using polynomials. In this way, we would be adding plausible data
points to the missing days, making it easier to interpret and forecast the data
as a time series, without falsely diminishing the variability of the data in a
way that other methods like averaging would have. For example, a spline follows
a piecewise polynomial function to generate points for Saturday and Sunday
between Friday and the following Monday, while another method might have just
picked the weekend points out of a straight line connecting Monday and Friday,
flattening variability.

 

Now that we had a more complete dataset to work with, our goal was to strip the
data of all distinguishing features until it was a white noise process (one can
think of it as values of random error about 0 with finite variance) that we
could then rebuild in order to forecast future stock prices. We wanted to make
the magnitude of the variability fairly even across time, get rid of any trend
(clearly downward in Mediocre Apps’ case), get rid of possible seasonality. This
is to make sure that the data is stable: the average value of the data became 0,
and the data was evenly variable across time. After it’s stable, we want to turn
it into white noise by making sure that the data points are uncorrelated with
each other. Working with a time series, in which the data points are all from a
single source, just collected at different points in time, this is unlikely, so
we employ tools to make sure that the correlation between points is under some
acceptable interval.

 

**The Nitty-Gritty**

 

Upon seeing that the first half of the data had up and downs at a much larger
magnitude than the second half, we stabilized the variance by taking the log of
the price. This essentially squishes the magnitude of the values down so that
the variability is a little more uniform, not quite so different as time goes
on.

 

To remove the trend of the data points over time, we fit a linear regression
model, creating an equation where the (logged) stock price of Mediocre Apps
equaled a function of 2 variables: time and time squared. This model
appropriately captured the data because it captured the trend well without
getting bogged down by the relatively inconsequential, daily ups-and-downs of an
inherently ever-changing market.

![](https://lh5.googleusercontent.com/5wqt6ugjn7zl23rQlLVLS6tavsMzF8gb4cGyw0mt0_8idCR5htqCB0BW6Y_Wvn7Ar7QSn0M31KcuDIjwcOQeBC3uhni_kc6U0PO-U8LTau6oGgHkXnYXiysr3xe_p-_Sm3owT0Xu)

When we looked at the residuals (the error left over from our model that we
wanted to look stable), it did in fact look stable. To turn this stable process
into white noise, we looked at plots of the correlations between data points
until we could capture a function that described them. What was left was now,
truly, white noise: a series of uncorrelated random variables about 0 with some
finite variance.

**The Fun Part (the results!)**

![](https://lh5.googleusercontent.com/nNOhrKorj8CndmBdvcZ1PshmIAgrsuHgTRJzZ_3F1oOFbF4HWMKTmkN7OBg7kJ60iUvnd3GEW5LjFiUbMvmyM0kY2ygcZFzEZQhtuXSZAz6FOYCoxSQXXI60rP5aiV8XWmBTtXsZ)

![](https://lh3.googleusercontent.com/Wr45BNSNA4T3sJNlUpk_e3yl2Oa6x-w7h8fAewLwW23mpX9qNE2jNXT-msviGkzZbwvof_5qWhHOy1dazhi6xQ2i_rMR6XlguoeCvO8nylCGdMOSquJRKbtIs81AsCClQNhEn1uj)

Using our model, we forecasted the stock price of the next 10 trading days.
Above, we’ve shown you the plot starting at day 1461, the first day of 2019, so
that you can clearly see the tiny data points that we’ve forecasted. 

 

Fortunately for Mediocre Social Network Apps, it predicts that the company’s
stock price will pick up, but only by about 17 cents, listing October 14 as
being \$20.65 when the market closes. 

 

Experts hesitate to say that this is indicative of an improvement in the
operations of Mediocre Apps, as such a small change could easily be nothing more
than the rumblings of an ever-changing market. Although for Mediocre Apps, stock
prices not declining may be the best news they can hope for at the moment.  
