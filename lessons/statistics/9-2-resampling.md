[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)


class DiffMeansResample(DiffMeansPermute):

    """Tests a difference in means using resampling."""
    
    def RunModel(self):
    
        """Run the model of the null hypothesis.

        returns: simulated data
        """
        
        group1 = np.random.choice(self.pool, self.n, replace=True)
        
        group2 = np.random.choice(self.pool, self.m, replace=True)
        
        return group1, group2

def RunResampleTest(firsts, others):

    """Tests differences in means by resampling.

    firsts: DataFrame
    
    others: DataFrame
    """
    
    data = firsts.prglngth.values, others.prglngth.values
    
    ht = DiffMeansResample(data)
    
    p_value = ht.PValue(iters=10000)
    
    print('\ndiff means resample preglength')
    
    print('p-value =', p_value)
    
    print('actual =', ht.actual)
    
    print('ts max =', ht.MaxTestStat())

    data = (firsts.totalwgt_lb.dropna().values,
            others.totalwgt_lb.dropna().values)
            
    ht = DiffMeansPermute(data)
    
    p_value = ht.PValue(iters=10000)
    
    print('\ndiff means resample birthweight')
    
    print('p-value =', p_value)
    
    print('actual =', ht.actual)
    
    print('ts max =', ht.MaxTestStat())
    
RunResampleTest(firsts, others)
