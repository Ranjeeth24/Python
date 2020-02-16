import numpy as np,pandas as pd,matplotlib.pyplot as plt
from datetime import datetime
import scipy.stats
import seaborn as sns

##importing a csv file into 
x=pd.read_csv('Sales.csv')

## craeting pandas dataframe
a={'S.no':[1,2,3,4,5],'Date':['24-11-2005','6-9-2006','3-12-2007','6-8-2008','10-10-2009'],'India_income':[12.85,20.00,22.50,26.70,28.20],
   'China_income':[15.5,17.2,19.0,20.8,23.0],'Tokyo_income':[10.0,11.8,13.5,10.2,9.0],'Kenya_income':[8.0,9.7,11.8,13.0,13.9]}
b=pd.DataFrame(a)
print(b)

##converting date column to datetime
#updated_time= datetime.datetime.strftime()
b['Date']=pd.to_dataframe(b['Date'])
b.info()

##creating stats from the above dataframe
#c=b.max('India')
#b['India_income'].max()
c=b[['India_income','China_income','Tokyo_income','Kenya_income']].max() ##max of all income columns
print(c)
d=b[['India_income','China_income','Tokyo_income','Kenya_income']].min() ##min of all income columns
print(d)
#e=b.max(axis=1)
f=b[['India_income','China_income','Tokyo_income','Kenya_income']].mean() ## mean 
print(f)
g=b[['India_income','China_income','Tokyo_income','Kenya_income']].std() ## std deviation 
print(g)
h=b[['India_income','China_income','Tokyo_income','Kenya_income']].var() ## variance of 
print(h)
i=b[['India_income','China_income','Tokyo_income','Kenya_income']].median() ##median
print(i)
j=b[['India_income','China_income','Tokyo_income','Kenya_income']].mode() ## mode
print(j)
k=b[['India_income','China_income','Tokyo_income','Kenya_income']].quantile(0.1)  ##10th percentile
print(k)
l=b[['India_income','China_income','Tokyo_income','Kenya_income']].quantile(0.2)  ##10th percentile
print(l)
#n=b[['India_income','China_income','Tokyo_income','Kenya_income']].percentile(10,interpolation='midpoint')
#print(n)
o=b[['India_income','China_income','Tokyo_income','Kenya_income']].skew()  ##finding skewness
print(o)
p=b[['India_income','China_income','Tokyo_income','Kenya_income']].kurt()  ##finding kurtosis
print(p)

## finding Pearson correlation matrix and Spearman’s Rank correlation matrix 
#seed(1)
#data1=randn(1000)
data1 =  np.random.random(1000)
data2 =  data1 +( np.random.random(1000) )

print('data1: mean=%f stdv=%f' % (np.mean(data1), np.std(data1)))
print('data2: mean=%f stdv=%f' % (np.mean(data2), np.std(data2)))
a=scipy.stats.pearsonr(data1,data2)[0]
b=scipy.stats.spearmanr(data1,data2)[0]
print( a)
print(b)
#pyplot.scatter(data1,datta2)
plt.scatter(data1,data2)
#pyplot.show()
plt.show()

##graphs using plotly 
plt.bar(x='Date',y='India_income',width=0.5,color=['red','green'])
#b.plt.bar()
plt.show()

##seaborne pairplot
z=sns.pairplot(data=b[['Date','India_income','China_income','Tokyo_income','Kenya_income']],hue='Date')
