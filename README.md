[![CRAN](https://img.shields.io/cran/v/ggart?color=yellow&label=CRAN&logo=r)](https://cran.r-project.org/package=ggart)
[![R_build_status](https://github.com/koenderks/ggart/workflows/Build/badge.svg)](https://github.com/koenderks/ggart/actions)
[![Codecov](https://codecov.io/gh/koenderks/ggart/branch/master/graph/badge.svg?token=ZoxIB8p8PW)](https://codecov.io/gh/koenderks/ggart)
[![Bugs](https://img.shields.io/github/issues/koenderks/ggart/bug?label=Bugs&logo=github&logoColor=%23FFF&color=brightgreen)](https://github.com/koenderks/ggart/issues?q=is%3Aopen+is%3Aissue+label%3Abug)
[![Monthly](https://cranlogs.r-pkg.org/badges/ggart?color=blue)](https://cranlogs.r-pkg.org)
[![Total](https://cranlogs.r-pkg.org/badges/grand-total/ggart?color=blue)](https://cranlogs.r-pkg.org)

# ggart: Generative Art Using R

`ggart` is an attempt at making generative art available for the masses. The package mimicks the ideas of multiple generative artists in the `ggplot2` language and encapsulates each of these ideas in their own function.

The most recently released version of `ggart` can be downloaded from [CRAN](https://cran.r-project.org/package=ggart) by running the following command in R:

```r
install.packages('ggart')
```

Alternatively, you can download the development version from GitHub using:

```r
devtools::install_github('koenderks/ggart')
```

After installation, the `ggart` package can be loaded with:

```r
library(ggart)
```

Let's go hunting for some good `seed`'s!

## Overview

* [Painting of the day](#painting-of-the-day)
* [`paint_strokes()`](#paint-strokes)
* [`paint_turmite()`](#turmite)
* [`paint_ant()`](#langtons-ant)
* [`paint_planet()`](#planets)
* [`paint_mondriaan()`](#mondriaan)
* [`paint_cirlemap()`](#circle-maps)
* [`paint_arcs()`](#arcs)
* [`paint_function()`](#functions)

## Painting of the day

Every day this repository generates a random painting using the `ggart` package. This is today's painting:

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/daily.png' width='400' height='400'>
</p>

## Paint strokes

This type of painting creates paint strokes. The paint strokes algorithm is based on the simple idea that each next point on a grid has a chance to take over the color of an adjacent colored point, but also has a minor change of generating a new color. Going over the grid like this results in strokes of paint on the canvas.

You can use the `paint_strokes()` function to make your own painting using this algorithm.

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/strokes/2021-03-21.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/strokes/2021-03-20.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/strokes/2021-03-10.png' width='270' height='270'>
</p>

## Turmite

This type of painting creates a turmite. According to [wikipedia](https://en.wikipedia.org/wiki/Turmite), a turmite is *a Turing machine which has an orientation in addition to a current state and a "tape" that consists of an infinite two-dimensional grid of cells*. The classic algorithm consists of repeating the three simple steps shown below. However, the algorithm in `ggart` is slightly modified so that the block does not go off the canvas, but instead bounces back onto the canvas.

1. Turn on the spot (left, right, up, or down),
2. Change the color of the block,
3. Move forward one block.

You can use the `paint_turmite()` function to make your own painting using this algorithm.

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/turmites/2021-03-06.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/turmites/2021-03-09.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/turmites/2021-03-08.png' width='270' height='270'>
</p>

## Langton's ant

This type of painting creates Langton's ant. According to [wikipedia](https://en.wikipedia.org/wiki/Langton%27s_ant), Langton's ant is a turmite with a very specific set of rules. In particular, the algorithm involves repeating the three rules shown below. The problem with this type of painting is that it always moves off the canvas though...

1. On a non-colored block: turn 90 degrees clockwise, un-color the block, move forward one block.
1. On a colored block: turn 90 degrees counter-clockwise, color the block, move forward one block.
1. The ant is able to cycle through different colors which correspond to different combinations of these rules.

You can use the `paint_ant()` function to make your own painting using this algorithm.

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/ants/2021-03-03.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/ants/2021-03-02.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/ants/2021-03-01.png' width='270' height='270'>
</p> 

## Planets

This type of painting creates one or multiple planets in space and uses a cellular automata (inspired by an idea from [Fronkonstin](https://fronkonstin.com/2021/01/02/neighborhoods-experimenting-with-cyclic-cellular-automata/)) to fill in their surfaces.

You can use the `paint_planet()` function to make your own painting using this algorithm.

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/planets/2021-02-26.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/planets/2021-02-27.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/planets/2021-02-28.png' width='270' height='270'>
</p>

## Mondriaan

This type of painting mimics the style of the well-known paintings by the Dutch artist [Piet Mondriaan](https://nl.wikipedia.org/wiki/Piet_Mondriaan). It works by repeatedly cutting into the canvas at random locations and coloring the square that these cuts create.

You can use the `paint_mondriaan()` function to make your own painting using this algorithm.

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/mondriaans/2021-03-01.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/mondriaans/2021-02-28.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/mondriaans/2021-02-29.png' width='270' height='270'>
</p> 

## Circle maps

This type of painting is based on the concept of an [Arnold tongue](https://en.wikipedia.org/wiki/Arnold_tongue).

You can use the `paint_circlemap()` function to make your own painting using this algorithm.

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/circlemaps/2021-04-22b.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/circlemaps/2021-04-22c.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/circlemaps/2021-04-22a.png' width='270' height='270'>
</p> 

## Arcs

Inspired by the work of [@ijeamaka_a](https://twitter.com/ijeamaka_a), this type of painting mimicks her beautiful [Arc Series](https://www.etsy.com/listing/1032142006/arcs-series-geometric-art-generative-art?ref=shop_home_recs_1&crt=1).

You can use the `paint_arcs()` function to make your own painting using this algorithm.

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/arcs/2021-07-16.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/arcs/2021-07-14.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/arcs/2021-07-15.png' width='270' height='270'>
</p>

## Functions

To be honest, this last type of painting is plainly and completely taken over from the [`generativeart`](https://github.com/cutterkom/generativeart) package, but it makes pretty pictures nonetheless. In this algorithm, the position of every single point is calculated by a formula which has random parameters.

You can use the `paint_function()` function to make your own painting using this algorithm.

<p align="center">
  <img src='https://github.com/koenderks/ggart/raw/master/png/functions/2021-03-17.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/functions/2021-04-08.png' width='270' height='270'>
  <img src='https://github.com/koenderks/ggart/raw/master/png/functions/2021-04-04.png' width='270' height='270'>
</p>