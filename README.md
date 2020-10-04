# kawakudari_processing_r

This project implements part of the [std15.h](https://github.com/IchigoJam/c4ij/blob/master/src/std15.h) API (from [c4ij](https://github.com/IchigoJam/c4ij)) with [Processing](https://processing.org/) R mode, and [Kawakudari Game](https://ichigojam.github.io/print/en/KAWAKUDARI.html) on top of it.

It will allow programming for [IchigoJam](https://ichigojam.net/index-en.html)-like targets that display [IchigoJam FONT](https://mitsuji.github.io/ichigojam-font.json/) on screen using a R-like programming language.
```
settings <- function() {
  size(512, 384 + 30)
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
      scroll(std15,dir_up)
      if(scr(std15,x,5) != 0) {
        locate(std15,0,23)
        putstr(std15,"Game Over...")
        putnum(std15,frameCount)
        running <- FALSE
      }
    }
    draw_screen(std15)
  }
}

```

## Prerequisite

* [Download](https://processing.org/download/) and install Processing application suitable for your environment.
* Install [R mode](https://processing-r.github.io/)


## License
[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png)](http://creativecommons.org/licenses/by/4.0/)
[CC BY](https://creativecommons.org/licenses/by/4.0/) [mitsuji.org](https://mitsuji.org)

This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
