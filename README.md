# SelfAggregation
Collection of f-plane cloud-resolving model data used to study convective self-aggregation and tropical cyclogenesis by Carstens and Wing (2020, 2022). This repository contains model input parameters as plain text files for a series of simulations using the System for Atmospheric Modeling (SAM), developed by Marat Khairoutdinov at Stony Brook University. It also contains daily-averaged data in standardized netCDF format from the SAM simulations used to generate the results in Carstens and Wing (2022), which will be described below. Additional data relevant to tropical cyclogenesis will be added at a later date, and is available upon request.

# Model Input Parameters

Each folder in this repository (i.e. f01, f4, etc.) contains three text files with parameters used to run the respective f-plane simulations. These files are called grd (describing the vertical grid), snd (a reference sounding containing standard vertical profiles of altitude, pressure, potential temperature, water vapor mixing ratio, and wind), and prm (specific simulation settings including the sea surface temperature, Coriolis parameter, horizontal resolution, and frequency of model output). 

The grd and snd files are identical in each of these folders, reflecting the uniform initial conditions that each simulation begins from. The only parameter that varies between f-planes in prm is "fcor", representing the Coriolis parameter. More details about each file are discussed below.

1. grd - This file simply lists the altitude of each vertical level in the model in meters. The first model level is at 37 m, with an initial vertical grid spacing of 75 m which gradually spaces out. Above 3 km, the vertical grid spacing is fixed at 500 m. Though the vertical domain extends to an altitude of approximately 28 km, the remaining vertical levels are inferred by the model from the uniform grid spacing above 3 km. There are 64 vertical levels in total.

2. snd - This text file contains 6 columns specifying the reference vertical profiles used to initialize each simulation. The first column is simply the altitude (same as grd). The second is the reference pressure in mb or hPa, where the model output is expressed as a perturbation from this reference pressure at each level. The third column is the potential temperature (K), and the fourth is the water vapor mixing ratio (g/kg). The fifth and sixth columns are the reference profiles of zonal and meridional wind, which are set to zero at every vertical level. That is, there is no mean flow or wind shear imposed in any simulation. This sounding is developed from the domain mean of the last 30 days of a 96 km square simulation, which is run to a state of radiative-convective equilibrium (RCE).

3. prm - 

# CRH_1.5km.nc



# CRH_3km.nc



# DomainAverages_TimeSeries.nc



# DomainAverages_VerticalProfiles.nc



# FMSEVarianceBudget.nc
