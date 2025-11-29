# Geostatistically Simulating Mertz Glacier Bed Topography Using Sequential Gaussian Simulation and Markov Chain Monte Carlo

A project I worked on in the Course-Based Undergraduate Research Experience, Geophysical Exploration of the Cryosphere. University of Florida, Fall 2025.

## Overview
The topography underneath the surface of ice influences how fast and in which direction the ice is flowing and will flow in the future. In particular, Mertz Glacier is known to have undergone a calving event in 2010, after further study into the matter, it is possible that the glacier goes through cycles of ablation and calving (Giles, 2017). It is important to study the topography under this area to understand how future calving may occure, and to obtain further evidence for this cyclical nature. BedMap3 and BedMachine are products which utilized kriging to interpolate between the raw data and retain mass conservation. However, the topography they produce is too smooth to be realistic geologicaly. In order to create a rough topography, sequential gaussian simulation may be used to randomly generate topography that is constrained to match the data points, yet has geostatistical variance and realism. However, this geography has a high loss initially, and thus it is beneficial to iterate this method with markov chain monte carlo to reduce the loss. 
![Image 11-18-25 at 10 16 PM](https://github.com/user-attachments/assets/222574ec-5b6d-4c1a-bd6f-f16c70185b70)
![Image 11-18-25 at 10 18 PM](https://github.com/user-attachments/assets/c727f50f-6a25-425a-a6b9-8693f54b7e9d)
![Image 11-18-25 at 10 23 PM](https://github.com/user-attachments/assets/986b864c-c412-4c68-b4dc-c25965b000ac)
![Image 11-18-25 at 10 24 PM](https://github.com/user-attachments/assets/90270314-0fae-49d4-a7f9-3c2bb2324d1c)
Remaining figures are either being updated or created.

## Environment
This work utilized a conda environment with gstatsMCMC.yml.
Such an environment can be reproduced with the following prompt:
`conda env create -f gstatsMCMC.yml`
`conda activate gstatsMCMC`

## Usage
## Data
## Software and References

### Authors: 
Maheer Bansari, Emma (Mickey) MacKie, Niya Shao

https://github.com/NiyaShao/geostatisticalMCMC.git

SciKit Gstat

geopandas

shapely.geometry

cartopy.crs

cartopy.feature

matplotlib.lines

Topography

gstatsMCMC

Dependencies:

python=3.12.3

numba=0.59.1

numpy=1.26.4

pandas=2.1.4

scikit-gstat=1.0.21

scikit-learn=1.7.1

scipy=1.12.0

matplotlib-base=3.10.1

matplotlib-inline=0.1.7

gstools=1.7.0

gstools-cython=1.1.0

pillow=10.3.0

xarray=2024.1.0

pyproj=3.6.1

jupyterlab

netCDF4

verde=1.8.1

pip

pip:

gstatsim==1.1.5

opencv-python==4.9.0.80

Giles, A. B. (2017). The Mertz Glacier Tongue, East Antarctica. Changes in the past 100years and its cyclic nature - Past, present and future. Remote Sensing of Environment, 191, 30-37. https://doi.org/https://doi.org/10.1016/j.rse.2017.01.003
