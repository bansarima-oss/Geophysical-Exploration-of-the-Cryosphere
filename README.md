# Geostatistically Simulating Mertz Glacier Bed Topography Using Sequential Gaussian Simulation and Markov Chain Monte Carlo

A project developed for the Course-Based Undergraduate Research Experience, 
### Geophysical Exploration of the Cryosphere, 
University of Florida, Fall 2025.

## Overview
The topography underneath the surface of ice influences how fast and in which direction the ice is flowing and will flow in the future. In particular, Mertz Glacier is known to have undergone a calving event in 2010, after further study into the matter, it is possible that the glacier goes through cycles of ablation and calving (Giles, 2017). It is important to study the topography under this area to understand how future calving may occure, and to obtain further evidence for this cyclical nature. BedMap3 and BedMachine are products which utilized kriging to interpolate between the raw data and retain mass conservation. However, the topography they produce is too smooth to be realistic geologicaly. In order to create a rough topography, sequential gaussian simulation may be used to randomly generate topography that is constrained to match the data points, yet has geostatistical variance and realism. However, this geography has a high loss initially, and thus it is beneficial to iterate this method with markov chain monte carlo to reduce the loss. 

## Environment
This work utilized a conda environment with `gstatsMCMC.yml`.

Such an environment can be reproduced with the following prompts in terminal:

`conda env create -f gstatsMCMC.yml`

`conda activate gstatsMCMC`

Then launched with:
`conda activate gstatsMCMC'

`jupyter lab`

And deactivated with:

`conda deactivate`

## Usage

To reproduce or extend this work:

	1.	Crop raw radar data using `Lab1_LoadData.ipynb` (or see Tutorial 1 in Niya Shao’s repository: https://github.com/NiyaShao/geostatisticalMCMC.git)
	
	2.	Fit variograms and generate initial SGS realizations with `T2_StatisticalAnalysis.ipynb`
	
	3.	Initialize and run the large-scale chain (`T3_LargeScaleChain.ipynb`)
	
	4.	Initialize and run the small-scale chain (`T4_SmallScaleChain.ipynb`)
	
	5.	Visualize final outputs using `visualization.ipynb`

For updated tutorials and optimized methods, refer to the original repository:
https://github.com/NiyaShao/geostatisticalMCMC.git￼
## Data

Haran, T., Klinger, M., Bohlander, J., Fahnestock, M., Painter, T. & Scambos, T. (2018). MEaSUREs MODIS Mosaic of Antarctica 2013-2014 (MOA2014) Image Map. (NSIDC-0730, Version 1). [Data Set]. Boulder, Colorado USA. NASA National Snow and Ice Data Center Distributed Active Archive Center. https://doi.org/10.5067/RNF17BP824UM. 

Jan Melchior van Wessem, Willem Jan van de Berg, & Michiel Roland van den Broeke. (2023). Data set: Monthly averaged RACMO2.3p2 variables (1979-2022); Antarctica [Data set]. Zenodo. https://doi.org/10.5281/zenodo.7845736.

Morlighem, M. (2022). MEaSUREs BedMachine Antarctica. (NSIDC-0756, Version 3). [Data Set]. Boulder, Colorado USA. NASA National Snow and Ice Data Center Distributed Active Archive Center. https://doi.org/10.5067/FPSU0V1MWUB6.

Mouginot, J., Rignot, E. & Scheuchl, B. (2019). MEaSUREs Phase-Based Antarctica Ice Velocity Map. (NSIDC-0754, Version 1). [Data Set]. Boulder, Colorado USA. NASA National Snow and Ice Data Center Distributed Active Archive Center. https://doi.org/10.5067/PZ3NJ5RXRH10. [describe subset used if applicable]. Date Accessed 11-29-2025.

Pritchard, H.D., Fretwell, P.T., Fremand, A.C. et al. Bedmap3 updated ice bed, surface and thickness gridded datasets for Antarctica. Sci Data 12, 414 (2025). https://doi.org/10.1038/s41597-025-04672-y.

Rignot, E., Mouginot, J. & Scheuchl, B. (2023). MEaSUREs Grounding Zone of the Antarctic Ice Sheet. (NSIDC-0778, Version 1). [Data Set]. Boulder, Colorado USA. NASA National Snow and Ice Data Center Distributed Active Archive Center. https://doi.org/10.5067/HGLT8XB480E4.

## Software and References

### Authors: 
Maheer Bansari, Emma (Mickey) MacKie, Niya Shao

<img width="300" height="300" alt="30" src="https://github.com/user-attachments/assets/c0eb49d0-8138-4227-8518-5e4a208dc23b" />


### Softwares used

https://github.com/NiyaShao/geostatisticalMCMC.git

SciKit Gstat

geopandas

shapely.geometry

cartopy.crs

cartopy.feature

matplotlib.lines

Topography

gstatsMCMC

#### Dependencies:

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

### References to text

Giles, A. B. (2017). The Mertz Glacier Tongue, East Antarctica. Changes in the past 100years and its cyclic nature - Past, present and future. Remote Sensing of Environment, 191, 30-37. https://doi.org/https://doi.org/10.1016/j.rse.2017.01.003
