---
layout: page
bigimg: /img/pubg3.jpeg
---
## Feature Engineering

## Explore The Pearson Correlation Graph

![GW Data Science logo](/img/image_13.png)

1). Variables "winPoints", "killPoints" and "rank" points are highly correlated variables, and as a matter of facts, they represents the same number, therefore, drop two of the variables and leave one

2). Variables "maxPlace" and "numGroup" are the variables that have the same values, therefore, drop one of them

## Create New Features

1). Create new feature "totalDistance" which represents the total distance travelled by a player

```
data['totalDistance'] = data['walkDistance'] + data['swimDistance'] + data['rideDistance']
```
2). Create new feature "healsAndBoosts" which is the total medical items used by a player

```
data['healsAndBoosts'] = data['heals'] + data['boosts']
```

3). Create new feature "headShotRate". Headshot rate is a good indicator of professional player

```
data['headshotRate'] = data['headshotKills'] / data['kills']
```

## Find The Cheaters

There are always cheaters in PUBG, and it is possible to find them using some feature engineering skills

1). Create new variables "killsWithMoving", if a player has "kills" > 0 and "walkDistance" = 0, he must be a cheater

```
data['killsWithoutMoving'] = ((data['kills'] > 0) & (data['totalDistance'] == 0))
data[data['killsWithoutMoving'] == True].shape
```
It turns out there are 1535 players kill with moving.

2). Find the cheater using 100% headshot rate.

If a player has 100% headshot rate, and has kills over 10, he might be a cheater

```
(data[(data['headshotRate'] == 1) & (data['kills'] >=10)]).shape
```
There are 24 players qualify this condition

Drop all cheater from the dataset

## Normalize The Features
Usually a match has 100 players, but some matches are not full

![GW Data Science logo](/img/image_14.png)

Create a variable "playersJoined" and normalize some important features

```
data['killsNorm'] = data['kills']*((100-data['playersJoined'])/100 + 1)
data['damageDealtNorm'] = data['damageDealt']*((100-data['playersJoined'])/100 + 1)
```





