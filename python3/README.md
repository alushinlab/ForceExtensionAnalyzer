# Using the force extension analyzer in a python 3 environment
### Due to Tkinter and matplotlib compatibility issues, this program only works on python versions up to, and including, version 3.5
It is recommended to create a separate conda environment for this program to ensure it will run. Enter the following in the command line to create a new environment:
```
conda create --name forceExtAnalyze_pyth3p5 python=3.5
```
Then activate the environment:
```
conda activate forceExtAnalyze_pyth3p5
```
And install the required packages: 
```
pip install numpy; pip install matplotlib; pip install scipy; pip install pandas
```
Once the conda environment has the required packages, it may be activated at any point, and the egg file in this directory can be run using the following command:
```
python force_extension_analyzer.egg
```
