# FPS-URB-RCC stage1 Shanghai-ensemble 7d-test WRF simulation

The first test **7d-test** run is set to be performed for 7 days (i.e. 2017.07.18-2017.07.27, the first three days for spin-up) prior to the [STAGE-1](./STAGE-1) simulation 
in order to verify if the WRF model with an urban scheme turned on and the LCZ categories can be run successfully by all the groups involved in the Stage1-Shanghai-Ensemble 
activities, and how fast. Each of the group should use the same setting to perform the run. For that reason all the files necessary to complete the run are prepared and can 
be downloaded at this **link**(in progress).

The downloaded file is a tar file and includes:

## 1. geo_em files 

The geo_em.d0X.nc is created via ./geogrid.exe following the default setup in [namelist.wps](./7d-test/namelist.wps) with 21 landuse categories. The other geo_em files were 
created by w2w tool to implement the LCZ categories (51-60) from **LCZ dataset**(T.B.D):
   
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
## 2. Aerosol climatology data created follow the instruction at [link](https://github.com/AEI-CORDyS/aerosols4wrf):
```
AOD_20170718_20170728_d01
AOD_20170718_20170728_d02
```
## 3. I/O fields txt file

The file that deletes/adds variables from/to the output if not changed in the Registry files (`iofields_filename` in namelist.input):
```
varlist.txt
```
## 4. Input and boundary files:
```
wrfbdy_d01
wrfinput_d01
wrfinput_d02
wrflowinp_d01
wrflowinp_d02
```
## 5. namelist.wps and namelist.input:

*[namelist.wps](./7d-test/namelist.wps)* defines 2 [domains](../Stage1_Shanghai-ensemble_domain.pngs): ESA-12 d01 - the outer domain in Lambert Conformal projection named EAS-12, 
and 	YRD-3 d02 - the inner domain centered around Shanghai.
*[namelist.input](./7d-test/namelist.input)* is set to run with BouLac PBL scheme (`bl_pbl_physics = 8`) and BEP+BEM urban scheme (`sf_urban_physics = 3`). 
```
namelist.wps
namelist.input
```
  
To run the simulations, place the files from (2), (3), (4) and namelist.input from (5) to the `WRF/run` directory, and then run `wrf.exe`:

	# Copy the provided files to the WRF/run directory
	cp AOD_20070720_20070805_d01 AOD_20070720_20070805_d02  \
 		varlist.txt \
		wrfbdy_d01 wrfinput_d01  \
  		wrfinput_d02 wrflowinp_d01 wrflowinp_d02 \
		namelist.input WRF/run
	cd WRF/run
