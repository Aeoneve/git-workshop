HW 1, CS 625, Fall 2021
================
Dr. Michele Weigle
Sep 9, 2021

## Git, GitHub

1.  *What is your GitHub username?*

    **Aeoneve**

2.  *What is the URL of your remote GitHub repo (created through
    Mr. Kennedy’s exercises)?*

    **<https://github.com/Aeoneve/git-workshop>**

## R

The command below will load the tidyverse package. If you have installed
R, RStudio, and the tidyverse package, it should display a list of
loaded packages and their versions.

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.4     v dplyr   1.0.7
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   2.0.1     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

## R Markdown

1.  *Create a bulleted list with at least 3 items*

-   **Item 1**
-   **Item 2**
-   **Item 3**

2.  *Write a single paragraph that demonstrates the use of italics,
    bold, bold italics, code, and includes a link. The paragraph does
    not have to make sense.*

This is *italics*, this is **bold**, and this is ***bold italics***.
This is some code:

``` python
code = "This is code in Python"
print(code)
```

    ## This is code in Python

Lastly, click the word to find a download of [Python](http://python.org)

3.  *Create a level 3 heading*

### This is a 3rd level header

## R

#### Data Visualization Exercises

install.packages(“tidyverse”) library(tidyverse)

ggplot2::mpg

1.  (Q2) *How many rows are in mpg? How many columns?*

    **The mpg dataframe contains 234 rows and 11 columns**

2.  (Q4) *Make a scatterplot of hwy vs cyl.*

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = cyl, y = hwy))
```

![](report_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

#### Workflow: basics Exercises

1.  (Q2) *Tweak each of the following R commands so that they run
    correctly (`library(tidyverse)` is correct):*

-   “data” misspelled
-   “filter” misspelled
-   “=” should be “==”
-   “diamonds” misspelled

``` r
library(tidyverse)
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy))
```

![](report_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
filter(mpg, cyl == 8)
```

    ## # A tibble: 70 x 11
    ##    manufacturer model     displ  year   cyl trans  drv     cty   hwy fl    class
    ##    <chr>        <chr>     <dbl> <int> <int> <chr>  <chr> <int> <int> <chr> <chr>
    ##  1 audi         a6 quatt~   4.2  2008     8 auto(~ 4        16    23 p     mids~
    ##  2 chevrolet    c1500 su~   5.3  2008     8 auto(~ r        14    20 r     suv  
    ##  3 chevrolet    c1500 su~   5.3  2008     8 auto(~ r        11    15 e     suv  
    ##  4 chevrolet    c1500 su~   5.3  2008     8 auto(~ r        14    20 r     suv  
    ##  5 chevrolet    c1500 su~   5.7  1999     8 auto(~ r        13    17 r     suv  
    ##  6 chevrolet    c1500 su~   6    2008     8 auto(~ r        12    17 r     suv  
    ##  7 chevrolet    corvette    5.7  1999     8 manua~ r        16    26 p     2sea~
    ##  8 chevrolet    corvette    5.7  1999     8 auto(~ r        15    23 p     2sea~
    ##  9 chevrolet    corvette    6.2  2008     8 manua~ r        16    26 p     2sea~
    ## 10 chevrolet    corvette    6.2  2008     8 auto(~ r        15    25 p     2sea~
    ## # ... with 60 more rows

``` r
filter(diamonds, carat > 3)
```

    ## # A tibble: 32 x 10
    ##    carat cut     color clarity depth table price     x     y     z
    ##    <dbl> <ord>   <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1  3.01 Premium I     I1       62.7    58  8040  9.1   8.97  5.67
    ##  2  3.11 Fair    J     I1       65.9    57  9823  9.15  9.02  5.98
    ##  3  3.01 Premium F     I1       62.2    56  9925  9.24  9.13  5.73
    ##  4  3.05 Premium E     I1       60.9    58 10453  9.26  9.25  5.66
    ##  5  3.02 Fair    I     I1       65.2    56 10577  9.11  9.02  5.91
    ##  6  3.01 Fair    H     I1       56.1    62 10761  9.54  9.38  5.31
    ##  7  3.65 Fair    H     I1       67.1    53 11668  9.53  9.48  6.38
    ##  8  3.24 Premium H     I1       62.1    58 12300  9.44  9.4   5.85
    ##  9  3.22 Ideal   I     I1       62.6    55 12545  9.49  9.42  5.92
    ## 10  3.5  Ideal   H     I1       62.8    57 12587  9.65  9.59  6.03
    ## # ... with 22 more rows

## Google Colab

1.  *What are the URLs of your Google Colab notebooks (both Python and
    R)?*

[Python
Notebook](https://colab.research.google.com/drive/1Jqs3Dy9EzuTKX3OZEJ13c0Wz33_dWOYo?usp=sharing)

[R
Notebook](https://colab.research.google.com/drive/1fQt_NIZUjKP7UXYX63w7GklpjFzQbAil?usp=sharing)

## Tableau

*Insert your the image of your final bar chart here*

![Chart](Sales.png)

1.  *What conclusions can you draw from the chart?*

**Sales are increasing each year but Technology is especially strong**

## Observable and Vega-Lite

### A Taste of Observable

1.  *In the “New York City weather forecast” section, try replacing
    `Forecast: detailedForecast` with `Forecast: shortForecast`. Then
    press the blue play button or use Shift-Return to run your change.
    What happens?*

**The table above changes, under the “Forcast” column most of the text**
**goes away leaving only a brief explaination of the forecast**

1.  *Under the scatterplot of temperature vs. name, try replacing
    `markCircle()` with `markSquare()`. Then press the blue play button
    or use Shift-Return to run your change. What happens? How about
    `markPoint()`?*

**markSquare() changes the icons to solid squares and markPoint
changes** **the icons to hollow circles**

1.  *Under “Pick a location, see the weather forecast”, pick a location
    on the map. Where was the point you picked near?*

**I attempted to click near Philadelphia and got the coordinates**
**\[-75.87, 40.19\], which ended up being New Morgan, PA**

1.  *The last visualization on this page is a “fancy” weather chart
    embedded from another notebook. Click on the 3 dots next to that
    chart and choose ‘Download PNG’. Insert the PNG into your report.*

![Fancy Weather](weather.png)

### Charting with Vega-Lite

`markCircle()`

1.  *Pass an option of `{ size: 200 }` to `markCircle()`.*

**The circles become so large they are mostly indistinguishable**

1.  *Try `markSquare` instead of `markCircle`.*

**The large solid circles become large solid squares**

1.  *Try `markPoint({ shape: 'diamond' })`.*

**The chart becomes much nicer looking with small hollow diamonds**

`vl.x().fieldQ("Horsepower")`, …

1.  *Change `Horsepower` to `Acceleration`*

**The data moves to the upper right side of the chart from the** **upper
middle as the x-axis changes from Horsepower to Acceleration**

1.  *Swap what fields are displayed on the x- and y-axis*

**The data congregates around the middle of the chart now as the**
**axes flip and Acceleration is the y and Miles\_per\_Gallon is the x**

`vl.tooltip().fieldN("Name")`

1.  *Change `Name` to `Origin`.*

**Each data point now shows the country of origin instead of the**
**name of the car when you hover over it**

Another example, `count()`

1.  *Remove the `vl.y().fieldN("Origin")` line.*

**All the data gets combined into one count and the y axis is removed**

1.  *Replace `count()` with `average("Miles_per_Gallon")`.*

**The average of all the combined data is computed and displayed** **on
the x-axis as a bar chart**

## References

*Every report must list the references that you consulted while
completing the assignment. If you consulted a webpage, you must include
the URL.*

-   <https://classroom.github.com/>
-   <https://github.com/>
-   <https://git.cs.odu.edu/tkennedy/git-workshop/-/wikis/Git-Workshop>
-   <https://www.rstudio.com/>
-   <https://github.com/odu-cs625-datavis/github-classroom-for-students/blob/master/README.md>
-   <https://r4ds.had.co.nz/>
-   <https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>
-   <https://colab.research.google.com/>
-   <https://www.tableau.com/learn/tutorials/on-demand/getting-started>
-   <https://www.earthdatascience.org/courses/earth-analytics/document-your-science/add-images-to-rmarkdown-report/>
-   <https://observablehq.com/>
