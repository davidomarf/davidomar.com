---
title: "Procedurally Generated Subway Networks"
date: 2019-09-12T00:20:19-05:00
draft: true
---

This is the second article related to the development of
[Subway Networks](/projects/subway-networks). Now, I'll deal with the generation
of the networks.

For the v1.0.0 of the project, I aim to work without taking any data as input,
letting the program be completely free about the process. However, for the v2.0.0
I'd like it to take as input the geographic data of real cities.

This post will describe the working ideas for v1.0.0. For v2.0.0 I'll write
another one when opportune.

I'll be using the data structures and the corresponding operating functions
I described in the previous post:
[Data Structures for Subway Networks](/writings/data-structures-for-subway-networks/).

## Generating first line

The first line is different from every other line because it doesn't have to look for
intersections when generating the line.

1. Create two stations on opposite sides of the city: `start` and `end`.
1. Create a new station near the midpoint between `start` and `end`.
   - Displace the station to generate a wiggly line.
1. Repeat 2 until the two stations are closer than a distance `d`.

![Single Subway Line](/img/writings/procedurally-generated-subway-networks/single-subway-line.png)

## Generating subsequent lines

### Method 1 (not used)

This is the first idea I had, but started to produce degenerated results once implemented.

It consisted on repeating the first-line algorithm, but adding the capacity to create
intersections when the newly created stations were near enough to previously existing
stations.

1. Create two stations on opposite sides of the city: `start` and `end`.
1. If there are no intersections with other lines, generate like a first line.
1. If there are intersections:
   1. Select a station close to the intersection (not necesarily the closest
      one)
   2. Add that station to the line. (See
      [Adding Stations to Lines][adding-stations-to-lines])
   3. Treat the intersection as a simple station, and proceed like it's a first
      line.


![Subway Network with Method 1](/img/writings/procedurally-generated-subway-networks/subway-network-method-1.png)

The problem with this approach is that it doesn't necessarily connect a new line to the
existent network. Every subsequent line should have at least one intersection with any other
line.

Plus, selecting random positions for the lines would produce degenerated cases like lines being really close
both in position and direction to another one, or very short lines with 2 or 3 stations, or the worse one:
disconnected lines.

These problems could be solved by forcing the generation of points to be distant from each other,
forcing the slope of the start and end points, or setting a minimum line station-span.

However, I decided to look for other ideas that would produce better results without me needing
to force the structure too much.

### Method 2

Turning heavily loaded stations into growing hermit worms.

First, I'd choose a heavilyLoaded station and turn it into an intersection between 
the line it already belongs to, and the new line to be created.

Then, the new line would grow perpendicularly to the slope of the existent line.

This algorithms has two main parts: 

- Determining the "usage load" of each station.
- Adding stations to the new line.

#### Determining usage load

The meaning I gave to `stationUsageLoad` was "proportion of points inside the city that
have this station as the closest one".

To solve this, I'd obtain the Voronoi diagram for the stations in the network, and then
compute the area of each polygon.
This works because each point that built a polygon, is the closest point to every point
inside that polygon.

![Usage load for stations in subway network][usage-load-1]

The more usage load, the darker the shade of red. 

I didn't want to start an intersection at any line terminal, so I decided not to consider
them when computing usage load.

#### Growing lines

After selecting the station that will span the new line, the program should determine the
direction for the line to propagate.

Let's assume we have a subway line formed by (and keeping that order) `st-0`, `st-1`,
and `st-2`.

We now want to create a new line using `st-1` as the intersection.

To determine the direction of the new line, we compute the slope of the line that joins
`st-0` with `st-2`. 

This direction directly determines the position of the two contiguous stations for `st-1`
in the new line.

For the next stations, they use the previously used direction and apply a mild modification
to it.

Each new station has a lookup radius for other stations. If another station falls within
that radius, and the current line doesn't already have an intersection with the lines that
station belongs to, the new stations will be generated so they aim to join that station.



[adding-stations-to-lines]: /writings/data-structures-for-subway-networks/#adding-stations-to-lines
[usage-load-1]: /img/writings/procedurally-generated-subway-networks/subway-network-usage-load.png