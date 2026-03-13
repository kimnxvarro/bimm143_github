# Class 06: R Functions
Kimberly Navarro

- [Background](#background)
- [A first function](#a-first-function)
- [A second function](#a-second-function)
- [A new cool function](#a-new-cool-function)

## Background

Functions are at the heart of using R. Everything we do involves calling
and using fractions (from data input, analysis to results output)

All functions in R have at least 3 things:

1.  A **name** the thing we use to call the function.
2.  One or more input **arguments** that are a comma separared
3.  The **body**, lines of code between curly brackets { } that does the
    work of the function.

## A first function

Let’s write a silly wee function to add some numbers:

``` r
add <- function(x) {
  x + 1
}
```

Let’s try it out

``` r
add(100)
```

    [1] 101

Will this work

``` r
add(c(100,200,300))
```

    [1] 101 201 301

Modify to be more useful and add more than just 1

``` r
add <- function (x,y=1){
  x + y
}
```

``` r
add(100,10)
```

    [1] 110

Will this work?

``` r
add(100)
```

    [1] 101

``` r
plot(1:10, col="blue", typ="b")
```

![](Class06_files/figure-commonmark/unnamed-chunk-7-1.png)

``` r
log(10, base=10)
```

    [1] 1

> **N.B.** Input arguments can be either **required** or **optional**.
> The later have a fall-back default that is specified in the function
> code with an equal sign.

``` r
#add(x=100, y=200, z=300)
```

## A second function

All functions in R look like this

``` r
name <- function(arg) {
  body
}
```

The `sample()` function in R…?

``` r
sample(1:10, size=4)
```

    [1]  6 10  7  4

> Q. Return 12 numbers picked randomly from the input 1:10

``` r
sample(1:10, size=12, replace=TRUE)
```

     [1] 7 6 9 7 7 5 4 6 4 2 2 1

> Q. Write the code to generate a random 12 nucleotide long DNA
> sequence?

``` r
bases <- c("A","C","G","T")
sample(bases, size=12, replace=TRUE)
```

     [1] "C" "C" "C" "C" "T" "C" "G" "A" "G" "C" "C" "T"

> Q. Write a first version function called `generate_dna()` that
> generates a user specificed length `n` random DNA sequence?

``` r
generate_dna <- function(n=6) {
  bases <- c("A","C","G","T")
  sample(bases, size=n, replace=TRUE)
}
```

``` r
generate_dna(100)
```

      [1] "T" "C" "C" "G" "C" "C" "A" "T" "A" "G" "T" "C" "G" "A" "G" "A" "A" "G"
     [19] "A" "G" "G" "A" "G" "A" "A" "G" "G" "A" "C" "G" "C" "T" "C" "C" "A" "T"
     [37] "T" "A" "T" "A" "G" "C" "A" "C" "A" "A" "C" "A" "G" "T" "C" "T" "G" "A"
     [55] "G" "A" "A" "T" "A" "A" "C" "G" "C" "T" "T" "G" "C" "C" "C" "T" "A" "T"
     [73] "T" "C" "C" "T" "T" "C" "T" "C" "A" "G" "C" "T" "G" "T" "A" "T" "A" "A"
     [91] "C" "G" "A" "C" "G" "C" "T" "C" "A" "A"

> Q. Modify your function to return a FASTA like sequence so rather than
> \[1\] ““A” “T” “C” “C” “G” we want “ATCCG”

``` r
generate_dna <- function(n=6) {
  bases <- c("A","C","G","T")
 ans <- sample(bases, size=n, replace=TRUE)
 ans <- paste(ans, collapse = "")
 return(ans)
}
```

``` r
generate_dna(10)
```

    [1] "ACAGCGGGCG"

``` r
x<- 100
x<- 10
x<- 300
x
```

    [1] 300

> Q. Give the user an option to return FASTA format output sequence or
> standard multi-element vector format?

``` r
generate_dna <- function(n=6, fasta=TRUE) {
 bases <- c("A","C","G","T")
 ans <- sample(bases, size=n, replace=TRUE)
 
 if(fasta){
   ans <- paste(ans, collapse = "")
   cat("Hello...")
 }else {
   cat("...is it me you are looking for...")
 }
 
 return(ans)
}
```

``` r
generate_dna(10)
```

    Hello...

    [1] "GTTATCAGCG"

``` r
generate_dna(10, fasta=F)
```

    ...is it me you are looking for...

     [1] "A" "T" "A" "C" "C" "T" "A" "G" "G" "C"

## A new cool function

> Q. Write a function called `generate_protein()` that generates a user
> specified length protein sequence in FASTA like format?

``` r
generate_protein <- function(n){

 aa <- c("A", "R", "N", "D", "C", "Q", "E", "G", "H", "I", "L", "K", "M", "F", "P", "S", "T", "W", "Y", "V")

 ans <- sample(aa, size=n, replace=T)
 ans <- paste (ans, collapse= "")
 return (ans)
}
```

``` r
generate_protein(10)
```

    [1] "MFLKYLPWCC"

> Q. Use your new `generate_protein()` function to generate all
> sequences between length 6 and 12 amino-acids in length and check if
> any of these are unique in nature (i.e. found in the NR database at
> NCBI)

``` r
generate_protein(6)
```

    [1] "MMKVED"

``` r
generate_protein(7)
```

    [1] "PESYMAA"

``` r
generate_protein(8)
```

    [1] "WRWCFIDR"

``` r
generate_protein(9)
```

    [1] "IDLYCTNRN"

``` r
generate_protein(10)
```

    [1] "CILLHCKWCD"

``` r
generate_protein(11)
```

    [1] "IEDFLPPCNPV"

``` r
generate_protein(12)
```

    [1] "STMEMQKPWAMS"

Or we could do a `for()` loop:

``` r
for(i in 6:12) {
  cat(">", i, sep="", "\n")
  cat(generate_protein(i), "\n" )
}
```

    >6
    PKVYRN 
    >7
    WRMRQWQ 
    >8
    IDCQIGEF 
    >9
    PCECPIMAH 
    >10
    QTHDEKEHIH 
    >11
    PRMHGFFWANC 
    >12
    SMTRQCMENDKN 

Results: Only 6-8 were found within the NCBI database.
