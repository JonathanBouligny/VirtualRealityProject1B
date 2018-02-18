# Virtual Reality Project 1
A human scale scene experienced from the 'inside out'.

## Video Overview

[![OH NO! WE DIDNT LOAD THE THUMBNAIL!](http://img.youtube.com/vi/GtEXJ_xA5kc/0.jpg)](http://www.youtube.com/watch?v=GtEXJ_xA5kc)

## Overview
This project was constructed to be a human scale expereince from the inside out. Essentially it had to be a building. I chose to do a start up company because I thought that would be the most interesting. I did a small company. Two programmers with one server and a few robots to help out. Of course we had to have entertainment so there was robot entertainment. Its in the middle of a forest because thats soothing. This report will go line by line on the various parts of the code.
## Libraries

Of course, we used AFrame, the library that takes three.js using some other javascript to create an entity system to make creation of files easier. 

Then I found and imported the AFrame Extras. These extras added key functionality like universal controls to the system. These universal controls allowed the scene to work on desktop and any mobile device. Basically, it detects the device and picks from some preset controls. The mobile controls are touch to move controls and the desktop is normal wasd. 

Next, I found and imported the AFrame Environment. The environment library created an infinite background, which allowed the forest to appear more natural and for there to be a lot of forest. It creates a background from a standard library of files. This library is faster than any implementation because all the files and constructs come from the same place. It created a sun, the forest, and the ground. It did not interact well with physics, this was later compensated for and will be talked about later in the report.

## Assets
I imported various jpg images to become the various textures for the planes that made up the building. These images were imported from sources cited in the end of this report. We needed to gather files for walls, the floor, the ceiling, and the exterior. The stars.jpg was the base file for the receptionist robots face. The file eventually was faded mostly out but is subtly used as the base for his face.

## Environment
The enviornment was an important part of the scene because it depicted exactly where I wanted my scene to be based. I wanted the comapny to be based in a forest, where me and a partner, perhaps a whole slew of people, could get lost in the majesty of a forest. Perhaps we would learn something new frolicking with the bird and the flowers. Anyway, I limited the amount of trees in the forest to 100 for preformance reasons. The environment package also didnt work well with physics, so a ground collider had to be added on the viable play area, which was defined at 50 by 50 squares by default. This was then boxed in by plane colliders to keep the player from walking too far for preformance reasons.

## Sources

### Libraries

AFrame

https://github.com/aframevr/aframe

AFrame-Extras

https://github.com/donmccurdy/aframe-extras

AFrame-Environment 

https://github.com/feiss/aframe-environment-component

### Model Sources

Kitchen

https://sketchfab.com/models/3b540ab5964a428c8cb4563ed737d2c7?utm_source=triggered-emails&utm_medium=email&utm_campaign=model-downloaded

fridge

https://sketchfab.com/models/2e6576fae0ea4034b09cd48722feb9a7#

table

https://sketchfab.com/models/132b635ab00748ab905bbc279497d6d9?utm_source=triggered-emails&utm_medium=email&utm_campaign=model-downloaded

Iphone

https://sketchfab.com/models/bd03fb7d550e4a609d8261696c25f610# 

filing cabinet

https://sketchfab.com/models/cd6f9016db8644129af1b6026f9e46bd

arcade machine

https://sketchfab.com/models/e9f530f79c674880ad48ff23b5cf5ed1

tv

https://sketchfab.com/models/c91f9ac4de274b5aad362e0f19c3f16b?utm_source=triggered-emails&utm_medium=email&utm_campaign=model-downloaded

potted plant

https://sketchfab.com/models/1eadc590800847e1a23c49223e355738 

office chair

https://sketchfab.com/models/db03012c3c484314a480b4137da8eb30?utm_source=triggered-emails&utm_medium=email&utm_campaign=model-downloaded

computer

https://sketchfab.com/models/aa398650fe6e4baa8771c71266d842f4?utm_source=triggered-emails&utm_medium=email&utm_campaign=model-downloaded

server

https://sketchfab.com/models/6fe2cacf836b4aed96c650b286db5486#

pens

https://sketchfab.com/models/c6b686d261df46bc833f1c5309907770# 

desk

https://sketchfab.com/models/368ff371a72949ddbf00b2539a4a71ce# 

reception desk

https://sketchfab.com/models/b20d6299f00945e4ab26f3b29ec8a181?utm_source=triggered-emails&utm_medium=email&utm_campaign=model-downloaded 

sofa

https://sketchfab.com/models/3e26165f222f4eabbc1c06d1120f4727# 

whiteboard

https://sketchfab.com/models/858a2d94034f48ebbbbbd1f07494cea0#

receptionist

https://sketchfab.com/models/c335e0d796e1442299fa7a9df84cbb12?utm_source=triggered-emails&utm_medium=email&utm_campaign=model-downloaded


### Texture Sources

wall

http://andreaoutloud.com/26625/modern-indoor-wall-tetures-teture-designs-print/

floor

http://inverbol.com/dark-brown-wood-floor-texture/

exterior

http://www.e-splash.gr/product-category/tapetsaries/

ceiling

http://www.jemfix.se/vaeggpaneler__11558/vaeggpanel_9038372

stars

https://upload.wikimedia.org/wikipedia/commons/6/62/Starsinthesky.jpg




