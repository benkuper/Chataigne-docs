# The Morpher : 2D interpolations made fun

The Morpher was originally a side project, coming from the need of a 2D interpolator that would interpolate between multiple presets. It eventually got merged into Chataigne's Custom Variable system, allowing to easily create interactions between this interpolator and Chataigne's mechanism, as well as being able to create multiple separate interpolators.

![Interpolating between multiple presets in a 2D voronoi system.](../.gitbook/assets/morpher.png)

By selecting **2D Voronoi** in the Control Mode parameter of your Custom Variable group, you can then use the Morpher container and panel, to place in 2D all your presets.  
Using a Voronoi-based proximity algorithm, the white target is defining the weight of each preset depending on its distance to the target, but also depending on the global layout of the Morpher.

After having set up your layout, you can start playing with attraction and decay to create even more unpredictable behaviors.

