# FPS-URB-RCC Stage-1 Shanghai-ensemble WRF simulation

Here are the general configuration and input files for Shanghai-ensemble simulations from 2015-2024 as following:

## 1. [geo_em files](https://drive.google.com/file/d/1xdK4E_XHA7jMUqOUfGervmThU0r0429e/view?usp=drive_link) 

created by w2w tool with the LCZ map of Yangtze River Delta urban agglomerations from [Wang's](https://www.mdpi.com/2072-4292/15/12/3111) datasets:
   
```
geo_em.d01.nc
geo_em.d01_LCZ_extent.nc
geo_em.d01_LCZ_params.nc
geo_em.d01_NoUrban.nc
geo_em.d02.nc
geo_em.d02_LCZ_extent.nc
geo_em.d02_LCZ_params.nc
geo_em.d02_NoUrban.nc
```
The `geo_em.d0X.nc` is the original one without LCZ information, created just by running `./geogrid.exe` in WPS. The `geo_em.d0X_LCZ_extent.nc` is the updated LULC with Wang's dataset but without any LCZ information, and the LULC types of urban grids are all 13. 
The `geo_em.d0X_NoUrban.nc` replaces the urban LULC to natural one. The `geo_em.d0X_LCZ_params.nc` contains the updated LCZ information. If you want to use one of the urban LULC conditions for simulation, please copy one of them and rename them into format `geo_em.d0x.nc` in your WPS dir, 
and then running `ungrib.exe` and `metgrid.exe` to create `met_em` files.

## 2. [Aerosol climatology data](https://drive.google.com/file/d/1kPbRUrIXuw8PmvQbSDM173Arbf7fPiIa/view?usp=drive_link) created follow the [instruction](https://github.com/AEI-CORDyS/aerosols4wrf):
```
AOD_20140101_20241231_d01
AOD_20140101_20241231_d02
```

## 3. I/O fields txt file

The file that deletes/adds variables from/to the output if not changed in the Registry files (`iofields_filename` in namelist.input):
```
varlist.txt
```

## 4. URBPARAM_LCZ.TBL

The default urban morphological parameters.
```
URBPARAM_LCZ.TBL
```

## 5. namelist.wps and namelist.input:

*[namelist.wps](./namelist.wps)* defines 2 [domains](./Stage1_Shanghai_ensemble_domains_final.png): ESA-12 d01 - the outer domain in Lambert Conformal projection named EAS-12, and YRD-4 d02 - the inner domain centered around Shanghai.
*[namelist.input](./namelist.input)* is set to run with BouLac PBL scheme (`bl_pbl_physics = 8`) and BEP+BEM urban scheme (`sf_urban_physics = 3`). 
```
namelist.wps
namelist.input
```


Finally, to run the simulations, the wrfinput_d0X, wrfbdy_d01 and wrflowinp_d0X should be created by running real.exe in `WRF/run` after finishing generating met_em files in WPS, and then run `wrf.exe`.
