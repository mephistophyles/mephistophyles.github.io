---
layout: post
title: Simulating Car Dynamics on the Spa Francorchamps Circuit
blog_group: project
---


As part of a course on simulation, we were given noisy (GPS) height data of the area around (and including the) track at Spa Francorchamps. This data was then cleaned and used to develop a heightmap (Fig 3) of the area, as well as later on to simulate the dynamics of a car's suspension system as it travels along the track based on split time data.

|![gui of the single mass spring damper]({{site.url}}/images/spa/gui.png)|
|---|
|Fig 1. The GUI of the 2D, note the configurable parameters and the input file contains timestamped position, speed and height data of the car on the track.|

The first incarnation of the simulation focused on a single mass-damper-spring system, but later on this was expanded to the classical half-car model. Expansion to the full 3D car, with lateral dynamics was left outside the scope of the simulation since information such as turning speed and position on the track were missing.

|![raw gps data with outliers]({{site.url}}/images/spa/raw.png)|![cleaned up gps data]({{site.url}}/images/spa/smooth.png)|
|---|---|
|Fig 2. Plot of the raw data of the area around the Spa track. | Fig 3. The smoothed data of the same area used in the above simulation. |

All the code can be found [here](http://www.github.com/mephistophyles/simulatieopdracht)
