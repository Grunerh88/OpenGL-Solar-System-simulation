# OpenGL-Solar-System-simulation
Animated to scale 3D model of the Solar System using OpenGL


Objects
* Sun
	* Textured
	* Point light within
* Mercury, Venus, Earth, Mars, Uranus, Neptune, Pluto:
	* Textured
	* Scaled rotation
	* Scaled orbit
* Jupiter:
	* Animated texture
	* Scaled rotation
	* Scaled orbit
* Saturn:
	* Textured
	* Scaled rotation
	* Scaled orbit
	* Surrounded by separate ring object
	* Ring spins in same direction but slightly faster

The scene depicts a model of our solar system, with multiple realistic characteristics, and some that are exaggerated for practicality. All 
eight planets (and Pluto) orbit the central “Sun” and rotate. The model can be toggled from a 2D planar 
view, to a 3D view utilizing the y axis in addition to x and z. Attached planet labels can also be toggled on 
or off in the menu.

<p>
Mercury:
</p>

![Mercury](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/mercury.JPG)

<p>
Venus:
</p>

![Venus](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/venus.JPG)

<p>
Earth: Then only texture used not stitched from NASA or other official sources (worldtex.bmp)
</p>

![Earth](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/earth.JPG)

<p>
Mars:
</p>

![Mars](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/mars.JPG)


<p>
Jupiter: This was one of the more technical planets. Although not apparent from the still image below, 
the texture is animated to (somewhat) simulate the storming, moving atmosphere of the planet. When 
unfrozen the planet spin and animated texture give off a “wiggly” feel to the texture.
</p>

![Jupiter](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/jupiter.JPG)



<p>
Saturn: This was one of the more troublesome parts of this project. Not the planet itself, but the ring. 
Even more specifically, texturing the ring. I spent about a quarter of the time on this project trying to 
figure out how to apply a HD ring texture I found to the ring, but was ultimately unable to do so since I 
used a glu function that gives up any vertex freedom after use. That being said, I decided to apply the 
Saturn texture resulting in a decent representation of the planet and its ring.
</p>

![Saturn](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/saturn.JPG)


<p>
Uranus: Despite what looks like a non-textured blue ball, the applied image is from NASA.
</p>

![Uranus](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/uranus.JPG)


<p>
Neptune:
</p>

![Neptune](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/neptune.JPG)


<p>
Pluto:
</p>

![Pluto](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/pluto.JPG)



<p>
Scene:
</p>

![Scene](https://github.com/Grunerh88/OpenGL-Solar-System-simulation/blob/main/Images/overall.JPG)


As mentioned above, some aspects are realistic while others are exaggerated. Due to the sheer scale of 
real space, the orbital radii are completely unrealistic and incremented by 0.333 for each planet. While 
the planet diameters are also unrealistic they are actually scaled to one another somewhat. For the 
planet radii values, I modified the real radii values (Km) in the following way: 

2.5 * log(radius)/ log(Jupiter radius)

The log operation clumps the large outliers closer together, and the rest is to adjust and scale the value 
to a fraction of Jupiter (the largest radius) such that Jupiter’s final value is 0.25. This can be seen in the 
following table: 

Planet | Radius | log(Radius) | 2.5*log(radius)/4.85 | Final Radii
------------ | ------------- | ------------ | ------------- | ------------
Mercury | 2439.7 | 3.3873364 | 1.744517406 | 0.17445174
Venus | 6051.8 | 3.7818846 | 1.947714259 | 0.19477143
Earth | 6378.1 | 3.8046913 | 1.959460002 | 0.195946
Mars | 3396.2 | 3.5309933 | 1.818502335 | 0.18185023
Jupiter | 71492 | 4.8542574 | 2.499998685 | 0.24999987
Saturn | 60268 | 4.7800868 | 2.461799934 | 0.24617999
Uranus | 25559 | 4.4075439 | 2.269936024 | 0.2269936
Neptune | 24764 | 4.3938208 | 2.262868488 | 0.22628685
Pluto | 1196 | 3.0777312 | 1.585067126 | 0.15850671



The realistic attributes are the orbital periods with respect to the orbital radius and the planet rotation 
speed. By applying Kepler’s Third Law of planetary motion to the predetermined orbital radii we get the 
accurately scaled Orbital Period:

Orbital Period = sqrt(Orbital Radius^3)

Planet | Actual Period (Earth years) | Or Radius | Or Period |
------------ | ------------- | ------------ | ------------- 
Mercury | 0.241 | 0.333 | 0.192161487
Venus | 0.615 | 0.667 | 0.544739353
Earth | 1 | 1.001 | 1.001500375
Mars | 1.88 | 1.335 | 1.542488371
Jupiter | 11.9 | 1.669 | 2.156177476
Saturn | 29.5 | 2.003 | 2.834793472
Uranus | 84 | 2.337 | 3.572630229
Neptune | 165 | 2.671 | 4.365267198
Pluto | 248 | 3.005 | 5.209148215



For the rotation, I simply divided the actual rotation time values (Earth days) by 1000 for values that are 
usable with openGL. 

Planet | Rotation (Earth days)  | Final Rotation
------------ | ------------- | ------------
Mercury | 58.6 | 0.0586
Venus | 243 | 0.243
Earth | 1 | 0.001
Mars | 1.03 | 0.00103
Jupiter | 0.41 | 0.00041
Saturn | 0.45 | 0.00045
Uranus | 0.72 | 0.00072
Neptune | 0.67 | 0.00067
Pluto | 6.39 | 0.00639

As a result of these calculations, the raw values aren’t lifelike, but they are scaled correctly from planet 
to planet. 
