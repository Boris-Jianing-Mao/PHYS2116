# PHYS 2116 Computational Assignment

## Project Overview
This repository contains the computational assignment for analysing stellar populations within the Milky Way using data from the GALAH survey and the Gaia catalogue. 

The primary objective of this code is to process raw data (Right Ascension, Declination, Parallax, and Radial Velocity) into plots to answer astronomical questions by mapping star kinematics against chemical fingerprints ([Fe/H] and [alpha/Fe]).

**When running the Colab Notebook, it will request access to mount your Google Drive.** It will create an `Astronomy_Project` folder and permanently save the 1.2 GB dataset to your Drive. 

## Methodology & Data Processing
The pipeline is built using `Python` within a Google Colab environment and relies on `astropy`, `pandas`, `numpy`, and `matplotlib`.

1. **Data Ingestion:** Merges Gaia DR3 astrometry with GALAH DR3 spectroscopy. Original pipeline identifiers (including overlapping `star_id` columns from table merges) are intentionally preserved without forced renaming to maintain strict, one-to-one traceability with the source catalogs.
2. **Quality Control:** Filters for high-quality observations by mathematically enforcing a Signal-to-Noise ratio $> 30$ and strictly excluding chemical error flags (`flag_fe_h == 0`).
3. **Kinematic Transformation:** Uses `astropy.coordinates` to convert the filtered observational data into a physical Galactocentric coordinate frame ($X, Y, Z, U, V, W$), enabling the calculation of rotational ($V_\phi$) and random velocities.
4. **Visualization:** Generates Matplotlib visualisations, including an Aitoff sky projection, a Toomre diagram, and chemical abundance plots to explicitly correlate stellar age with galactic motion.

## Repository Contents
* `GALAH.ipynb`: The main Google Colab notebook containing the code for the final submission.
