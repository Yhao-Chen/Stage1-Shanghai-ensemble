# Stage1-Shanghai-ensemble
This repository is created for the coordination of the WRF simulations within the CORDEX FPS URB-RCC framework following [The FPS-URB-RCC protocol](https://docs.google.com/document/d/1ACD8XcMzNjzKCIjTDmOUgNd8JPr2nQOD4LKHHl1U3sc/edit?tab=t.0).

[**7d-test**](./7d-test) simulation, a short 7-day run, is set-up to test the stability and speed of the WRF model with the most complex urban scheme (BEP+BEM; `sf_urban_physics=3`) tuned on by different machines from all the involved [Institutions](T.B.D) running WRF.  

[**STAGE-1**](./STAGE-1) simulations for Shanghai satellite city in East Asia will be performed in order to create a mini-ensemble for FPS URB-RCC Stage1 comparison across the globe. These simulations planned to be centered over the Shanghai region with a period of 10 years.

These experiments use CWC WRF v4.5.1.4
```bash
git clone --recurse-submodules -b v4.5.1.7-devel https://github.com/CORDEX-WRF-community/WRF.git
```

![WRF domains for Shanghai mini-ensemble](https://github.com/Yhao-Chen/Stage1-Shanghai-ensemble/blob/main/STAGE-1/Stage1_Shanghai-ensembel_domains_final.png)
