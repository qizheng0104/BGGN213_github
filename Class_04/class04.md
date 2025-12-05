# BGGN213 Lab04
Qingyun Zheng

``` r
#This is my first R script
x <- 1:50
plot(x)
```

![](class04_files/figure-commonmark/unnamed-chunk-1-1.png)

``` r
plot(x,type = "b", color = "green")
```

    Warning in plot.window(...): "color" is not a graphical parameter

    Warning in plot.xy(xy, type, ...): "color" is not a graphical parameter

    Warning in axis(side = side, at = at, labels = labels, ...): "color" is not a
    graphical parameter
    Warning in axis(side = side, at = at, labels = labels, ...): "color" is not a
    graphical parameter

    Warning in box(...): "color" is not a graphical parameter

    Warning in title(...): "color" is not a graphical parameter

![](class04_files/figure-commonmark/unnamed-chunk-1-2.png)

``` r
plot(x, sin(x), col = "red", type = "l", lwd = 4)
```

![](class04_files/figure-commonmark/unnamed-chunk-1-3.png)

``` r
log(10)
```

    [1] 2.302585

``` r
log(exp(1))
```

    [1] 1

``` r
log(10, base = 10)
```

    [1] 1

``` r
plot(x,log(x, base = 10), type = "l")
```

![](class04_files/figure-commonmark/unnamed-chunk-1-4.png)
