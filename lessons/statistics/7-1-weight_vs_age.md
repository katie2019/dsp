[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

import first

live, firsts, others = first.MakeFrames()

live = live.dropna(subset=['agepreg', 'totalwgt_lb'])ages = live.agepreg


weights = live.totalwgt_lb

def ScatterPlot(ages, weights, alpha=1.0, s=20):

    """Make a scatter plot and save it.

    ages: sequence of float
    
    weights: sequence of float
    
    alpha: float
    """
    thinkplot.Scatter(ages, weights, alpha=alpha)
    
    thinkplot.Config(xlabel='Age (years)',
                     ylabel='Birth weight (lbs)',
                     xlim=[10, 45],
                     ylim=[0, 15],
                     legend=False)
    
ScatterPlot(ages, weights, alpha=0.05, s=10)
