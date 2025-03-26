# FPS-URB-RCC Test-7d WRF simulation

The first test **Test-7d** run is set to be performed for 14 days (i.e. 2007.07.21-2007.08.05) prior to the [STAGE-1](./STAGE-1) simulation in order to verify if the WRF model with an urban scheme turned on and the LCZ categories can be run successfully by all the groups involved in the Stage1-Shanghai-Ensemble activities, and how fast. Each of the group should use the same setting to perform the run. For that reason all the files necessary to complete the run are prepared and can be downloaded at this [link](https://drive.google.com/file/d/1yDecFagh6e6YIb1y3V74WcIMKO0LaWpv/view?usp=drive_link). 

The downloaded file is a tar file and includes:

## 1. geo_em files 

created with the CGLC_MODIS_LCZ data:
   
```
geo_em.d01.nc
geo_em.d02.nc
```
## 2. Aerosol climatology data created follow the instruction at [link](https://github.com/AEI-CORDyS/aerosols4wrf):
```
AOD_20070720_20070805_d01
AOD_20070720_20070805_d02
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

*[namelist.wps](./namelist.wps)* defines 2 [domains](../Stage1_Shanghai_ensemble_domain.png): ESA-12 d01 - the outer domain in Lambert Conformal projection named EAS-12, and 	YRD-3 d02 - the inner domain centered around Shanghai.
*[namelist.input](./namelist.input)* is set to run with BouLac PBL scheme (`bl_pbl_physics = 8`) and BEP+BEM urban scheme (`sf_urban_physics = 3`). 
```
namelist.wps
namelist.input
```



  
To run the simulations, place the files from (2), (3), (4) and namelist.input from (5) to the `WRF/run` directory, and then run `wrf.exe`:

	# Copy the provided files to the WRF/run directory
	cp AOD202004_d01 AOD202004_d02  \
 		varlist.txt \
		wrfbdy_d01 wrfinput_d01  \
  		wrfinput_d02 wrflowinp_d01 wrflowinp_d02 \
		namelist.input WRF/run
	cd WRF/run
