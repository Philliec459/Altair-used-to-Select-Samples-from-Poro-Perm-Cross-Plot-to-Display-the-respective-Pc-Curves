# Interrogate Petrophysical data using Python's Interactive Altair
The objective of this project is to interrogate Petrophysical core data using python's interacive Altair. 

Clerke's Rosetta Stone Arab-D carbonate data(1) is show below in the display of our data. This is Core analysis data. The Permeability (and log10 of perm lPerm) and Porosity are from the routine core analysis data. Clerke masterfully selected this dataset starting from thousands of qualified, inspected plug samples where the final samples were randomly selected from the group to create a very unique in that covers the full range in poro-perm space and Petrophysical Rock Types (PRTs). 

High Pressure Mercury Injection (HPMI) was performed on each of the core plug samples too. The HPMI data was fit to the Thomeer hyperbolas for each pore system giving us the Thomeer parameters Pd, G and Bulk Volume Occupied for each pore system found in the plug sample.



1) Clerke, E. A., Mueller III, H. W., Phillips, E. C., Eyvazzadeh, R. Y., Jones, D. H., Ramamoorthy, R., Srivastava, A., (2008) “Application of Thomeer Hyperbolas to decode the pore systems, facies and reservoir properties of the Upper Jurassic Arab D Limestone, Ghawar field, Saudi Arabia: A Rosetta Stone approach”, GeoArabia, Vol. 13, No. 4, p. 113-160, October, 2008.


### Thomeer Parameters and Petrophysical Rock Types:

A Thomeer hyperbola is fit to the HPMI data by optimizing on the Thomeer Parameters G1, Pd1 and BV1 for the first pore system and G2, Pd2 and BV2 for the second. The following image relates the Thomeer hyperbola (dashed black line) to the Capillary Pressure Curve (solid red line). Ed Clerke used hist famous Thomeer Parameter spreadsheet with solver to determine the correct set of Thomeer parameters for each sample.  

![thomeer.png](attachment:thomeer.png)

After all the Thomeer parameters were assigned to all the samples, then Ed used the distributions of the the Initial Displacement Pressure (Pd) to devise his Petrophysical Rock Types (PRT) scheme. 

![Rock-Types.png](attachment:Rock-Types.png)

Most macro rock typically has a dual porosity system where the Pore Throat Distribution (PTD) will have two modes as shown below. 

![Mode.png](attachment:Mode.png)

The macro portion of the rock will have a mode greater than 2 microns with a second (or third) mode less than 2 microns. Probably the most abundant PRT is the M_1. This is a macro-porous rock with a mode in the macro portion of the PTD and a second mode in the meso-porosity range. In this PRT both the macro pores and meso-porous grains can have oil saturations once the capillary pressure is great enough to drive out the water. The M_2 PRT is also a macro rock, but the second pore system is micro-porous and is too tight to have hydrocarbon saturations. The Table below shows Clerke's description of his PRT's. 

The following are some example results using Altair where the data in cross plots can be selected and then the appropriate data for those selected samples are shown in the bar charts below the cross plots. 

![Rosetta_altair.png](attachment:Rosetta_altair.png)

### Petrophysical Rock Typing (PRT):

One of the benefits of working with Thomeer parameters is that the exact mode of the PTD (radius) can be calculated for each sample using the Buiting Mode equation as shown below:

        Mode(microns) = (exp(-1.15 * G) * (214/Pd))/2
        
Again, this equation gives us the mode of the pore system, and we normally only calculate the mode of the largest pore system in the sample. 

In the Altair plots below the first row of poro-perm xplot show the PRT and actual Mode of Pore Throats on the Z color axis. The second row of xplots show the Winland r35 on the color axis, Amaefule FZI and RQI on the color axis.

The actual mode of the Pore Throat Distribution is shown in the first row of the poro-perm xplots. In Rock Typing Winlands' r35 and Amaefule's FZI or RQI attempt to predict the most dominant pore throat. In dual-porosity carbonates Winland's r35 is usually a close proximity, but FZI does not do well. RQI appears to be off, but captures the range of the pore throats a bit better. 

Windland's r35 is calculated:

        r35(microns) = 10**(0.732 + 0.588*log(Permeability) - 0.864*log(Porosity*100))


Amaefule-Kersey FZI is calculated:

        RQI(microns) = 0.0314 * sqrt(Permeability/Porosity)
        
        Phiz = Porosity / (1 - Porosity)

        FZI(microns) = RQI / Phiz
    
where Porosity is a volume fraction and not percent. 

On this dataset it appears that r35 has the best match to the actual mode of the Pore Throat Distribution. The bi-modality in the macro-porous rock has FZI falling between the two modes since it is the mean pore throat radius. Windland's r35 does a fairly good job of estimating the most dominant pore throat. 


### PRT in Relationship with Mode of Pore Throat Distribution, Winland r35 , Amaefule FZI and RQI:


