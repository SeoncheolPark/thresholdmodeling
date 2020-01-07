# thresholdmodeling: A Python package for modeling excesses over a threshold using the Peak-Over-Threshold Method and the Generalized Pareto Distribution

This package is intended for those who wish to conduct an extreme values analysis. It provides the whole toolkit necessary to create a threshold model in a simple and efficient way, presenting the main methods towards the Peak-Over-Threshold method and the fit in the Generalized Pareto Distribution.

In this repository you can find the main files of the package, the [Functions Documenation](https://github.com/iagolemos1/thresholdmodeling/blob/master/Functions%20Documentation.md), the [dataset](https://github.com/iagolemos1/thresholdmodeling/blob/master/dataset/rain.csv) used in some examples, the [paper](https://github.com/iagolemos1/thresholdmodeling/blob/master/paper.md) submitted to the [Jounal of Open Source Software](https://joss.theoj.org/) and some tutorials. 

# Installing Package 
**It is necessary to have internet connection.**
For installing the package just use the following command (it is already in PyPi): 
```
pip install thresholdmodeling
```
The Python dependencies for runing the software will install automatically with this command.

Once the package is installed, it is necessary to run this lines on your IDE for installing ``POT`` package:
```python
from rpy2.robjects.packages import importr
import rpy2.robjects.packages as rpackages

base = importr('base')
utils = importr('utils')
utils.chooseCRANmirror(ind=1)
utils.install_packages('POT') #installing POT package
```
Or, it is possible to download this [file](https://github.com/iagolemos1/thresholdmodeling/blob/master/install_pot.py) in order to run it in yout IDE and installing ``POT``.

# User's guide and Reproducibility 
In the file [test](https://github.com/iagolemos1/thresholdmodeling/blob/master/Test/test.py) it is possible to see how the package should be used. In [Functions Documenation](https://github.com/iagolemos1/thresholdmodeling/blob/master/Functions%20Documentation.md) it may be seen a complete documentation on how to use the functions presented in the package. 

In order to present a tutorial on how to use the package and its results, a guide is presented below, using the example on the Coles's [book](https://www.springer.com/gp/book/9781852334598) with the [Daily Rainfall in South-West England](https://github.com/iagolemos1/thresholdmodeling/blob/master/dataset/rain.csv) dataset.

## Threshold Selection
Firstly, it is necessary to conduct a threshold value analysis using the first two functions of the package: ``MRL`` and ``Parameter_Stability_Plot``, in order to select a reasonable threshold value. 
Runing this: 
```python
from thresholdmodeling import thresh_modeling #importing package
import pandas as pd #importing pandas

url = 'https://raw.githubusercontent.com/iagolemos1/thresholdmodeling/master/dataset/rain.csv' #saving url
df =  pd.read_csv(url, error_bad_lines=False) #getting data
data = df.values.ravel() #turning data into an array

thresh_modeling.MRL(data, 0.05)   
thresh_modeling.Parameter_Stability_plot(data, 0.05)
```
The results must be:
![](result_MRL.png)
![](result_SHAPE.png)
![](result_MODSCALE.png)

# Backgroud
I am a mechanical engineering student in the Federal University of Uberlândia and this package was made in the Acoustics and Vibration Laboratory, in the School of Mechanical Engineering.

