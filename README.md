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

This file contains time series of domain-averaged thermodynamic variables used to characterize the mean state of the various f-plane simulations, averaged daily. The variables are in dimensions of (f,m,t), where f refers to the effective latitude corresponding to that simulation's Coriolis parameter in increasing order (i.e. 0.1 -> 1 -> 2... -> 15 -> 20 degrees), m is the ensemble member, and t is the day. Within an individual f-plane, ensemble members are initialized with a different random distribution of convection. However, "Member 2" of one f-plane has an identical distribution to "Member 2" of another. The 4-degree and 8-degree simulations were extended an additional 20 days, so data are available for these simulations from day 101-120. A NaN value means that data are not available for that ensemble member or time step, as the size of the individual f-plane ensembles varies. There are 14 f-planes and a total of up to 5 ensemble members for each. Data are used to produce Figure 2 and Figure S1 in Carstens and Wing (2022). The data are as follows:

1. CF - Cloud fraction, or fraction of the domain covered by clouds
2. PREC - Precipitation rate (mm/day)
3. OLR - Outgoing longwave radiation (W/m^2)
4. PW - Column precipitable water (mm)
5. LHF - Latent heat flux (W/m^2)
6. SHF - Sensible heat flux (W/m^2)

# DomainAverages_VerticalProfiles.nc

This file contains vertical profiles of domain-averaged thermodynamic variables used to characterize the mean state of the various f-plane simulations, averaged over the final 30 days of each simulation. The variables are in dimensions of (f,m,z), where f refers to the effective latitude corresponding to that simulation's Coriolis parameter in increasing order (i.e. 0.1 -> 1 -> 2... -> 15 -> 20 degrees), m is the ensemble member, and z is the altitude. Within an individual f-plane, ensemble members are initialized with a different random distribution of convection. However, "Member 2" of one f-plane has an identical distribution to "Member 2" of another. Though the 4-degree and 8-degree simulations are extended an additional 20 days, the profiles are still averaged from day 70-100 for consistency. A NaN value means that data are not available for that ensemble member, as the size of the individual f-plane ensembles varies. There are 14 f-planes and a total of up to 5 ensemble members for each. Data are used to produce Figure 2 and Figure S1 in Carstens and Wing (2022). The data are as follows:

1. CF_Vertical - Cloud fraction, or fraction of the domain covered by clouds at a given altitude
2. TEMP - Temperature (K)
3. THETAE - Equivalent potential temperature (K)
4. QL - Liquid water mixing ratio (kg/kg)
5. QI - Ice mixing ratio (kg/kg)
6. RH - Relative humidity (%)
7. LQRAD - Longwave radiative heating rate (K/day)
8. SQRAD - Shortwave radiative heating rate (K/day)

# FMSEVarianceBudget.nc

This file contains time series of all feedbacks (including their decompositions) to the FMSE spatial variance budget of Wing and Emanuel (2014), for the f-plane simulations studied in Carstens and Wing (2022). These are used to generate Figures 3-6 in the manuscript, and also include the dates of tropical cyclogenesis and lifetime maximum intensity for the high-f simulations (as in Figure 4). Variables are described below, expressed in terms of (f,m,t) - the effective latitude corresponding to the Coriolis parameter (in increasing order), the ensemble member, and the day (daily-averaged). NaN values indicate that a particular ensemble member is not run for a given f-plane, since the ensembles are of varying size. The feedbacks represent correlations between anomalies of FMSE and that particular variable in question.

1. VAR - Daily and domain-averaged variance of frozen moist static energy (FMSE, J^2/m^4)
2. VAR_TEN - Tendency of FMSE variance (i.e. what the budget solves for, J^2/(s m^4))
3. ADV - Advective feedback, representing changes in FMSE variance due to mesoscale circulations. This is calculated as a residual from VAR_TEN and DIAB (J^2/(s m^4))
4. DIAB - Diabatic feedback, the sum of the longwave, shortwave, and surface flux feedbacks. LW+SW+SEF (J^2/(s m^4))
5. SEF - Surface flux feedback, decomposed into latent and sensible heat flux components which can be broken down further (J^2/(s m^4))
6. LHF - Latent heat flux feedback, which adds into SEF (J^2/(s m^4))
7. SHF - Sensible heat flux feedback, which adds with LHF into SEF (J^2/(s m^4))
8. LW - Longwave radiative feedback, which can be decomposed into clear-sky and cloud components (J^2/(s m^4))
9. LW_CLOUD - Cloud longwave feedback, which adds into LW (J^2/(s m^4))
10. LW_CLEAR - Clear-sky longwave feedback, which adds with LW_CLOUD into LW (J^2/(s m^4))
11. SW - Shortwave radiative feedback, which can be decomposed into clear-sky and cloud components (J^2/(s m^4))
12. SW_CLOUD - Cloud shortwave feedback, which adds into SW (J^2/(s m^4))
13. SW_CLEAR - Clear-sky shortwave feedback, which adds with SW_CLOUD into SW (J^2/(s m^4))
14. LHF_MEANEDDY - Mean eddy term of latent heat flux feedback, characterized by the product of disequilibrium and wind speed feedbacks. This is subtracted from the WIND, DISEQ, and EDDY terms to achieve the full LHF feedback (J^2/(s m^4))
15. LHF_EDDY - Eddy term of latent heat flux feedback, calculated using the product of disequilibrium and wind speed feedbacks (J^2/(s m^4))
16. LHF_WIND - Wind speed (WISHE) component of latent heat flux feedback (J^2/(s m^4))
17. LHF_DISEQ - Air-sea enthalpy disequilibrium component of latent heat flux feedback (J^2/(s m^4))
18. SHF_MEANEDDY - Mean eddy term of sensible heat flux feedback, characterized by the product of disequilibrium and wind speed feedbacks. This is subtracted from the WIND, DISEQ, and EDDY terms to achieve the full SHF feedback (J^2/(s m^4))
19. SHF_EDDY - Eddy term of sensible heat flux feedback, calculated using the product of disequilibrium and wind speed feedbacks (J^2/(s m^4))
20. SHF_WIND - Wind speed (WISHE) component of sensible heat flux feedback (J^2/(s m^4))
21. SHF_DISEQ - Air-sea enthalpy disequilibrium component of sensible heat flux feedback (J^2/(s m^4))
22. TGEN (function of only f,m) - Day of tropical cyclogenesis in high-f simulations
23. TLMI (function of only f,m) - Day of lifetime maximum intensity for tropical cyclones in high-f simulations
