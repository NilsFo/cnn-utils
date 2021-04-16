# Keras Utils

This folder contains util functions that work with keras models.
The following python libraries are needed:

```
datetime
keras
matplotlib
numpy
os
socket
sys
time
```

# Function Overviews
See all functions and their usages below.
Refer to the function docstring for examples and more information.

## class: CanaryInterruptCallback
This extends the Keras Callback.
Add this to your model during training to use.

Upon training starting, a 'canary_interrupt.txt' file is created and this Callback keeps track of it.
When you delete this file, the training is ended after the current epoch completes.
You can use this class to manually delete the interrupt file to shut down the training without canceling it and run subsequent functions in your script (eg. saving the weights).

The canary file is automatically deleted when the training ends.

## class: PlotTrainingLiveCallback
This extends the Keras Callback.
Add this to your model during training to use.

This Callback automatically plots and saves specified training metrics on your device and updates the plots at the end of every epoch.
See the static field 'supported_formats' for a list of all available file formats programmatically.
Supported image formats are: eps, jpeg, jpg, pdf, pgf, png, ps, raw, rgba, svg, svgz, tif, tiff.

You can also export the plots as raw .csv files.
This callback also supports LaTeX compatible tikz plots.

This Callback also calculates the training time of each epoch and can plot them as well.
Based on that, the Callback can calculate the training ETA.

## function: gct
Gets the current time as a formated string or datetime object.
Shortcut function.

## function: get_time_diff
Calculates the time difference from a given datetime object and the current time this function is being called.

## function: create_tikz_axis
Sets up a basic tikz plot environment to be used in a LaTeX document.
This is a helper function; For the true function try `#get_plt_as_tex`.
That function fills the tikz plot with graphs.

## function: get_plt_as_tex
Formats a list of given plots in a single tikz axis to be compiled in LaTeX.
    
This function respects the limits of the tikz compiler.
That compiler can only use a limited amount of virtual memory that is (to my knowledge not changeable).
Hence this function can limit can limit the line numbers for the LaTeX document.
Read this function's parameters for more info.

This function is designed to be used in tandem with the python library matplotlib.
You can plot multiple graphs in a single axis by providing them in a list.
Make sure that the lengths of the lists (see parameters below) for the y and x coordinates, colors and legend labels match.

# LICENSE
See the license file in the repository root for license and usage information.