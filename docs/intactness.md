---
title: Intactness mapping
---

## Workflow: Mapping intactness and footprint

There are a number of possible applications including using the disturbance map, including to: i) create a landscape intactness or human footprint map; ii) evaluate the effects of cumulative disturbances on focal species or ecosytems; iii) create a resitance or permeability map for connectivity analysis, or iv)assist in the design of field surveys e.g., to evaluate the impacts of mining of caribou. In this section, we focus on the first example, which consists of five broad steps:

1. Define study area and objectives
2. Create geopackage for study area
3. Define minimum patch size and buffers of influence
4. Map landscape footprint and intactness
5. Export footprint and intactness maps

Optionally, depending on the conservation planning objectives, the last three steps can be repeated using different buffer width and minimum patch sizes.

The flowchart below provides an overview of the intactness mapping workflow and its five steps. Each step is then described in more detail in the following paragraphs.

<center><img src="pics/intactness.png" width="600">
<br>*Figure 1. Flowchart outlining the five steps used to map landscape intactness and human footprint for a study area of interest.*<br><br>
</center>

## Step 1. Define study area and objectives

The first step is to define a study area and objectives.  Some thought should also be given for the objectives of this analysis. For example, is the objective to create one intactness and footprint map based on predefined buffers? Or, is the objective to do a sensitivity analysis to evaluate the effects of changing buffer sizes and minimum patch sizes on estimates of landscape intactness?

## Step 2. Create geopackage for study area

Once a study area polygon has been defined, it can be used with the Geopackage Creator to create all of the data layers needed to create landscape intactness and footprint maps. More information on using the app is provided in the Geopackage Creator page of the Shiny Apps section of this website. Once the geopackage is ready, you can start the Disturbance Explorer and go to step 3.

## Step 3. Define minimum patch size and buffers of influence

Here we provide a brief description of this step. For additional details on how to do this with the Disturbance Explorer app, go to its page in the Shiny Apps section. This step consists of two related tasks: 1) Define buffer sizes of influence for each disturbance type (linear, areal) and 2) Specify minimum patch size (and shape) to qualify as intact. To achieve the first task, each anthropogenic disturbance type needs to be assigned a buffer size of influence based on its spatial extent and ecological impact. To achieve the second task, the minimum size required for an intact landscape patch also needs to be defined to differentiate between fragmented and relatively undisturbed areas.

## Step 4. Map landscape footprint and intactness

A landscape intactness (and footprint) map can be generated in one of three ways: i) using QGIS, ii) using R code, or iii) using the accompanying R/Shiny app. For now, we focus on the third method but may provide more details about the first two methods in the future. Using the Disturbance Explorer app (see relevant Shiny Apps section), it is possible to create intactness and footprint maps for any region within the Yukon and northern BC.

## Step 5. Export footprint and intactness maps

Using the Disturbance Explorer app, the resulting footprint and intactness maps can then be saved as layers within a geopackage using either of the 3 approaches.

## Repeat using different buffer width and minimum patch sizes (optional)

An optional, but recommended, step is to repeat the procedure of generating intactness and footprint maps using varying buffer sizes and minimum patch sizes to assess the sensitivity of the results to these parameters. 
