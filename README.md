# Geostatistically Simulating Mertz Glacier Bed Topography Using Sequential Gaussian Simulation and Markov Chain Monte Carlo

A project developed for the Course-Based Undergraduate Research Experience, Geophysical Exploration of the Cryosphere, University of Florida, Fall 2025.

Continued updates and contribution to DEMOGORGN body of research, Spring 2026 - present.

## Overview
The topography beneath the ice influences how fast and in which direction the ice is flowing—and will flow in the future. Mertz Glacier experienced a major calving event in 2010, and further study suggests the glacier may undergo cyclical phases of tongue formation, ablation, and calving (Giles, 2017). Understanding the underlying topography is important for predicting future calving events and gathering evidence for this potential cycle.

BedMap3 and BedMachine use kriging to interpolate between radar observations while maintaining mass conservation. However, the resulting topography is often too smooth to be geologically realistic. To generate rougher, more realistic terrain, sequential Gaussian simulation can be used to create random topographies that honor the data while preserving geostatistical variability. These initial simulations have high loss, so iterating them with Markov Chain Monte Carlo helps reduce the loss and improve data agreement.

<p align="center">
  <img width="594" height="638" src="https://github.com/user-attachments/assets/0d5d7cee-9716-40c2-8026-5e06b003128e" />
</p>

As seen from the image above of the location, surface velocity, and surface type mask, Mertz is in what appears to be a phase of tongue reformation after the 2010 calving event. There is rapid ice accumulation and a floating ice region remaining where the tongue once stood. For this project, the area cropped contains the following dimensions in `Lab1_LoadData.ipynb`:

`xmin = 1382750`

`xmax = 1543250`

`ymin = -2077750`

`ymax = -1850250`

<p align="center">
  <img width="544" height="314" src="https://github.com/user-attachments/assets/bed86b21-b72e-46b9-bbaf-b0b70727ee51" />
</p>

The figure above shows the BedMap3 and BedMachine realizations of Mertz Glacier and highlights a key limitation when using them in ice-flow prediction models: the topography lacks realistic roughness. The surface appears overly smooth, which can cause ice to behave unrealistically in simulations. To address this, Niya Shao et al. developed tutorials for reconstructing the bed topography with added geostatistical roughness while still matching radar observations. This is where the Markov Chain Monte Carlo approach becomes essential, as described below.

<p align="center">
  <img width="618" height="350" src="https://github.com/user-attachments/assets/25d82109-9041-4341-8b14-98927a053ebb" />
  <img width="350" height="350" src="https://github.com/user-attachments/assets/d02526a1-e710-445d-a64b-e378d4dd6c4f" />
</p>

In T2_StatisticalAnalysis.ipynb, we generated an initial bed using a geostatistical realization from sequential Gaussian simulation and used it as the starting point for the large-scale MCMC. In T3_LargeScaleChain.ipynb, we applied Markov Chain Monte Carlo with large block sizes to rapidly lower the loss over one million iterations, reaching values below BedMachine. We then refined the result in T4_SmallScaleChain.ipynb using much smaller block sizes and 50,000 additional iterations, further reducing the loss.

The final topography reveals a region of rapidly varying bed elevation near (1.45, 1.95), likely an artifact created by the MCMC algorithm. Current works to reduce the size of the high velocity mask are underway to prevent MCMC updates in the unstable region.

<p align="center">
	<img width="350" alt="image" src="https://github.com/user-attachments/assets/48800aa9-e087-4407-95f2-f48139a9e4d0" />
	<img width="350" alt="image" src="https://github.com/user-attachments/assets/385b208d-c8a2-48fb-9770-666449d93dbe" />
	<img src="https://github.com/user-attachments/assets/d1c8cee3-73db-4971-8656-3b708b8cf4d8" width="300" />
	<img src="https://github.com/user-attachments/assets/94666239-944f-4d23-8daa-d7a948305815" width="300" />
</p>

## Environment
This work utilized a conda environment with `gstatsMCMC.yml`.

Such an environment can be reproduced with the following prompts in terminal:

`conda env create -f gstatsMCMC.yml`

`conda activate gstatsMCMC`

Then launched with:

`conda activate gstatsMCMC`

`jupyter lab`

And deactivated with:

`conda deactivate`

## Usage

To reproduce or extend this work:

	1.	Crop raw radar data using Lab1_LoadData.ipynb (or see Tutorial 1 in Niya Shao’s repository: https://github.com/NiyaShao/geostatisticalMCMC.git)
	
	2.	Fit variograms and generate initial SGS realizations with T2_StatisticalAnalysis.ipynb
	
	3.	Initialize and run the large-scale chain (T3_LargeScaleChain.ipynb)
	
	4.	Initialize and run the small-scale chain (T4_SmallScaleChain.ipynb)
	
	5.	Visualize final outputs using visualization.ipynb

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

<img width="150" height="150" alt="30" src="https://github.com/user-attachments/assets/c0eb49d0-8138-4227-8518-5e4a208dc23b" />


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
