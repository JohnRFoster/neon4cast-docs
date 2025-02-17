# Theme: Beetle Communities

**What:** Beetle abundance and species richness

**Where:** 47 terrestrial NEON sites that span the diverse ecosystems of the U.S.

**When:** Weekly forecasts for 20 months in the future starting June 30-December 31, 2022; later submissions after the June 30 start are permissible

**Why:** Improve understanding of habitat quality, conservation potential, land-use sustainability, and biodiversity change in response to global change and ecological disturbances

**Who**: Open to any individual or team that registers.

**How**: [REGISTER](https://nd.qualtrics.com/jfe/form/SV_9MJ29y2xNrBOjqZ){target="_blank"} your team and submit forecast. If you registered for the Round 1 (2021) and are using the same team and method then you do not need to re-register.

The video below is an overview of the Beetle Communities Challenge that was recorded for the [2021 Early Career Annual Meeting](https://ecoforecast.org/ecological-forecasting-early-career-annual-meeting/){target="_blank"}

<iframe width="560" height="315" src="https://www.youtube.com/embed/7196wcarMXQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>




## Overview

Biodiversity monitoring is critical for understanding environmental quality, evaluating the sustainability of land-use practices, and forecasting future impacts of global change on ecosystems. Sentinel species give forewarning of environmental risk to humans, so are particularly useful for such monitoring and forecasting efforts because they can provide surrogates for other co-located components of biodiversity (Sauberer et al. 2004). 

Ground beetles (Family: Carabidae) are appropriate candidates for biodiversity monitoring and ecological forecasting as they are well-studied sentinel species that are geographically widespread, and their community dynamics are particularly congruent with the diversity of other invertebrates (Holland 2002; Lundgren & McCravy 2011; Bousquet 2012; Hoekman et al. 2017). Therefore, monitoring carabid communities and forecasting changes in their species richness and abundance can be useful in studying edge effects and habitat quality (Magura 2002), conservation potential (Butterfield 1995), land-use sustainability (Pearce & Venier 2006) and biodiversity change in response to global change and ecological disturbances (Koivula 2011). Most ecological forecasting models are limited in the geographic scale and also suffer from scarcity of temporally extensive data. Further, most existing forecasting efforts focus on a single species (Humphries et al. 2018) with limited community-wide forecasts at the continental scale. Developing forecasts for community-scale metrics (i.e., species richness, abundance) and evaluating such models for accuracy and generalizability can help test our scientific knowledge of spatial (geographical turnover) and temporal (seasonal, inter-annual) carabid community dynamics (Dietze et al. 2018). Such forecasting models can inform regional or local habitat management, identify where biodiversity monitoring efforts should be prioritized, and shed light on what data or modelling techniques are needed to build the best forecasts of ecological dynamics (e.g., can we predict richness or abundance better and why?) (Johansson et al. 2019). 

With the long-term, community-wide, continental-scale data collection through the National Ecological Observatory Network (NEON), 181 data products are available for 81 sites in the US (47 terrestrial, at which carabids are sampled, and 34 aquatic). Fully initiated in 2019, this sampling will continue for 30 years (Schimel et al. 2007; 2011). NEON has effectively removed the previous barriers to community-scale forecasting across a broader geographical realm. 

## Challenge 

This is an open ecological forecasting challenge to forecast carabid species richness, defined as the total number of species, and abundance, defined as the total number of carabid individuals. The forecasts should be done weekly per site for all NEON terrestrial sites with richness being absolute and abundance scaled by the sampling effort. Contributing teams are required to submit a forecast for May-Dec 2022 and Jan-Dec 2023 on June 30, 2022. However, teams are encouraged to update their forecasts on the last day of each month, ending on December 31, 2021, as NEON validation data are released. NEON releases carabid sampling data weekly and no sooner than 60 days after collection, so a model submitted on June 30 can include a forecast for the first week of May, and so forth. Teams may use any open data products as drivers of richness and abundance so long as they are not from the month being forecast, and are made publicly available (minimum of URL, but ideally a script). Potential driver data sources include: NEON site data ([Soil and sediment data](https://www.neonscience.org/data-collection/soils-sediments){target="_blank"}, [Terrestrial Plant data](https://www.neonscience.org/data-collection/terrestrial-plants){target="_blank"}, [weather data](https://www.neonscience.org/data-collection/meteorology){target="_blank"}), NOAA forecasts, and beyond. 

## Data: Targets

The challenge uses the following NEON data product:   
[DP1.10022.001](https://data.neonscience.org/data-products/DP1.10022.001){target="_blank"}: Ground beetles sampled from pitfall traps

A file with previously released NEON data that has been processed into the aggregate “target” variables (richness and abundance) is provided below. The same processing will be applied to new data that are used for forecast evaluation. Further information about data structure, initial code for processing, and example null forecasts is provided in the [neon4cast-beetles GitHub repository](https://github.com/eco4cast/neon4cast-beetles){target="_blank"}. 

Forecasts will be made on a weekly basis for the abundance of beetles at a given NEON site at a given month (‘abundance’) and the observed species richness (n, number of species) of carabid beetles at each NEON site, each month.  

### Abundance of beetles (abundance)

**Definition**

Total number of carabid individuals per trap-night, estimated each week of the year at 
each NEON site

**Motivation**

A forecast prediction can be compared against only measured data (i.e. counts) and not latent variables (i.e. true carabid abundance), which are only inferred under specific model assumptions. However, raw count of beetles found in a particular trap depends on many other drivers than local abundance; in particular, the sampling effort. To avoid the need to accurately predict the sampling effort, we compute a target variable as counts per trap-night (number of nights each trap was set at the site; also called ‘catch per unit effort’). We chose this to define this variable in terms of total carabid abundance, rather than resolving to particular taxonomy (in contrast to species-specific relative abundance) because it simplifies issues related to taxonomic resolution of unpinned samples, data latency, and the choice of focal species. As supported by literature (Hoekman et al. 2017 and literature cited therein), we believe that abundance of the beetle family as a whole is an ecologically relevant metric.  We considered predictions aggregated to the site level (rather than predicting individual traps or individual plots) to be both the most ecologically meaningful and simplest choice.  Traps are typically collected every two weeks. Submitting a forecast for every week avoids the need to predict which weeks of the year collection does or does not occur.  See <https://github.com/eco4cast/neon4cast-beetles/blob/master/02_targets.R> for a programmatic definition of how the abundance metric is defined.

### Species richness (n)

**Definition**

Total number of unique ‘species’ in a sampling bout for each NEON site each week. For this challenge, we define ‘species’ as the taxonomic unit closest to species (e.g., species, genus, morphospecies) for each individual since not all identifications in the raw data are strictly at species-level.

**Motivation**

A forecast prediction can be compared against only measured data (i.e. observed count of taxonomic units) and not latent variables (i.e. count of species), which are only inferred under specific model and taxonomic assumptions. The number of unique taxonomic identities of beetles in a trap depends on many drivers, including sampling effort. As demonstrated by species rarefaction curves in ecology, the more time a trap is left out, the more individual beetles will fall in, and thus the more species can be expected. However, since perfect species-level data are not available to us and to keep the forecasted variables from being overly derived, we define the target variable as the total number of unique ‘species’ per week per NEON site. For this challenge, we chose to define ‘species’ as the taxonomic unit closest to species (e.g., species, genus, morphospecies) since not all identifications in the raw data are strictly at species-level. Species identifications will be used for individuals identified to sub-species level, as these are uncommon in the raw data. NEON taxonomists identify individuals as morphologically distinct units. Thus, it is reasonable to assert that the count of finest morphologically distinct identification (e.g., species, genus, morphospecies) is biologically meaningful, and thus the count of these is an important focal forecast variable.  We focus on the NEON site as the spatial resolution and weekly intervals as the temporal resolution for the same reasons stated in the abundance metric. See <https://github.com/eco4cast/NEON-community-forecast/blob/master/02_targets.R> for a programmatic definition of how the richness metric is defined.

### Focal sites

All 47bNEON terrestrial sites are included

Information on the sites can be found here:


```r
site_data <- readr::read_csv("https://raw.githubusercontent.com/eco4cast/neon4cast-beetles/master/Beetles_NEON_Field_Site_Metadata_20210928.csv")
```


|siteID |site name                                                   |vegetation type                                                                | latitude| longtitude|NEON site URL                                |
|:------|:-----------------------------------------------------------|:------------------------------------------------------------------------------|--------:|----------:|:--------------------------------------------|
|ABBY   |Abby Road NEON                                              |Evergreen Forest&#124;Grassland/Herbaceous&#124;Shrub/Scrub                    | 45.76244| -122.33032|https://www.neonscience.org/field-sites/abby |
|BARR   |Utqiaġvik NEON                                              |Emergent Herbaceous Wetlands                                                   | 71.28241| -156.61936|https://www.neonscience.org/field-sites/barr |
|BART   |Bartlett Experimental Forest NEON                           |Deciduous Forest&#124;Evergreen Forest&#124;Mixed Forest                       | 44.06389|  -71.28737|https://www.neonscience.org/field-sites/bart |
|BLAN   |Blandy Experimental Farm NEON                               |Deciduous Forest&#124;Pasture/Hay                                              | 39.03370|  -78.04179|https://www.neonscience.org/field-sites/blan |
|BONA   |Caribou-Poker Creeks Research Watershed NEON                |Deciduous Forest&#124;Evergreen Forest&#124;Mixed Forest&#124;Woody Wetlands   | 65.15401| -147.50258|https://www.neonscience.org/field-sites/bona |
|CLBJ   |Lyndon B. Johnson National Grassland NEON                   |Deciduous Forest&#124;Grassland/Herbaceous                                     | 33.40123|  -97.57000|https://www.neonscience.org/field-sites/clbj |
|CPER   |Central Plains Experimental Range NEON                      |Grassland/Herbaceous                                                           | 40.81554| -104.74559|https://www.neonscience.org/field-sites/cper |
|DCFS   |Dakota Coteau Field Site NEON                               |Grassland/Herbaceous                                                           | 47.16165|  -99.10656|https://www.neonscience.org/field-sites/dcfs |
|DEJU   |Delta Junction NEON                                         |Evergreen Forest&#124;Shrub/Scrub&#124;Woody Wetlands                          | 63.88112| -145.75136|https://www.neonscience.org/field-sites/deju |
|DELA   |Dead Lake NEON                                              |Evergreen Forest&#124;Woody Wetlands                                           | 32.54173|  -87.80388|https://www.neonscience.org/field-sites/dela |
|DSNY   |Disney Wilderness Preserve NEON                             |Pasture/Hay&#124;Woody Wetlands                                                | 28.12505|  -81.43619|https://www.neonscience.org/field-sites/dsny |
|GRSM   |Great Smoky Mountains National Park NEON                    |Deciduous Forest&#124;Evergreen Forest                                         | 35.68896|  -83.50195|https://www.neonscience.org/field-sites/grsm |
|GUAN   |Guanica Forest NEON                                         |Evergreen Forest                                                               | 17.96955|  -66.86870|https://www.neonscience.org/field-sites/quan |
|HARV   |Harvard Forest & Quabbin Watershed NEON                     |Deciduous Forest&#124;Evergreen Forest&#124;Mixed Forest&#124;Woody Wetlands   | 42.53691|  -72.17265|https://www.neonscience.org/field-sites/harv |
|HEAL   |Healy NEON                                                  |Dwarf Scrub&#124;Evergreen Forest&#124;Shrub/Scrub                             | 63.87580| -149.21335|https://www.neonscience.org/field-sites/heal |
|JERC   |The Jones Center At Ichauway NEON                           |Cultivated Crops&#124;Deciduous Forest&#124;Evergreen Forest&#124;Mixed Forest | 31.19484|  -84.46862|https://www.neonscience.org/field-sites/jerc |
|JORN   |Jornada Experimental Range NEON                             |Shrub/Scrub                                                                    | 32.59069| -106.84254|https://www.neonscience.org/field-sites/jorn |
|KONA   |Konza Prairie Agroecosystem NEON                            |Cultivated Crops                                                               | 39.11045|  -96.61293|https://www.neonscience.org/field-sites/kona |
|KONZ   |Konza Prairie Biological Station NEON                       |Deciduous Forest&#124;Grassland/Herbaceous                                     | 39.10077|  -96.56307|https://www.neonscience.org/field-sites/konz |
|LAJA   |Lajas Experimental Station NEON                             |Cultivated Crops&#124;Grassland/Herbaceous&#124;Pasture/Hay                    | 18.02126|  -67.07689|https://www.neonscience.org/field-sites/laja |
|LENO   |Lenoir Landing NEON                                         |Deciduous Forest&#124;Woody Wetlands                                           | 31.85386|  -88.16118|https://www.neonscience.org/field-sites/leno |
|MLBS   |Mountain Lake Biological Station NEON                       |Deciduous Forest                                                               | 37.37831|  -80.52485|https://www.neonscience.org/field-sites/mlbs |
|MOAB   |Moab NEON                                                   |Evergreen Forest&#124;Shrub/Scrub                                              | 38.24828| -109.38827|https://www.neonscience.org/field-sites/moab |
|NIWO   |Niwot Ridge NEON                                            |Evergreen Forest&#124;Grassland/Herbaceous                                     | 40.05425| -105.58237|https://www.neonscience.org/field-sites/niwo |
|NOGP   |Northern Great Plains Research Laboratory NEON              |Grassland/Herbaceous                                                           | 46.76972| -100.91535|https://www.neonscience.org/field-sites/nogp |
|OAES   |Marvin Klemme Range Research Station NEON                   |Grassland/Herbaceous&#124;Shrub/Scrub                                          | 35.41060|  -99.05878|https://www.neonscience.org/field-sites/oaes |
|ONAQ   |Onaqui NEON                                                 |Evergreen Forest&#124;Shrub/Scrub                                              | 40.17760| -112.45245|https://www.neonscience.org/field-sites/onaq |
|ORNL   |Oak Ridge NEON                                              |Deciduous Forest&#124;Evergreen Forest&#124;Pasture/Hay                        | 35.96413|  -84.28259|https://www.neonscience.org/field-sites/ornl |
|OSBS   |Ordway-Swisher Biological Station NEON                      |Emergent Herbaceous Wetlands&#124;Evergreen Forest&#124;Woody Wetlands         | 29.68928|  -81.99343|https://www.neonscience.org/field-sites/osbs |
|PUUM   |Pu'u Maka'ala Natural Area Reserve NEON                     |Evergreen Forest                                                               | 19.55309| -155.31731|https://www.neonscience.org/field-sites/puum |
|RMNP   |Rocky Mountains NEON                                        |Evergreen Forest                                                               | 40.27590| -105.54596|https://www.neonscience.org/field-sites/rmnp |
|SCBI   |Smithsonian Conservation Biology Institute NEON             |Deciduous Forest&#124;Evergreen Forest&#124;Pasture/Hay                        | 38.89292|  -78.13949|https://www.neonscience.org/field-sites/scbi |
|SERC   |Smithsonian Environmental Research Center NEON              |Cultivated Crops&#124;Deciduous Forest                                         | 38.89013|  -76.56001|https://www.neonscience.org/field-sites/serc |
|SJER   |San Joaquin Experimental Range NEON                         |Evergreen Forest&#124;Grassland/Herbaceous&#124;Shrub/Scrub                    | 37.10878| -119.73228|https://www.neonscience.org/field-sites/sjer |
|SOAP   |Soaproot Saddle NEON                                        |Evergreen Forest&#124;Shrub/Scrub                                              | 37.03337| -119.26219|https://www.neonscience.org/field-sites/soap |
|SRER   |Santa Rita Experimental Range NEON                          |Shrub/Scrub                                                                    | 31.91068| -110.83549|https://www.neonscience.org/field-sites/srer |
|STEI   |Steigerwaldt-Chequamegon NEON                               |Deciduous Forest&#124;Mixed Forest&#124;Woody Wetlands                         | 45.50894|  -89.58637|https://www.neonscience.org/field-sites/stei |
|STER   |North Sterling NEON                                         |Cultivated Crops                                                               | 40.46189| -103.02929|https://www.neonscience.org/field-sites/ster |
|TALL   |Talladega National Forest NEON                              |Deciduous Forest&#124;Evergreen Forest&#124;Mixed Forest                       | 32.95047|  -87.39326|https://www.neonscience.org/field-sites/tall |
|TEAK   |Lower Teakettle NEON                                        |Evergreen Forest&#124;Shrub/Scrub                                              | 37.00583| -119.00602|https://www.neonscience.org/field-sites/teak |
|TOOL   |Toolik Field Station NEON                                   |Dwarf Scrub&#124;Shrub/Scrub                                                   | 68.66109| -149.37047|https://www.neonscience.org/field-sites/tool |
|TREE   |Treehaven NEON                                              |Deciduous Forest&#124;Evergreen Forest&#124;Mixed Forest&#124;Woody Wetlands   | 45.49369|  -89.58571|https://www.neonscience.org/field-sites/tree |
|UKFS   |University of Kansas Field Station NEON                     |Deciduous Forest&#124;Pasture/Hay                                              | 39.04043|  -95.19215|https://www.neonscience.org/field-sites/ukfs |
|UNDE   |University of Notre Dame Environmental Research Center NEON |Deciduous Forest&#124;Mixed Forest&#124;Woody Wetlands                         | 46.23391|  -89.53725|https://www.neonscience.org/field-sites/unde |
|WOOD   |Chase Lake National Wildlife Refuge NEON                    |Emergent Herbaceous Wetlands&#124;Grassland/Herbaceous                         | 47.12820|  -99.24133|https://www.neonscience.org/field-sites/wood |
|WREF   |Wind River Experimental Forest NEON                         |Evergreen Forest                                                               | 45.82049| -121.95191|https://www.neonscience.org/field-sites/wref |
|YELL   |Yellowstone National Park NEON                              |Evergreen Forest&#124;Grassland/Herbaceous&#124;Shrub/Scrub                    | 44.95348| -110.53914|https://www.neonscience.org/field-sites/yell |

### Target data calculation

Ground beetle data are collected at each NEON site every two weeks throughout the sampling season. The sampling season is defined based on measures of growing season, including vegetation indices, phenology, and degree days, for a maximum of 13 bouts per site during which the 10-day average low temperature at the site is >4°C.  

Samples are collected from pitfall traps placed at each of the cardinal directions within the 10 plots per site representative of up to three dominant vegetation types. Four traps were placed from 2014-2017 and from 2018 onward the northward plot was eliminated leaving three traps for each plot. Ground beetles from the pitfall traps are removed, sorted, and identified to the lowest possible taxonomic rank or morphospecies. A subset of individuals (up to 467 per site and year) are sent to taxonomic experts for subsequent identification with priority on individuals for which species-level identification was not able to be assigned. Further detail can be found in the NEON Ground Beetle User Guide. 

Raw (NEON L1 ground beetle data product [DP1.10022.001](https://data.neonscience.org/data-products/DP1.10022.001){target="_blank"}) are accessible via the NEON data portal, via the NEON API, via R using the neonUtilties package, and via R using neonStore::neon_download. The raw data is also available through the NEON data portal with archived copies at https://data.ecoforecast.org/minio/neonstore. 

The raw data is processed to generate total abundance and richness per week per NEON site. All data in the supplied file is available to build and evaluate models before submitting a forecast to challenge.  Once new data becomes available, the data are appended to the existing file.  Within the challenge scoring, only the new data are used to evaluate previously submitted forecasts.

As part of our reproducible workflow, we provide an R script for producing derived tables of total abundance and richness from the raw NEON data. Our workflow gives preference to expert taxonomist identifications when available. Since expert taxonomy lags behind identifications from the sorting and pinning process, newer data will not be updated with expert taxonomy. The abundance table gives total abundance at each site for each week. The richness table gives an aggregate count of the number of ‘species’ at each site in each week. 

Note: The table includes all data that NEON has collected and can be used for building and training models (new data will be posted after forecasts are submitted)

### Target file

The code use to process the raw data to the evaluation data can be found here:
https://github.com/eco4cast/NEON-community-forecast/blob/master/02_targets.R

Here is the format of the target file


```r
readr::read_csv("https://data.ecoforecast.org/targets/beetles/beetles-targets.csv.gz", guess_max = 1e6)
```

```
## # A tibble: 3,177 × 4
##    siteID time       abundance richness
##    <chr>  <date>         <dbl>    <dbl>
##  1 ABBY   2016-09-12    1.05         14
##  2 ABBY   2016-09-26    4.45         13
##  3 ABBY   2017-05-01    0.0554       10
##  4 ABBY   2017-05-15    0.180        19
##  5 ABBY   2017-05-29    0.425        19
##  6 ABBY   2017-06-12    0.25         18
##  7 ABBY   2017-06-26    0.271        22
##  8 ABBY   2017-07-10    0.148        15
##  9 ABBY   2017-07-24    0.105        14
## 10 ABBY   2017-08-07    0.116        16
## # … with 3,167 more rows
```

The table has the following columns:  

- `siteID`: NEON site ID    
- `time`: YYYY-MM-DD (the Monday marking the week of sample collection (for training data) or forecast (submission). Per ISO standards, Monday marks the first day of each week.)   
- `abundance`: abundance of beetles    
- `richness`: species richness    

## Timeline

The timeline is determined by the data latency provided by NEON. NEON carabid pitfall trap data is released weekly with a latency of at least 60 days after collection. Weekly forecasts were chosen to best match up with NEON’s weekly release of carabid data. 

The challenge will begin June 30, 2022 at 11:59 Eastern Standard Time (UTC−05:00) and run through December 31, 2022. Subsequent forecasts are due at 11:59 EST on the final day of each month.

As an example, carabid pitfall trap data released in the last week of June would include data as recent as the last week of April. Thus, a model submitted in the last week of June could include forecasts from May onwards. Then, the forecast update submitted at the end of July can use new May data to help refine June forecasts, or forecasts following June, depending on what drivers are used. The July forecast update is due by 11:59 pm EST on July 31. Forecasts updates will not be considered for weeks where NEON validation data has already been released (i.e., no May forecast updates may be submitted on July 31) or for weeks when no NEON carabid data is available. 

![](images/June2021_Calendar.jpg)
![](images/July2021_Calendar.jpg)
Pitfall traps are collected and reset every 2 weeks throughout the growing season. Due to weather and conditions beyond the field team’s control, this collection schedule may not be followed. Thus, the exact collection dates cannot be known until they have happened. Field data are made publicly available on the data portal as the `bet_fielddata` dataframe no sooner than 14 days after collection. Teams can use `bet_fielddata` to inform the actual collection schedule. Data with parataxonomist identifications are made publicly available on the data portal as the bet_sorting dataframe no sooner than 60 days after collection. Data are released on the NEON data portal weekly, but may be released on any day of the week. The forecast schedule follows the ISO week standard with weeks starting on Mondays.

## Design team

Anna Spiers, University of Colorado, Boulder  
Carl Boettiger, University of California, Berkeley  
Tad Dallas, Louisiana State University  
Nico Franz, NEON Biorepository at Arizona State University  
Kari Norman, University of California, Berkeley  
Thilina Surasinghe, Bridgewater State University  
Brett Melbourne, University of Colorado, Boulder  
Eric Sokol, NEON  
Kelsey Yule, NEON Biorepository at Arizona State University  

## Partners

The challenge is hosted by the Ecological Forecasting Initiative (EFI; https://ecoforecast.org/) and its U.S. National Science Foundation sponsored Research Coordination Network (EFI-RCN; https://ecoforecast.org/rcn/).

Data used in the challenge from National Ecological Observatory Network (NEON): https://www.neonscience.org/. 

## References

Bousquet, Y. (2012) Catalogue of Geadephaga (Coleoptera: Adephaga) of America, north of Mexico. ZooKeys 245: 1-1722. https://doi.org/10.3897/zookeys.245.3416

Butterfield, J., Luff, M., Baines, M., Eyre, M. (1995) Carabid beetle communities as indicators of conservation potential in upland forests. Forest Ecology and Management 79, 63-77. 
https://doi.org/10.1016/0378-1127(95)03620-2

Dietze, M.C., Fox, A., Beck-Johnson, L.M., Betancourt, J.L., Hooten, M.B., Jarnevich, C.S., Keitt, T.H., Kenney, M.A., Laney, C.M., Larsen, L.G. (2018) Iterative near-term ecological forecasting: Needs, opportunities, and challenges. Proceedings of the National Academy of Sciences 115, 1424-1432. https://doi.org/10.1073/pnas.1710231115

Gneiting, T., & Raftery, A. E. (2007). Strictly proper scoring rules, prediction, and estimation. Journal of the American Statistical Association, 102(477), 359–378. https://doi.org/10.1198/016214506000001437

Hoekman, D., LeVan, K.E., Gibson, C., Ball, G.E., Browne, R.A., Davidson, R.L., Eriwin, T.L., Knisley, C.B., LaBonte, J.R., Lundgren, J., Maddison, D.R., Moore, W., Niemela, J., Ober, K.A., Pearson, D.L. Spence, J.R., Will, K., Work, T. (2017) Design for ground beetle abundance and diversity sampling within the National Ecological Observatory Network. Ecosphere, 8(4), e01744. https://doi.org/10.1002/ecs2.1744

Holland, J.M. (2002) The agroecology of carabid beetles. Intercept Limited, Andover.

Humphries, G.R., Che-Castaldo, C., Bull, P., Lipstein, G., Ravia, A., Carrión, B., Bolton, T., Ganguly, A., Lynch, H.J. (2018) Predicting the future is hard and other lessons from a population time series data science competition. Ecological Informatics 48, 1-11. https://doi.org/10.1016/j.ecoinf.2018.07.004

Johansson, M.A., Apfeldorf, K.M., Dobson, S., Devita, J., Buczak, A.L., Baugher, B., Moniz, L.J., Bagley, T., Babin, S.M., Guven, E. (2019) An open challenge to advance probabilistic forecasting for dengue epidemics. Proceedings of the National Academy of Sciences 116, 24268-24274. https://doi.org/10.1073/pnas.1909865116

Koivula, M.J. (2011) Useful model organisms, indicators, or both? Ground beetles (Coleoptera, Carabidae) reflecting environmental conditions. ZooKeys, 287-317. https://doi.org/10.3897/zookeys.100.1533

Lundgren, J., McCravy, K. (2011) Carabid beetles (Coleoptera: Carabidae) of the Midwestern United States: A review and synthesis of recent research. Terrestrial arthropod reviews 4, 63-94. https://doi.org/10.1163/187498311X565606

Magura, T. (2002) Carabids and forest edge: spatial pattern and edge effect. Forest Ecology and Management 157, 23-37. https://doi.org/10.1016/S0378-1127(00)00654-X

Pearce, J.L., Venier, L.A. (2006) The use of ground beetles (Coleoptera: Carabidae) and spiders (Araneae) as bioindicators of sustainable forest management: A review. Ecological Indicators 6, 780-793. https://doi.org/10.1016/j.ecolind.2005.03.005

Sauberer, N., Zulka, K.P., Abensperg-Traun, M., Berg, H.-M., Bieringer, G., Milasowszky, N., Moser, D., Plutzar, C., Pollheimer, M., Storch, C. (2004) Surrogate taxa for biodiversity in agricultural landscapes of eastern Austria. Biological Conservation 117, 181-190. https://doi.org/10.1016/S0006-3207(03)00291-X

Schimel, D., Hargrove, W., Hoffman, F., MacMahon, J. (2007) NEON: a hierarchically designed national ecological network. Frontiers in Ecology and the Environment 5, 59-59. https://doi.org/10.1890/1540-9295(2007)5[59:NAHDNE]2.0.CO;2

Schimel, D., Keller, M., Berukoff, S., Hufft, R., Loescher, H., Powell, H., Kampe, T., Moore, D., Gram, W. (2011) NEON Science Strategy: Enabling Continental-Scale Ecological Forecasting. https://www.neonscience.org/sites/default/files/basic-page-files/NEON_Strategy_2011u2_0.pdf
