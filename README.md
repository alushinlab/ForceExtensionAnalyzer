# Force-Extension Analyzer
This document provides a tutorial on how to operate the Force-Extension Analyzer 
software suite. The tutorial is organized into four different sections:
1) Launching the Force-Extension Analyzer Suite
2) Overview of the Graphical User Interface (GUI)
3) General workflow for analyzing force-extension curves
4) Some special use cases

## 1) Launching the Force-Extension Analyzer Suite
- Download the **force_extension_analyzer.egg** file and save it to any 
directory. The file will be saved to the Desktop for this tutorial
- Navigate to the file's directory in the terminal:
```
cd ~/Desktop/
```

- Launch the Force-Extension Analyzer suite with the following command:
```
python force_extension_analyzer.egg
```

**Required to run:**<br/>
python 2.7; numpy; matplotlib; scipy; pandas; <br/>
The python libraries may be installed using the command:
```
pip install numpy; pip install matplotlib; pip install scipy; pip install pandas
```

**Recommended to run:**<br/>
-It is recommended to run the software in your operating system's base python 
installation. You may also use Anaconda or other python installations, but fonts
 may not display correctly.<br/> 
-The software was written to run on a 1920x1080 monitor. If the aspect ratio of 
your computer is different than 1920x1080, it is recommended that when you 
launch the program, you click "Options >> Screen Resolution" in the top menu.


## 2) Overview of the Graphical User Interface (GUI)
Upon launching the software, the GUI should open to its default screen:
![Default Screen](imgs/splash_screen.png?raw=true "Default Screen")

**Menu Bar:**<br/>
**-File**: user may select trace to analyze or close the program<br/>
**-Options**: user may change the window dimensions (if needed) or enable/disable 
certain features<br/>
**-Help**: displays a help menu with hints on operating the software

**Mutable fields:**<br/>
**-Lp, Ko**: user may set a persistence length and/or elastic modulus instead of 
fitting these parameters based on data. If the field values are -1, the appropriate
parameter will be fit<br/>
**-Exclude left/right**: allows the user to remove data points at the beginning 
(left) or end (right) of the trace. These fields may be useful to change in 
niche cases, but primarily only exclude right is used for excluding points after 
the DNA strand breaks<br/>
**-Smooth factor, prominence**: these values affect the segmentation of the trace, 
explained below<br/>
**-Xmin, Ymin, Xmax, Ymax**: these fields specify the plotting axes. They do not 
affect the results; just how the displayed graph looks

**Results Display:**<br/>
**-File name:** the name of the file currently being operated on. <br/>
**-Persistence length:** the fit persistence length. <br/>
**-Elastic Modulus:** the fit elastic modulus.<br/>
**-Curves:** results from the curves. If delete mode is on, by clicking on a curve,
the user may delete that curve (by setting results to -100, which is then 
removed in later processing). Deletion mode may be disabled in the Options tab. 


## 3) General workflow for analyzing force-extension curves
- Open file of interest using "File >> New File"; this will remain the current
file until a new file is chosen
- For the first time plotting the data, leave all values to the default and 
click "Update Plot"
- Tweak the **Xmin, Ymin, Xmax, Ymax** fields until the trace occupies the full 
image window. This does not affect the curve fitting or results, but it does 
allow the user to manually inspect the trace
- Change the **Exclude right** field entry to be the extension distance of the 
last data point before the DNA breaks
- In many traces, the segmentation will be good with the default parameters. If
the segmentation is not good, the smooth factor and prominence may be adjusted.
The filtered trace used for segmentation depends on the smooth factor, and it may
be visualized in debug mode, under the Options tab.
- If desired, erroneous curves may be removed (although this may have downstream
consequences on analysis. It is recommended to segment the curves correctly 
instead of deleting curves.
- Once the fitting is successful, the data may be saved by clicking "Save Data". 
For the first analyzed trace of a given condition, a new csv file will be 
created. For subsequent traces, they will be appended to this csv file, as 
specified by the user. Analysis on relevant parameters like breaking force, 
contour length, persistence length, elastic modulus, and changes in contour length
are printed in this output file, and it may be further processed.
Example trace.
![Example Image](imgs/example_img.png?raw=true "Example Image")
Example trace in debug mode.
![Example Image Debug Mode](imgs/example_img_debug.png?raw=true "Example Image Debug Mode")

## 4) Some special use cases
- If for some reason, the first segmented curve does not fit correctly, and the 
determined **Lp** and **Ko** poorly fit the other curves, you may want to temporarily 
exclude the first curve using the **Exclude left** field. Once properly measured
values of persistence length and elastic modulus are obtained, these values may be entered into the fields in
the bottom left of the GUI, and **Exclude left** may be set back to zero.
- For the 12-mer nucleosome array studied on this particular instrument, 
transitions below 5 pN were ignored because occaisionally noise could outweigh 
signal in the low-force regime, and the transitions we were studying typically 
occured around 15 pN or higher. The user may study transitions in this low force
regime by activating the low force mode in the Options tab. Alternatively, the 
user may not want to exclude any transitions, or the user's force regime of 
interest could be at a lower force i.e. 3 pN to 20 pN. If this is the case, the
source code may be easily changed by altering lines 34 and 39 in the 
helper_methods.py script. 





