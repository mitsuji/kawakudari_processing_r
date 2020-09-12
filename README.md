# kawakudari_processing_r

This project implements part of the [std15.h](https://github.com/IchigoJam/c4ij/blob/master/src/std15.h) API (from [c4ij](https://github.com/IchigoJam/c4ij)) with [Processing](https://processing.org/) R mode, and [Kawakudari Game](https://ichigojam.github.io/print/en/KAWAKUDARI.html) on top of it.

It will allow programming for [IchigoJam](https://ichigojam.net/index-en.html)-like targets using a R-like programming language.
```
settings <- function() {
  size(512, 384)
  std15 <- Std15(512,384,32,24)
  x <- 15
  running <- TRUE
}

draw <- function() {
  if (running) {
    if (frameCount %% 3 == 0){
      if (keyPressedVar) {
        if (keyCode == LEFT)  x <- x-1
        if (keyCode == RIGHT) x <- x+1
      }
      locate(std15,x,5)
      putc(std15,charToRaw("0"))
      locate(std15,random(32),23)
      putc(std15,charToRaw("*"))
      scroll(std15)
      if(scr(std15,x,5) != 0) running <- FALSE 
    }
    pAppletDraw(std15)
  }
}

```

## Prerequisite

* [Download](https://processing.org/download/) and install Processing application suitable for your environment.
* Install [R mode](https://processing-r.github.io/)


