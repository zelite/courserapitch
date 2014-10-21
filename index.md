---
title       : The shortest tour
subtitle    : 
author      : zelite
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---


## Motivation

* You´re planning your next holiday around europe?
* You want to take full advantage of your holiday time?
* You want to minimize the time you spend moving from city to city?

## There´s an app for that!



--- .class #id 

## How does it work?

1. Select the cities you want to visit (limited city choices in this beta version)
2. Select in which city you want to start your trip.
3. Our super amazing algorithms find you the shortest trip through all the cities!
  + You don´'t visit the same city twice.
  + You come back to the city where you began.

## Tell me more!

The *traveling salesman problem* is a classical computer science problem. Learn more here: http://en.wikipedia.org/wiki/Travelling_salesman_problem

The package [TSP](http://CRAN.R-project.org/package=TSP) provides solvers for this complex problem. And this app provides you a friendly interface to interact with the solver!

Given a matrix of distances and a starting city, the TSP solver gives you the shortest path that does not cross the same city twice.

---

## Let´s look at a bit of code!


```r
library(TSP)
data(eurodist) ## dataset with distances between several european cities
tsp_object <- TSP(as.matrix(eurodist)) ## we need a special TSP object
path <- solve_TSP(x = tsp_object,method = "nn", control = list(start=1))
names(path) # Gives the order of the path
```

```
##  [1] "Athens"          "Rome"            "Milan"          
##  [4] "Lyons"           "Geneva"          "Marseilles"     
##  [7] "Barcelona"       "Madrid"          "Lisbon"         
## [10] "Gibraltar"       "Paris"           "Calais"         
## [13] "Brussels"        "Hook of Holland" "Copenhagen"     
## [16] "Hamburg"         "Cologne"         "Munich"         
## [19] "Vienna"          "Cherbourg"       "Stockholm"
```

```r
attributes(path)$tour_length #Gives the length of the path (km)
```

```
## [1] 17353
```



---
## Room for improvement

1. This app currently only calculates distances in straight line: by using a online service like google maps the road distances could be used instead.
2. Instead of distances, maybe it would be interesting to use cost of travel between cities and calculate cheapest trip (we all know how crazy airline prices are.)
3. The plotting of the tour is a bit clumbsy. Fancier plotting should be made!

Thanks for watching this presentation! Hope you liked it!





