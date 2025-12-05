# Class 6: R Functions
Qingyun Zheng (PID:A16338254)

- [Our first (silly) function](#our-first-silly-function)
- [Our second function](#our-second-function)
- [A protein generating function](#a-protein-generating-function)

All functions in R have at least 3 things:

- A **name**, we pick this and use it to call our function,
- Input **arguments** (there can be multiple)
- The **body** lines of R code that do the work

## Our first (silly) function

Write a function to add some numbers

``` r
add <- function(x,y=1) {
  x+y
}
```

Note: The y=1 means that if we don’t provide a value for y, it will
default to 1.

Now we call this function:

``` r
add(5,10)
```

    [1] 15

``` r
add(5)
```

    [1] 6

Input values as vectors

``` r
add(c(10, 10, 100))
```

    [1]  11  11 101

``` r
add(c(10, 10), 100)
```

    [1] 110 110

## Our second function

Write a function to generate random nucleotide sequencesof a user
specified length

The `sample()` function can be helpful here

``` r
sample(c("A","T","G","C"), size = 50, replace = TRUE) 
```

     [1] "A" "G" "A" "C" "C" "C" "A" "C" "G" "A" "T" "G" "G" "A" "C" "A" "T" "G" "G"
    [20] "T" "A" "A" "G" "T" "C" "T" "T" "C" "C" "T" "A" "C" "T" "G" "G" "A" "G" "G"
    [39] "T" "T" "A" "T" "A" "C" "C" "T" "G" "G" "T" "T"

\*Replace = TRUE fixes the size issue

I want the a 1 element long character vector that looks have no gaps
like “ATCGCTA”

``` r
v <- sample(c("A","T","G","C"), size = 50, replace = TRUE) 
paste(v, collapse = "")
```

    [1] "TTGTAGGTGATTAAATATTCCCCTTAAGGGCGCTAATCGAGTGCCGTCGG"

\*The paste(x, collapse = ““) function removes the gap

Turn the above into a function that takes input length and generates
nucleotide sequence of that input length

``` r
generate_DNA <- function(x){
  v <- sample(c("A","T","G","C"), size = x, replace = TRUE)
  paste(v, collapse = "")
}
```

Callling the function above

``` r
generate_DNA(20)
```

    [1] "TGCCAAACATCTCTCTGTAG"

The if statement has the following structure:

``` r
if(TRUE){
  cat("HELLO you!")
} else{
  cat("No you don't")
}
```

    HELLO you!

Add the ability to return a multi-element vector or a single element
fasta like vector

``` r
generate_fasta <- function(size = 50, fasta = TRUE){
  v <- sample(c("A","T","G","C"), size = size, replace = TRUE)
  s <- paste(v, collapse = "")
  
if(fasta){
  return(s)
} else{
  return(v)
}
}
```

``` r
generate_fasta(10, fasta = FALSE)
```

     [1] "A" "G" "C" "T" "A" "G" "G" "T" "G" "G"

``` r
generate_fasta()
```

    [1] "TAAAACTAATGAACGCCATCTGCATTAGTGAACAGCCCTAGATGCCTGTT"

``` r
generate_fasta(10)
```

    [1] "CATTAAGTTC"

## A protein generating function

``` r
generate_protein <- function(size = 50, fasta = TRUE){
  aa <- c("A","R","N","D","C","Q","E","G","H","I",
          "L","K","M","F","P","S","T","W","Y","V")
  v <- sample(aa, size = size, replace = TRUE)
  s <- paste(v, collapse = "")
  
  if(fasta){
    return(s)
  } else{
    return(v)
  }
}
```

``` r
generate_protein(60)
```

    [1] "FCIDTNMDCMDRPCEMATMFTFMYWSVLHFRCIQTDRSGTNSPQMGDCFMHNDAACMAWY"

Use our new `generate_protein()` function to make random protein
sequences of length 6 to 12 (i.e. one length = 6, one length = 7…)

Using `for` loop

``` r
lengths <- 6:12
for (i in lengths){
  cat(">",i, sep = "")
  cat("\n")
  aa <- generate_protein(i)
  cat(aa)
  cat("\n")
}
```

    >6
    PDQFKP
    >7
    SLSAVAD
    >8
    TWEGMEDW
    >9
    WEESWAQVR
    >10
    FCWSDSRHKV
    >11
    DAMIEMAMTQS
    >12
    FWANLLDPLTCS

``` r
sapply(6:10, generate_protein)
```

    [1] "VYRWFA"     "TRWREAH"    "GLMDIMHA"   "CETKPSRAI"  "PDQHNFNAHD"
