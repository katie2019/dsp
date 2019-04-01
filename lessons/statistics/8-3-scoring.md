[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

def SimulateGame(lam):

    """Simulates a game and returns the estimated goal-scoring rate.

    lam: actual goal scoring rate in goals per game
    """
    
    goals = 0
    
    t = 0
    
    while True:
    
        time_between_goals = random.expovariate(lam)
        
        t += time_between_goals
        
        if t > 1:
        
            break
            
        goals += 1

    # estimated goal-scoring rate is the actual number of goals scored
    
    L = goals
    
    return L
    


def Estimate6(lam=2, m=1000000):

    estimates = []
    
    for i in range(m):
    
        L = SimulateGame(lam)
        
        estimates.append(L)

    print('Experiment 4')
    
    print('rmse L', RMSE(estimates, lam))
    
    print('mean error L', MeanError(estimates, lam))
    
    pmf = thinkstats2.Pmf(estimates)
    
    thinkplot.Hist(pmf)
    
    thinkplot.Config(xlabel='Goals scored', ylabel='PMF')
    
Estimate6()
