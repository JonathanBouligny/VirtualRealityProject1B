# Virtual Reality Project 1
A human scale scene experienced from the 'inside out'.

## Video Overview

[![OH NO! WE DIDNT LOAD THE THUMBNAIL!](http://img.youtube.com/vi/GtEXJ_xA5kc/0.jpg)](http://www.youtube.com/watch?v=GtEXJ_xA5kc)

## Overview
This project was constructed to be a human scale experience from the inside out. Essentially it had to be a building. I chose to do a startup company because I thought that would be the most interesting. I did a small company. Two programmers with one server and a few robots to help. Of course, we had to have entertainment so there was robot entertainment. It’s in the middle of a forest because that’s soothing. This report will go line by line on the various parts of the code.
## Libraries

Of course, we used AFrame, the library that takes three.js using some other JavaScript to create an entity system to make creation of files easier. 

Then I found and imported the AFrame Extras. These extras added key functionality like universal controls to the system. These universal controls allowed the scene to work on desktop and any mobile device. Basically, it detects the device and picks from some preset controls. The mobile controls are touching to move controls and the desktop is normal wasd. 

Next, I found and imported the AFrame Environment. The environment library created an infinite background, which allowed the forest to appear more natural and for there to be a lot of forest. It creates a background from a standard library of files. This library is faster than any implementation because all the files and constructs come from the same place. It created a sun, the forest, and the ground. It did not interact well with physics, this was later compensated for and will be talked about later in the report.

![Environment](https://github.com/feiss/aframe-environment-component/raw/master/assets/aframeenvironment.gif?raw=true "Environment")

From A-Frame Environment GitHub ReadMe

## Assets
I imported various jpg images to become the various textures for the planes that made up the building. These images were imported from sources cited in the end of this report. We needed to gather files for walls, the floor, the ceiling, and the exterior. The stars.jpg was the base file for the receptionist robots face. The file eventually was faded mostly out but is subtly used as the base for his face.

## Environment
The environment was an important part of the scene because it depicted exactly where I wanted my scene to be based. I wanted the company to be based in a forest, where me and a partner, perhaps a whole slew of people, could get lost in the majesty of a forest. Perhaps we would learn something new frolicking with the bird and the flowers. Anyway, I limited the number of trees in the forest to 100 for performance reasons. The environment package also didn’t work well with physics, so a ground collider had to be added on the viable play area, which was defined at 50 by 50 squares by default. This was then boxed in by plane colliders to keep the player from walking too far for performance reasons. The ground was also made flat, so the environment would not clip into the ground in the building.

![Environment](https://puu.sh/zrauN/9a073f31fe.png "Environment")

Screenshot of the Environment in Scene

## Player Camera
The player camera was developed using the example provided by our TA. It uses universal controls as previously talked about a kinematic body to interact with all the physics colliders and is positioned so that the scene opens facing the robot. It was also positioned so that you may accidently click on the robot when spawning into the scene. This reinforces that certain objects clearly labeled can be interacted with. Of course, we also told the player that they could do these things so they won't get lost. 

The last component in the camera is the ray-caster. Essentially, ray-casting shoots out rays when the player clicks that go a certain distance in the direction the player clicked. These rays intersect objects and the intersection tells the object that the player wants to interact with this object. A key point of the ray-casting mechanic was that we had to make objects intersect able or else the rays would never penetrate them. The rays go 150 units. The ray-caster also gives a targeting reticle so the player can see where they are sending the rays out from to increase accuracy. 

## Office Area

### Office
The office is composed of walls, the entrance area to walk through, and various objects. The walls are made up of two planes one is the outside plane the other is the inside plane. The inside plane is mainly for texturing. The outside plane is textured and is a collider. It works this way for all external walls. The floor is mainly for texturing. The roof is also. There are no colliders on the roof because this is unnecessary for the floor, we have a global collider, and unnecessary for the roof, the player can’t jump.

All models are GLTF files. GLTF stands for GL Transmission Format, which is a 3D scene file created withe JSON standard. This file These files were easier to work with because the texture was prepackaged with the model, this made placement and scaling easier and helped decrease the number of files in the file system, increasing simplicity.

The desks are for the first two people who work at this company to work at. These desks have computers and iPhones on them. These are apple fans. They also have their own chairs.

The filing cabinets were previously in the office area and moved to the reception area. These are for various papers that are not secure on the cloud and other papers received in the mail. The white board in the corner is brought out for quick idea sketching and other ideas that paper may not be a big enough medium for.

The arcade machine is for fun, a very enjoyable experience for a quick 10-minute break. The TV is also there for breaks and viewing various assets. The kitchen of course is for eating as well as the fridge. This allows for productivity to increase. 


![Office](https://puu.sh/zraEV/fa21136a8a.jpg "Office")

Office Area screenshot from level


### Reception

Models are GLTF. All building pieces are as previously stated.

The reception area was created for, of course, reception. It is manned by two autonomous drones. One is for entertainment of guests, the other is for administrative purposes. 

The reception desk is made for the robot to stand in and he is sized accordingly. He never moves from there because why would he. The receptionist has a giant light on his head. This lets you know he is on, and currently doing receptionist things. When you click him his light turns on. His friend is a dancer. When you click him, he does a little spin and moves forward. He dances for you.  Dance funny man dance. There is a pen for the robot. Not for him to take notes, but for the humans to leave notes for him. He enjoys this. Also, the humans use the pad. There is a sofa for sitting and waiting for your appointment and two plants to, as the robots like to put it, human up the room.

![Reception](https://puu.sh/zraF0/0e77fd30e6.jpg "Reception")

Reception area screenshot from level


## Script
The robot() function in the only script is a function that controls the robots light. This was particularly challenging to build because I did not know that the types of most of the outputs are strings, not the integers that you assume they are. So, intensity comes out as a string of numbers, and must be edited as such. 

The function gets the item with the tag robot light. This is a light positioned in the head of the receptionist robot. Then we get the intensity attribute on the light. This intensity is set to 0 by default. This means that the light is off. The logic for the next part goes as follows. First this script only activates when the bulb on the robot (the giant white piece) is intersected by a ray-cast. If when the light is intersected, the intensity is 0, meaning the light is off, turn the light on. If when the light is intersected, the intensity is 1 then turn the light off. Essentially the light turns to the opposite state when it is clicked on.

![Script](https://puu.sh/zraEV/fa21136a8a.jpg "Script")

Script area screenshot from level


## Robot Light
The light is, as previously stated, positioned in the head of the robot. The Bulb which is the clickable object has the onclick property which contains the robot() function. This means when this object is clicked it activates the robot function. This object is also intersectable so it can be intersected by ray-casts, meaning clicked on. 

There is also helpful text under the receptionist robot. This text reads, "Hi I'm a robot!". Another text bubble reads "Click my face to turn me on". This tells the user to click on the robots face which is the giant white bubble to turn him on. To assure that something like this happens the robots face is positioned right on the target reticle at the start of the scene. 

## Dancer Robot
The dancer robot is made up of several objects. These objects are the overall entity which is intersectable so it can be interacted with by the player. Then it has the GLTF model which is the robot. 

Next, we have the animations. The first animation has the parameter begin=click which means it begins when it is clicked. The animation moves the robot from its starting position to a position a little forward from the robot. The second animation works the same way except it rotates the robot from its initial rotation to 360 degrees. This spins the robot. These two animations together make the robot look like he is doing a little spin dance.

Under the robot is some helpful text. The first text reads "I'm a dancer!". The second text reads "Click me and I'll dance!". This gives the player the prompt to click the guy, so we can see him do his animation. This text assures that the player will figure it out. This assumes the player has accidently or intentionally clicked the receptionist robot.

## Boundaries
The boundaries were put up to keep the player from wandering off the stage. The stage has an infinite background, this could cause performance issues. So, the ground collider was only set to 50 by 50. Then extra colliders were added in around the playable area. This allows the player to wander around while not falling off the edge of the scene. The colliders are invisible planes with static bodies on them. These static bodies are 10 high, although this is unnecessary.

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
