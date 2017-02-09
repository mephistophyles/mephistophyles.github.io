---
layout: post
title: License Plate Recognition
blog_group: project
---
For a class on image processing a friend of mine (Jorick Spitzen) and I worked on a project together to implement a license plate recognition program. In four days we built a program to recognize license plate numbers from video.

We would be given video (see screenshot below) of various cars in various lighting settings, orientations and the like and we were tasked with reading them and finding them in the video and printing their plate details.

|![An example of the kind of data we had to work from.]({{site.url}}/images/license_plate/frame2.jpg)|
|---|
|Fig 1. An example of the kind of data we had to work from.|

It's a trivial task for humans, but getting a computer to do it in real time isn't quite as simple. First we had to figure out how do we distinguish which part of the frame is the license plate. We did this by leveraging three key bits of information:
1. License plates in Holland are all yellow
2. License plates in Holland are all the same approximate height, width
3. License plates in Holland use the same standardized font.

Now we knew the lighting conditions would be various, so we had our program search for areas of yellow within certain color and intensity parameters (we tweaked it by testing it against footage of yellow cars), then we again filtered based on aspect ratio (height:width), again with certain tolerances to deal with stickers, borders, shadows, etc.

This license plate image we segmented out and passed on as a black and white image to our OCR (optical character recognition). Using some more invariants in Dutch license plates (6 characters, letters and number groups separated by dashes, fixed font) we built a library of every possible letter and number. Then we cleaned up our image and took out the 6 largest images (we ignored the dashes, explained why later), compared them to our image database and returned the possible matches.

In order to avoid certain false positives we tested the license plates against the RDW (Database of all registered license plates in the Netherlands) API to see if it is indeed a legal plate. We also used a regular expression to reinsert the dashes into the final answer.

|![A screenshot of our program running]({{site.url}}/images/license_plate/screenshot2.jpg)|
|---|
|Fig 2. A screenshot of our program running.|
Attached is also the [poster]({{ site.url }}/assets/finalposter_group5.pdf) we presented at the end of the project, including some more details of the implementation and suggested improvements. Final MATLAB code can be found on Jorick Spitzen's Github repository [here](https://github.com/jspitzen/yolo-robot) (and yes, we did call the project Yolo-Robot).