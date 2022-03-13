# SelfAggregation
Collection of f-plane cloud-resolving model data used to study convective self-aggregation and tropical cyclogenesis by Carstens and Wing (2020, 2022). This repository contains model input parameters as plain text files for a series of simulations using the System for Atmospheric Modeling (SAM), developed by Marat Khairoutdinov at Stony Brook University. It also contains daily-averaged data in standardized netCDF format from the SAM simulations used to generate the results in Carstens and Wing (2022), which will be described below. Additional data relevant to tropical cyclogenesis will be added at a later date, and is available upon request.

# Model Input Parameters

Each folder in this repository (i.e. f01, f4, etc.) contains three text files with parameters used to run the respective f-plane simulations. These files are called grd (describing the vertical grid), snd (a reference sounding containing standard vertical profiles of altitude, pressure, potential temperature, water vapor mixing ratio, and wind), and prm (specific simulation settings including the sea surface temperature, Coriolis parameter, horizontal resolution, and frequency of model output). 

The grd and snd files are identical in each of these folders, reflecting the uniform initial conditions that each simulation begins from. The only parameter that varies between f-planes in prm is "fcor", representing the Coriolis parameter. More details about each file are discussed below.

1. grd - This file simply lists the altitude of each vertical level in the model in meters. The first model level is at 37 m, with an initial vertical grid spacing of 75 m which gradually spaces out. Above 3 km, the vertical grid spacing is fixed at 500 m. Though the vertical domain extends to an altitude of approximately 28 km, the remaining vertical levels are inferred by the model from the uniform grid spacing above 3 km. There are 64 vertical levels in total.

2. snd - This text file contains 6 columns specifying the reference vertical profiles used to initialize each simulation. The first column is simply the altitude (same as grd). The second is the reference pressure in mb or hPa, where the model output is expressed as a perturbation from this reference pressure at each level. The third column is the potential temperature (K), and the fourth is the water vapor mixing ratio (g/kg). The fifth and sixth columns are the reference profiles of zonal and meridional wind, which are set to zero at every vertical level. That is, there is no mean flow or wind shear imposed in any simulation. This sounding is developed from the domain mean of the last 30 days of a 96 km square simulation, which is run to a state of radiative-convective equilibrium (RCE).

3. prm - This file contains specific input parameters used to initialize simulations, and is the only one to vary between the folders in this repository. However, the only parameter that is different is "fcor", whose value represents the respective latitude referenced in the folder name and in Carstens and Wing (2022). The top set of parameters beginning with "do" are boolean variables. These allow for the choice of settings such as interactive longwave and shortwave radiation, the use of a Coriolis parameter, interactive surface fluxes, and nudging of wind, water vapor, and temperature profiles. Below this, settings include the sea surface temperature, Coriolis parameter ("latitude0" refers to a center latitude if a beta-plane is used), solar insolation, horizontal grid spacing, and time step. The "nsave" parameters refer to the frequency of model output, expressed in the form of time steps. For example, nsave2D = 300 with a 12 second time step means that 2D (x,y) data will be averaged and written every hour.

# CRH_1.5km.nc

This file contains snapshots of column relative humidity (x,y,t) at 10-day intervals of simulations run at 1.5 km horizontal grid spacing. These simulations on the 2 (CRH_LowF), 7 (CRH_MidF), and 20-degree (CRH_HighF) f-planes were developed in response to reviewer comments about the role of horizontal resolution in modulating convective self-aggregation. This was used to generate Figure S2 of Carstens and Wing (2022). The simulations begin with an identical random distribution of convection, and all other initial conditions are identical with the exception of the Coriolis parameter. The 20-degree simulation is only run for 50 days, as a tropical cyclone forms by day 20.

# CRH_3km.nc

Similar to CRH_1.5km.nc, this file contains snapshots of column relative humidity (x,y,t) at 10-day intervals of simulations run at 3 km horizontal grid spacing. These simulations on the 3 (CRH_LowF), 7 (CRH_MidF), and 10-degree (CRH_HighF) f-planes were used to generate Figure 1 of Carstens and Wing (2022). The 3-degree simulation shows an example of self-aggregation into a long, non-rotating band. The 7-degree simulation fails to fully self-aggregate, while the 10-degree simulation undergoes tropical cyclogenesis near day 80. All simulations are initialized with an identical distribution of random convection, and all other initial conditions are identical with the exception of the Coriolis parameter.

# DomainAverages_TimeSeries.nc



# DomainAverages_VerticalProfiles.nc



# FMSEVarianceBudget.nc
