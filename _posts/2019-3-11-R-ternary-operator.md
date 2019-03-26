As a problem in my Bayesian Statistics Homework, I was asked to find an example where the posterior variance is larger than the prior distribution. I decided to write R code to solve it.

When writing my code, I need to compare the two calculated variances in a fucntion. Firstly, I write as below:

```
If (prior.var(a,b) < post.var(a,b)){return(1)}
return(0)
```

I aware that it's not brief immediatly, so I rewrite it:

```
return(as.inteer(prior.var(a,b) < post.var(a,b)))
```

## `ifelse(test, yes, no)`

At that moment, I thought of whether there is a " ? : " operator in R. After a failed try, I searched it on Google.
![Failed try](/images/posts/2019-3-11-R-ternary-operator-1.png)

And I found that the built-in "ternary operator" of R is `ifelse(test, yes, no)`, which does have the similar function with `? :`.

## More

Moreover, A definition of C-style `? :` R-function is given in [this stack overflow post](https://stackoverflow.com/questions/8790143/does-the-ternary-operator-exist-in-r).

```
`?` <- function(x, y)
    eval(
      sapply(
        strsplit(
          deparse(substitute(y)), 
          ":"
      ), 
      function(e) parse(text = e)
    )[[2 - as.logical(x)]])
```

It's a function with only one line function body.

The most inner function `substitute(expr, env)` returns the parse tree for the expression expr, substituing any variables bound in env. Briefly, it parse the part after `?`. And `deparse()` turns unevaluated expresion into character strings， in order to facilitate the subsequent operations.

`strsplit(x, split)` splits the elements of a character vector x into substrings according to the matches to substring `split` within them.

`sapply()` is a useful broadcasting function in R. `function(e) parse(text = e)` is the broadcasted functoin on the two strings before and after `:`, it helps to transform the string expression to its exace result.

Finally the `sapply()` returns a vector of two expressions which is stated before and after `:`. And we use `[2 - as.logical(x)]` to determine which is selected at last. `2 - as.logical(x)` tells us whether the index choosen is 1 (x is true) or 2 (x is false).

The outer `eval()` evaluate the choosen expression and returns the final result.

I have to say that this fucntion is excellent.

## Recently 

The new semester (second half of my junior year) has startred for 3 weeks. 

In the past 3 months, I realized an online [Jupyter notebook](http://119.29.186.218:6060) on my cloud server by docker, in which I learnt alot about docker and the computer networks.

This weekend, I will participate TOEFL second time, good luck to me.

A good news: The Department of Statistics will be established officialy in September. Maybe I will be graduate student of the first session in SUSTech Statistics Department :)
