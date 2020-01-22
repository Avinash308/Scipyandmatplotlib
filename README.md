# Scipyandmatplotlib
Scipy: We have the min and max temperatures in a city In India for each months of the year. We would like to find a function to describe this and show it graphically, the dataset given below. Task: 1. fitting it to the periodic function 2. plot the fit Data Max = 39, 41, 43, 47, 49, 51, 45, 38, 37, 29, 27, 25 Min = 21, 23, 27, 28, 32, 35, 31, 28, 21, 19, 17, 18

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline

Max=np.array([39, 41, 43, 47, 49, 51, 45, 38, 37, 29, 27, 25])
Min=np.array([21, 23, 27, 28, 32, 35, 31, 28, 21, 19, 17, 18])
months=np.arange(1,13)

plt.plot(months,Max,'ro')
plt.plot(months,Min,'bo')
plt.xlabel('months')
plt.ylabel('Max and min temperatures')

#fitting it to a periodic functions

from scipy import optimize
def yearly_temps(times, avg, ampl, time_offset):
    return (avg
            + ampl * np.cos((times + time_offset) * 1.8 * np.pi / times.max()))

res_max, cov_max = optimize.curve_fit(yearly_temps, months,
                                      Max, [40, 20, 0])
res_min, cov_min = optimize.curve_fit(yearly_temps, months,
                                      Min, [-40, 20, 0])
                                      
#plotting the fit

days = np.linspace(0, 12, num=365)

plt.figure()
plt.plot(months, Max, 'ro')
plt.plot(days, yearly_temps(days, *res_max), 'r-')
plt.plot(months, Min, 'bo')
plt.plot(days, yearly_temps(days, *res_min), 'b-')
plt.xlabel('Month')
plt.ylabel('Temperature ($^\circ$C)')

plt.show() 

#Matplotlib
#creating pie chart using male female proportion
labels=['male','female']
sizes=Titanic.sex.value_counts()
fig1,ax1=plt.subplots()
ax1.pie(sizes,labels=labels,autopct='%1.1f%%',colors=['Blue','Red'])


#creating scatter plot using fare paid and age differ the plot color by gender

plt.figure()
category1=Titanic[Titanic.sex=='male'].plot.scatter('age','fare',color='red',label='male')
Titanic[Titanic.sex=='female'].plot.scatter('age','fare',color='blue',label='female',ax=category1)









