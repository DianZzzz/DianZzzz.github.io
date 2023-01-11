Visualization
import matplotlib.pyplot as plt
df = pd.read_csv("https://raw.githubusercontent.com/fivethirtyeight/data/master/college-majors/recent-grads.csv")
# histogram
fig, (ax1, ax2) = plt.subplots(nrows=1,
                               ncols=2,
                               sharey=True,
                               figsize=(10, 4))

df['Median'].hist(ax=ax1,bins = 20)
df['Median'].plot(ax=ax2, kind = 'hist',bins = 20)
ax1.set_xlabel('MPG')
ax1.set_ylabel('Number of cars')
Text(0, 0.5, 'Number of cars')

#sns histogram

import seaborn as sns
sns.set_style("white")
sns.set(style = "ticks")

ttbill = sns.distplot(df['Median'])
ttbill.set(xlabel = 'Value', ylabel = 'Frequency', title = "Total Bill")
sns.despine()

# line plot; plt.plot(x,y)
plot(df["Rank"], df["P75th"])
[<matplotlib.lines.Line2D at 0x1e5c4b39fd0>]

df[['Men', 'Women']].plot(subplots=False, figsize=(8, 4))
<AxesSubplot:>

#bar
top_5 = df.sort_values(by="Median", ascending=False).head()
top_5.plot(x="Major", y="Median", kind="bar", rot=5, fontsize=4)
<AxesSubplot:xlabel='Major'>

top_medians = df[df["Median"] > 60000].sort_values("Median")
top_medians.plot(x="Major", y=["P25th", "Median", "P75th"], kind="bar")
<AxesSubplot:xlabel='Major'>

#scatterplot
plot(df["Median"], df["Men"],marker='o',color='blue',linestyle='None',label='men')
plot(df["Median"], df["Women"],marker='o',color='red',linestyle='None',label='women')
xlabel('Median')
title("Unemployment_rate")
legend(numpoints = 1, loc='best')
show()

marker = 's' #square
marker = 'p' #pentagons
market = '.' #points
marker = 'None' #no marker

linestyle = '-' #plain line
linestyle = '--'#dashed line
linestyle = '-.'

df.plot(x="Median", y="Unemployment_rate", kind="scatter")
<AxesSubplot:xlabel='Median', ylabel='Unemployment_rate'>

#sns scatterplot
sns.stripplot(x = "Men", y = "Women",
              hue = "Major_category",
              data = df.iloc[:20,:])
<AxesSubplot:xlabel='Men', ylabel='Women'>

# zoom in
plt.xlim(-40,2000)
plt.ylim(-1,80)
# pairwise
sns.pairplot(df)
