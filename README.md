# Interrogate Petrophysical data using Python's Interactive Altair
The objective of this project is to interrogate Petrophysical core data using python's interacive Altair. This program is also available with Geolog python loglans that are included in this repository. 

### Data:
Clerke's Rosetta Stone Arab-D carbonate data(1) is shown below in the display of our pandas DataFrame. This is Core analysis data. 

Clerke masterfully selected this dataset starting from 1,000's of qualified, inspected core plug samples where the final 450 samples were randomly selected from this total group to create a very unique dataset in that covers the full range in poro-perm space and Petrophysical Rock Types (PRTs) in the Arab D. 

High Pressure Mercury Injection (HPMI) was performed on each of the core plug samples too. The HPMI data was fit to the Thomeer hyperbolas for each pore system present in the sample giving us the Thomeer parameters Pd, G and Bulk Volume Occupied for each pore system.


1) Clerke, E. A., Mueller III, H. W., Phillips, E. C., Eyvazzadeh, R. Y., Jones, D. H., Ramamoorthy, R., Srivastava, A., (2008) “Application of Thomeer Hyperbolas to decode the pore systems, facies and reservoir properties of the Upper Jurassic Arab D Limestone, Ghawar field, Saudi Arabia: A Rosetta Stone approach”, GeoArabia, Vol. 13, No. 4, p. 113-160, October, 2008. 

### Thomeer Parameters and Petrophysical Rock Types:

A Thomeer hyperbola is fit to the HPMI data by optimizing on the Thomeer Parameters G1, Pd1 and BV1 for the first pore system and G2, Pd2 and BV2 for the second. The following image relates the Thomeer hyperbola (dashed black line) to the Capillary Pressure Curve (solid black line). Ed Clerke used hist famous Thomeer Parameter spreadsheet with solver to optimize on the correct set of Thomeer parameters for each sample.  

>![thomeer.png](thomeer.png)

After all the Thomeer parameters were assigned to all samples, then Dr. Clerke used the distributions of the Initial Displacement Pressure (Pd) to devise his Petrophysical Rock Types (PRT) scheme. 

>![Rock-Types.png](Rock-Types.png)


The following are some example results using Altair where the data in cross plots can be selected and then the appropriate data for those selected samples are shown in the bar charts below the cross plots. 

>![Upscale_Pc2.gif](Thomeer_Pc_and_Thomeer_Parameters2.gif)


### Exact Mode of Pore Throat Distribution using Thomeer Parameters from Buiting Mode Equation:
In Clerke's Arab D Rosetta Stone data, most of the macro-porous rock typically has a dual porosity system.  The Pore Throat Distribution (PTD) will have two modes as shown below. 

>![Mode.png](Mode.png)

The macro portion of the rock will have a mode greater than 2 microns with a second (or third) mode less than 2 microns. Probably the most abundant PRT is the M_1. This is a macro-porous rock with a mode in the macro portion of the PTD and a second mode in the meso-porosity range. In this PRT both the macro pores and meso-porous grains can contain oil saturations once the capillary pressure is great enough to drive out the water. The M_2 PRT is also a macro-porous rock, but the second pore system is micro-porous and too tight to have hydrocarbon saturations. 

One of the benefits of working with Thomeer parameters is that the exact mode of the PTD (radius) can be calculated for each sample using the Buiting Mode equation as shown below:

    Mode(microns) = (exp(-1.15 * G) * (214/Pd))/2

Again, this equation gives us the mode of the pore system in microns, and we normally only calculate the mode for the largest pore system in the sample. In another of our GitHub repositories we use this mode as the ground truth as to the most dominant pore throat and compare this to the calculated Winland r35 and Amaefule FZI and RQI. Winland's r35 and Amaefule RQI compare the most favorably in this data set. FZI, or the mean hydraulic radius as defined in the Amaefule paper, usually lies between the two modes of a bi-modal pore system rock from this dataset. 


