---
title: "Data Structures for Subway Networks"
date: 2019-09-11T14:15:58-05:00
toc: true
draft: false
---

Currently I'm developing a twitter bot that will share a generated subway network everyday.
The first step is writing the code that will produce the network.

The first problem arised when I tried to decide how to represent it.

Originally, I only thought of generating individual lines, represented in arrays, with
each element (`station`) containing a pair of `(x, y)` coordinates. But sooner than later I
found problems with that approach.

I needed to mantain the line stations in order, so drawing them would be easy by connecting
contiguous elements with a line.

I also needed to keep track of each station information, so I could later build intersections
with other lines, if necessary.

So, how should I be representing these lines? And what about the whole network?

I decided to build bottom up, starting with the stations.

## Stations

A single station should contain the line (or lines) it belongs to, its name, the previous and
next stations, and the coordinates the stations is built in. So it had to have at least this fields:

```js
station {
    id: "st-11235",
    name: "59th Street Station",
    coordinates: {
        x: 2293.9948,
        y: 9848.8817
    },
    lines: [
        // Contains the ids of the lines this station belongs to
        "ln-n",
        "ln-r"
        ],
    previous: {
        // Contains the previous station for each line
        // line-id: station-id
        "ln-n": "st-18233"
        "ln-r": "st-17772"
        },
    next: {
        // Contains the next station for each line
        // line-id: station-id
        ln-n: "st-9928"
        ln-r: "st-887"
        }
}
```

With this information, I could easily modify each station to be part of any line by adding the id of the
line to the `lines[]` field.

By having an `id`, I could also update the name of the station without messing with the order of the stations
inside one line.

If the station was either the first or last station, their respective previous and next values would be `null`.

## Lines

Once I had the structure for a single station, specifying the structure for the lines was easier.
It just needs to contain the ids of the stations inside it, and a "shortcut" to indicate what
of those stations have intersections with other lines.

Just for practicity, I also included the ids of the first and last stations.

```js
line {
    id: "ln-n",
    size: 3,
    stations: [
        "st-18233",
        "st-11235",
        "st-9928"
    ],
    intersections: {
        // station-id: [line-id, ]
        "st-11235": ["ln-r"]
    }
    start: "st-982",
    end: "st-87"
}
```

## Network

So, having the individual stations and lines, the network could be just a wrapper to contain
all that information.

```js
network {
    lines,
    stations
]
```

## Operations over the structure

What I'd want from this structure is for it to provide me with the easeness to generate new 
stations, create intersections, and draw the network.
 
For now, the basic operations are:

- Creating stations
- Creating lines
- Adding stations to lines
- Creating intersections

### Creating stations

We would have to provide just the `name` and `coordinates` for the new station.

The id should be generated so it is guaranteed to be unique.

```js
let station = {
  id: generateUniqueID(),
  name: "My New Station",
  coordinates: {
    x: 100,
    y: 200
  }
  lines: [],
  previous: {},
  next: {}
};
```


To insert this station onto a `Line`, we use another function. See 
[Adding Stations to Lines](#adding-stations-to-lines)


### Creating lines

The default way to create a line will be by just specifying `start` and `end`.

Being `start` and `end` the only two stations, `size`, `stations`, and 
`intersections` are automatically assigned to `2`, `[start.id, end.id]`,
and `[]` respectively.

The id should be generated so it is guaranteed to be unique.

```js
let start = { /* Create a station as before */}
let end = { /* Create a station as before */ }

let line = {
  id: generateUniqueID(),
  // We could automate the initialization of size,
  // stations[], and intersections[]
  size: 2,
  stations: [
    start.id,
    end.id
  ],
  intersections: [],
  start: start.id,
  end: end.id
}
```

### Adding stations to lines

To add a station to a line, we must specify the position we'll add the station to.

This means that we have the ids of the contiguous stations that will be separated by a
new station. And of course, the line we will add the station to.

```js
/**
 * Inserts a new station between stationA and stationB,
 * with the info provided.
 * @param {Line} line         Line that will contain new station
 * @param {Station} stationA  Future `previous` for the new station
 * @param {Station} stationB  Future `next` for the new station
 * @param {Station} station   New station to insert
 */
function insertStation(line, stationA, stationB, station) {
  // Push a new element of the id of the station inside the line
  // structure 
  line.stations.push(station.id);

  // Assuming stations is global (or was sent as parameter)
  // Update the next and previous fields for A and B
  stations[stationA.id].next[line.id] = station.id;
  stations[stationB.id].previous[line.id] = station.id;

  // Add the line information to the station
  station.line.push(line.id);

  // Specify the previous and next values for the new station
  // for the corresponding line
  station.previous[line.id] = stationA.id;
  station.next[line.id] = stationB.id;
}
```

### Creating Intersections

Or, more specifically, converting stations into intersections.

This is done automatically if we call `insertStation()` defined before,
using a station that has already been inserted into another line.

---

So far, so good.

But for the actual project, the next thing must be generating a network
procedurally. And then, drawing the network.