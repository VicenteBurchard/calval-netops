## Installation

You should have these programs installed:

* Python and/or [Anaconda](https://www.anaconda.com/download/success). 
* [QGIS](https://qgis.org/en/site/forusers/download.html)

Install the requirements either with conda/mamba:

`mamba env create -f environment.yml`

or

`conda env create -f environment.yml`

or check if you have installed these libraries:

- jupyter
- notebook
- jupyterlab
- jupyter-book
- jupyterlab-myst
- gdal
- numpy
- scipy
- pandas
- matplotlib
- geopandas
- pathlib
- scikit-learn
- pip

## Run the interactive book
Run the following command to initialize the book:

1. Activate python environment 

`conda activate calval-netops`

2. Initialize jupyter notebook
  
`jupyter notebook uav_calval_socorro.ipynb`

or 

`jupyter lab uav_calval_socorro.ipynb`
