mrphysics_code

The following circle packing code was developed for a side project I worked on. It performs random close packing on a collection of circles, uniformly or non-uniformly sized, using Matlab's morphological operation *imdilate*.

To run the code, the user inputs two items: the radii of the group of circles to be packed [n 1] and a desired resolution. The resolution determines the precision of the packing as well as the run-time. 

The result outputs the following:
(1) a list of positions corresponding to the centers of the circles
(2) a list of corresponding radii 
(3) an image of the packing
(4) a plot of the density of the packing as a function of windowing size 

Some details on item #4. The packing naturally takes on a circular shape. The density is measured by selecting a region of space within the packing. I start with delineating a circular boundary about the entirety of the packing and slowly shrinking this circular boundary. The plot of density as a function of the size of region of selection shows that it quickly plateaus to a maximum value (maximum packing density). 

This version of the code uses the operation *imdilate* which serves to make the algorithm computationally more rapid. It is an adaptation of the original script, which relies on an iterative process. Arguably this former version offers greater precision; however packings of large number of circles inconveniently increases run-time. I've also listed this version of the code here as *circ_pk_original.m*   

I do not claim that this method offers a mathematically fool proof means for random close packing. The general steps are itemized below. 

1. Generate a list of radii. For random packing, this list should be randomized (not sorted in any way).
2. Create a space for this packing using the function meshgrid.
3. Select the center of this space as the center of the first circle.
4. Determine the average center of the packing. For the first circle, the average center is simply the center of itself. For two circles, I find the mean of the x-coordinates and y-coordinates to generate an average (x,y) coordinate. 
5. I find the radii of the circle-to-be-placed and add that value to the radii of the circle(s) already packed. This allows me to create a region within which I can not place this new circle. 
6. I place the new circle (a) just outside this exclusion zone and (b) closest to the average position of the centers of the circles already in the packing.   



