# Dropsondes

This folder contains data, commented MATLAB code, and background information used to generate the results of Carstens and Wing (2022, GRL) - "Simulating Dropsondes to Assess Moist Static Energy Variability in Tropical Cyclones". This uses the 20-degree simulations in the main SelfAggregation folder, where model input parameters and descriptions for these files can be found.

The four simulations are labeled CTRL, LARGE, SMALL, and WEAK, with netCDF files of the column-integrated moist static energy ("MSE") and radiative/surface enthalpy fluxes ("Fluxes") available for each simulation separately. Fluxes are taken directly from the SAM model output, while MSE is computed using vertical profiles of temperature, pressure, altitude, density, and water vapor mixing ratio. In these files, the domain is centered on the TC center, defined as the grid point of minimum pressure. Descriptions of the data within the netCDF files are below, using the CTRL simulation as the example (all files are laid out identically).

# MSE_CTRL.nc
This file contains 6-hourly snapshots of column-integrated MSE through 3 different atmospheric columns, which all begin at the surface. t=0 is the first time where a TC is tracked in this study, at which point the storm is at tropical storm intensity.

1. MSE_full - Laid out in (x,y,t) coordinates, this is the column-integrated MSE (J/m^2) through the full column of the model, from the surface to a pressure of about 17 hPa.
2. MSE_G4 - The column-integrated MSE from the surface to about 200 hPa. This pressure level is near that flown by an upper-level aircraft reconnaissance flight, so this is the column that would be sampled by a dropsonde released in this type of mission.
3. MSE_P3 - The column-integrated MSE from the surface to about 680 hPa. This pressure level is near that flown by an lower-level aircraft reconnaissance flight, so this is the column that would be sampled by a dropsonde released in this type of mission.

# Fluxes_CTRL.nc
This file contains 6-hourly snapshots of longwave, shortwave, and surface enthalpy fluxes at the same times as those in MSE_CTRL.nc. All of these parameters are computed directly within the model.

1. NetLW - Laid out in (x,y,t) coordinates, this is the longwave radiative flux convergence. Here, upward fluxes are considered to be positive, and this quantity is defined as the difference between the net longwave radiative fluxes of the surface minus the top of the atmosphere.
2. NetSW - Similar to NetLW, but for the shortwave radiative flux convergence. In contrast to NetLW, downward fluxes are positive, and the difference used to obtain the convergence is the top of atmosphere minus the surface net shortwave flux.
3. SEF - Total surface enthalpy flux, computed by adding the latent and sensible heat flux calculated from bulk formulae within the model.
