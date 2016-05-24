# ASCII Clock

Charlie Brooking (@brookingcharlie)

## Implementation

A trigonometry-based implementation using Haskell.

Use the supplied `go` script to run the solution as follows:

```
$ ./go build
Usage: ./go run|test

$ ./go test
SUCCESS: "" -> ["INVALID INPUT"]
SUCCESS: "A" -> ["INVALID INPUT"]
SUCCESS: "10" -> ["INVALID INPUT"]
...

$ echo "25:61" | ./go run
INVALID INPUT
```

## Trigonometry

The solution relies on two equations:

x(hour) = -5 cos((2 pi / 12) hour) + 5

![plot of x(hour)](plot-x.png)

y(hour) = 8 sin(((2 pi / 12) hour) + 8

![plot of y(hour)](plot-y.png)

(To view the gnuplot scripts for the graphs above, see <plot.sh>, <plot-x.gp>, and <plot-y.gp>).

These equations make sense given that the clock a horizontal radius of 8 and a
vertical radius of 5. We can see this by looking at the clockface's position and
plotting the X and Y coordinates at each position:

{{{
        o
    o       o

 o             o

o               o

 o             o

    o       o
        o
}}}

Coordinates for each position on clockface:

```
hour  x  y
---- -- --
   0  0  8
   1  1 12
   2  3 15
   3  5 16
   4  7 15
   5  9 12
   6 10  8
   7  9  4
   8  7  1
   9  5  0
  10  3  1
  11  1  4
```

## The Challenge

In this challenge you must draw an analogue clock face.

* The time is supplied on stdin in the format hh:mm, followed by a single newline.
  Both hh and mm are padded with a leading 0 (zero) if they are less than 10.
* The analogue clock face representing that time, subject to the following rules,
  should be written on stdout.
* Each hour mark should be drawn with 'o' (Lower-case O).
* The hour mark representing the hour given in the input should be drawn with an 'h'.
* The hour mark representing the minute given in the input should be drawn with an 'm'.
* If the hour and the minute both fall on the same mark, then you should draw it with an 'x'.
* You should round down the minutes past the hour to the nearest 5 for the
  purposes of marking it on the clock (so 23 becomes 20, 39 becomes 35).

Examples:

21:35

```
        o
    o       o

 o             o

h               o

 o             o

    m       o
        o
```

04:59

```
        o
    m       o

 o             o

o               o

 o             h

    o       o
        o
```

## To Win

We will be looking for:

* Clean code
* Evidence of TDD
* A go script
* A readme
* With extra credit for:
* Submitting a solution as a pair
