Project Description:
This project file contains R Scripts created for a project on <i>Juglans cinerea</i>, also known as butternut. We are interested in determining how butternut's range has shifted in response to modern and past climate changes. Hoban et al. (2010) determined that butternut's genetic patterns were most inluenced by glacial patterns, so this study added individuals sampled by the Jeanne Romero-Severson and Martin William's labs. We also wanted to more specifically examine past sources of data to identify the range shifts of this taxon. Therefore the main focuses on this project are listed here: 

![Alt text](Images/worflow_github.jpg?raw=true "Flowchart for project") 

The code written for performing two of the steps are in this Github; code for downloading, projecting, and creating pollen and glacier maps were created by Alissa Brown (https://github.com/alissab). This repository is split into multiple folders: Archive, Images, SDMs, data_files, genetic_analyses, and genetic_analyses_results

Here are descriptions of what's in each folder: 

Archive: This is a folder for code that was used in initial steps of this analysis but did not end up in the final manuscript. Most of this code was performed on more individuals than ended up in the final results (were removed due to isolation or genetic relatedness) or for loci that differed based on scoring year. 

Images: This folder contains images generated for organizing the Github or population maps. 

SDMs: This folder is for the code to run "species distribution models," specifically with boosted regression tree models as described in Elith et al. (2008). The code published here is based on code from Peter Breslin (ASU) and Fabio Suzart de Albuquerque. Part of this project was interested in identifying butternut's ecological preferences using species distribution modeling and then modeling habitat requirements into the past. This folder contains the code for performing all of these analyses. First, occurrence records must be downloaded from herbarium databases (in this case, Global Biodiversity Information Facility (GBIF), Integrated Digitized Biocollections (iDigBio), South East Regional Network of Expertise and Collections (SERNEC), Botanical Information and Ecology Network (BIEN), and the national network of forest survey plots managed by the Forest Inventory and Analysis Program (FIA) of the USDA Forest Service) using code that was based off code created by Emily Beckman (https://github.com/esbeckman/IMLS_Beckman). Then, these occurrences were used to create a range polygon that buffered out 100 km from the range edges (which was eventually used for genetic diversity analyses as well). Occurrence records were reduced for spatial autocorrelation by selecting one point for every point that is within 1 km of others. Pseudo-absence points were generated in equal number to presence points. Following this, 19 previously downloaded Worldclim variables were extracted at every point location. Variables that were most correlated with presence and least correlated with one another (correlation coefficient < 0.5) were selected to model species distribution. This was done by generating a dissimilarity matrix and choosing the variable that had the highest correlation with presence in each cluster of highly correlated climate variables. The final boosted regression tree model was run with the variables: precipitation of the wettest month, mean diurnal range, mean temperature of the driest quarter, mean temperature of the wettest quarter, and seasonal precipitation and from these predictors a model of suitable habitat was made and then hindcast into past climate scenarios using eight time periods representing notable periods in post-LGM climatic history, available from the Paleoclim database (Brown et al., 2018): 130 (last interglacial); 22 (LGM); 17-14.7 (Heinrich-Stadial); 14.7-12.9 (Bolling-Allerod); 12.9-11.7 (Younger Dryas); 11.7-8.326 (early Holocene); 8.326-4.2 (mid-Holocene); and 4.2-0.3 ka YBP (late Holocene). 

genetic_analyses: We used genetic data from the publication Hoban et al. (2010) and newer sampling efforts on butternut from 2011 - 2015. These individuals were collected by Jeanne Romero-Severson, Sean Hoban (https://github.com/smhoban), and Martin Williams over the course of near ten years with a major sampling effort closer to 2009 and then followed up by another round of sampling 2012 - 2015. The initial individuals that were collected were genotyped by Sean Hoban and then subsequent individuals were genotyped in the Romero-Severson lab at Notre Dame non-consequetively. The first script labeled "comparison_barplot" was code used to determine if there were scoring differences between researcher. 
 
References: 

Elith, J., Leathwick, J. R., & Hastie, T. (2008). A working guide to boosted regression trees. Journal of Animal Ecology, 77(4), 802-813.
