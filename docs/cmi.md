# Climate Moisture Index

Canadian BEACONs Project, University of Alberta

September 9, 2015

## Description

Climate moisture index (CMI) quantifies the relationship between climate
and vegetation by tracking moisture and temperature in forests to
predict how well forests will grow. Globally, forest distribution is
influenced by bioclimatic variables and humidity gradients (Krishnaswamy
et al. 2009). Climate has a significant influence on vegetation, and
feedbacks of vegetation on local climate may be important (Mack et al.
2005). This relationship may be particularly relevant in the boreal
region, where large intact forests are still primarily influenced by
natural processes such as climate and disturbance. CMI is a simple index
for assessing moisture variation and drought severity in remote forested
regions where long-term climate data are typically limited to
temperature and precipitation (Hogg 1994, 1997). The index is calculated
from weather data, including the input of moisture from rain and snow,
and the losses from evaporation and transpiration i.e., water vapour
released from the leaves of trees and other vegetation: 

CMI = P -- PET (cm/year)

where P is the mean annual precipitation (including rain and snow) and
PET is the annual potential evapotranspiration. PET is estimated using
the simplified Penman-Monteith method which requires monthly
temperatures (mean maximum and minimum daily temperatures); monthly
values are summed to derive an annual PET which is subtracted from the
annual precipitation (Hogg 1994, 1997). Positive values of CMI indicate
an excess of precipitation while negative values indicate a
precipitation deficit. CMI has been applied in studies of drought
impacts on forests in western Canada (e.g., Hogg et al. 2002, Volney et
al. 2005), projections of future climate change impacts (e.g. Hogg &
Hurdle 1995, Price et al. 2013), and reviews of options for adaptation
(e.g., Hogg & Bernier 2005, Lempriere et al. 2008).

## Data Sources

Three types of CMI models (gridded maps) are available (Table 1): 1)
long-term averages (30-year normals), 2) annual historical maps for the
period 1901-2010, and 3) projected future maps (annual and 30-year
normals) based on several IPCC climate scenarios for the period
2002--2100.

Download:

-   NRCAN - <ftp://fluxnet:spatial@ftp.nofc.cfs.nrcan.gc.ca/canada-10km/cmi/>
-   ClimateNA - <http://tinyurl.com/ClimateNA>
-   ClimateWNA - <http://tinyurl.com/ClimateWNA>

Table 1. Summary of available datasets and their characteristics.

  **Name**     **Extent**   **Resolution**   **Type**     **Time step**   **Time period covered**
  ------------ ------------ ---------------- ------------ --------------- ------------------------------------
  NRCAN        Canada       10 km^2^         normal       30-yr average   1961--1990, 1971--2000, 1981--2010
                                             historical   annual          1901--2010
                                             projected    annual          2002-2100
  ClimateNA    NA           4 km^2^          normal       30-yr average   1961-1990
                                             projected    30-yr average   2011-2040, 2031-2070, 2071-2100
  ClimateWNA   western NA   1 km^2^          normal       30-yr average   1961-1990
                                             projected    30-yr average   2011-2040, 2031-2070, 2071-2100

## Data Processing

**ArcGIS -- Creating a regional CMI raster**

The following steps will extract a subset of the selected CMI raster
(ClimateWNA 1-km^2^ dataset) and ensure it is in the appropriate
regional projection and scale (spatial extent and resolution).

1.  Start a new ArcGIS project and add a raster boundary map for the study region. The raster should have the desired properties e.g., spatial extent, resolution, coordinate system.
2.  Set the Environment Settings (i.e., Output Coordinate, Processing Extent, and Raster Analysis) to match those of the study region raster.
3.  Use the \"Extract by Mask\" function to extract the required area from the CMI tiff file. Accept the default "Output raster".
4.  Resample to 250-m resolution.

**Box 1. Sample Python code to create regional CMI rasters using A2
ensemble datasets from ClimateWNA at a 1km resolution (Table 1).**

```python
import arcpy
from arcpy import env
from arcpy.sa import \*
arcpy.CheckOutExtension(\"Spatial\")
bnd = \"bnd.tif\"
cmi6190 = \"NORM\_6190\_CMI.asc\"
cmi2020 = \"ENSEMBLE\_A2\_2020s\_CMI.asc\"
cmi2050 = \"ENSEMBLE\_A2\_2050s\_CMI.asc\"
cmi2080 = \"ENSEMBLE\_A2\_2080s\_CMI.asc\"
out6190 = \"cmi\_a2\_6190.tif\"
out2020 = \"cmi\_a2\_2020.tif\"
out2050 = \"cmi\_a2\_2050.tif\"
out2080 = \"cmi\_a2\_2080.tif\"
env.overwriteOutput = True
env.workspace = env.scratchFolder
bndPrj = arcpy.Describe(bnd).spatialReference
arcpy.env.outputCoordinateSystem = bndPrj
env.extent = bnd
env.snapRaster = bnd
env.cellSize = bnd
out = \[out6190,out2020,out2050,out2080\]
i = 0
for (cmi in \[cmi6190,cmi2020,cmi2050,cmi2080\]:
tmp1 = ExtractByMask(cmi, bnd)
tmp1.save(out\[i\])
i = i + 1
```

## NWB LCC Datasets

The master CMI datasets (Table 1; ClimateWNA 1-km^2^ resampled to 250-m)
are located on the BEACONs Dropbox and cover the entire NWB LCC plus
surrounding areas to allow for analyses that extend beyond the study
region i.e., in some cases benchmark construction may extend beyond an
ecoregion to satisfy hydrology and size requirements. Subsets of this
dataset were extracted to the NWB LCC boundary and to each ecoregion and
ecoregion + HUC or ecoregion + FDA.

250-m dataset:

-   Dropbox (BEACONs)/NWB LCC/gisdata/criteria/nwb\_lcc\_plus/250m/cmi\_a2\_6190.tif
-   Dropbox (BEACONs)/NWB LCC/gisdata/criteria/nwb\_lcc\_plus/250m/cmi\_a2\_2020.tif
-   Dropbox (BEACONs)/NWB LCC/gisdata/criteria/nwb\_lcc\_plus/250m/cmi\_a2\_2050.tif
-   Dropbox (BEACONs)/NWB LCC/gisdata/criteria/nwb\_lcc\_plus/250m/cmi\_a2\_2080.tif

1-km^2^ dataset:

-   Dropbox (BEACONs)/NWB LCC/gisdata/criteria/nwb\_lcc\_plus/1000m/cmi\_a2\_6190.tif
-   Dropbox (BEACONs)/NWB LCC/gisdata/criteria/nwb\_lcc\_plus/1000m/cmi\_a2\_2020.tif
-   Dropbox (BEACONs)/NWB LCC/gisdata/criteria/nwb\_lcc\_plus/1000m/cmi\_a2\_2050.tif
-   Dropbox (BEACONs)/NWB LCC/gisdata/criteria/nwb\_lcc\_plus/1000m/cmi\_a2\_2080.tif

![](figures/cmi_nwb.png){width="6.489583333333333in" height="5.010416666666667in"}

Figure 1. Distribution of 1-km^2^ resolution CMI (1961-1990 normal) within the NWB LCC and surrounding regions.

## References

Fisher et al. 2011. ET come home: potential evapotranspiration in
geographical ecology. Global Ecology and Biogeography.

Hamann, A. and Wang, T., Spittlehouse, D.L., and Murdock, T.Q. 2013. A
comprehensive, high-resolution database of historical and projected
climate surfaces for western North America. Bulletin of the American
Meteorological Society 94: 1307--1309.

Hogg, E.H. 1994. Climate and the southern limit of the western Canadian
boreal forest. Canadian Journal of Forest Research 24: 1835--1845.

Hogg, E.H. 1997. Temporal scaling of moisture and the forest grassland
boundary in Western Canada. Agricultural and Forest Meteorology 84:
115--122.

Hogg, E. H., J.P. Brandt and B. Kochtubajda. 2002. Growth and dieback of
aspen forests in northwestern Alberta, Canada, in relation to climate
and insects. Canadian Journal of Forest Research 32: 823--832.

Hogg, E.H., Bernier, P.Y., 2005. Climate change impacts on drought-prone
forests in western Canada. Forestry Chronicle 81: 675--682.

Kriticos, D.J., B.L. Webber, A. Leriche, N. Ota, I. Macadam, J. Bathols
and J.K. Scott. 2012. CliMond: global high resolution historical and
future scenario climate surfaces for bioclimatic modelling. Methods in
Ecology and Evolution

Lempriere, T.C., Bernier, P.Y., Carroll, A.L., Flannigan, M.D.,
Gilsenan, R.P., McKenney, D.W., Hogg, E.H., Pedlar, J.H., and Blain, D.
2008. The importance of forest sector adaptation to climate change. Nat.
Resour. Can., Can. For. Serv., North. For. Cent., Edmonton, Alta. Inf.
Rep. NOR-X-416E.

McKenney, D., Pedlar, J., Hutchinson, M., Papadopol, P., Lawrence, K.,
Campbell, K., Milewska, E., Hopkinson, R.F., Price, D., 2013. Spatial
climate models for Canada' s forestry community. The Forestry Chronicle
89(5): 659-663.

Price, D.T., et al. 2013. Anticipating the consequences of climate
change for Canada\'s boreal forest ecosystems. Environmental Reviews 21:
322--365

Volney, W.J.A. et al. 2005. A framework for poplar plantation risk
assessments. Unasylva 221(56): 20-25.

Wang, T., Hamann, A., Spittlehouse, D.L., and Murdock, T.Q. 2012.
ClimateWNA -- High-resolution spatial climate data for western North
America. Journal of Applied Meteorology and Climatology 51: 16--29.
