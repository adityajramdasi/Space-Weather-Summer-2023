# Correlating Forbush Decrease Magnitudes and ICME properties

This public repository houses the data analysis work I did in analyzing Neutron Monitor time series data for my Summer 2023 research assistantship under [Prof. Prasad Subramanian] at IISER Pune. Includes the code I wrote, plots I generated, and statistical correlations I found between Forbush Decrease magnitudes and various ICME properties.

The following is an overview of the context of this project, what I did, and my key learnings - 

<p align="center">
  <img width="400" height="500" src = "https://github.com/adityajramdasi/IISERP-Summer-2023/assets/94242073/9a91f42c-6033-454a-983c-a4766205a1a2">
  <img width="400" height="500" src = "https://github.com/adityajramdasi/IISERP-Summer-2023/assets/94242073/132c59ac-7ce5-4549-9758-9338c814c708">
</p>



## ICMEs and Space Weather 
The solar surface and atmosphere is a region of constant activity. The sun often ejects outbursts of plasma and magnetic fields from its corona, which are known as Coronal Mass Ejections (CMEs). Some of these ejections become big enough to escape the solar atmosphere and travel through interplanetary space. These are known as Interplanetary CMEs (ICMEs). A fraction of these ICMEs are directed towards the Earth, where they travel the Earth-Sun distance and collide with the Earth's magnetosphere and ionosphere. This fills up energy in the Earth's magnetic field (like a stretched rubber band) by bending and stretching it, initiating a geomagnetic storm. A geomagnetic storm causes major disruptions in the near-Earth space weather, including exposing our satellites and astronauts to harmful radiation. Geomagnetic storms caused by ICMEs can disrupt all radio communication and overload electric power grids, causing widespread blackouts (see [Carrington event](https://en.wikipedia.org/wiki/Carrington_Event) for more). Thus, having an in-depth understanding of the dynamics of ICMEs and their effects on space weather is extremely crucial to protect our satellites, communication, and astronauts. 

## Cosmic rays and Forbush Decreases
Unlike the sun's occasional bombardment of the Earth by high-energy plasma walls and magnetic fields, it also experiences a constant shower of cosmic rays (streams of high-energy particles originating from the sun as well as from other extra-solar sources) in various energy bands. Neutron Monitor (NM) stations located at various locations and altitudes on the Earth's surface capture and record this cosmic ray shower (in counts/sec) in a particular energy bandwidth. Each NM station has its own "cutoff rigidity" (momentum per unit charge), which can be roughly thought of as "cutoff energy", below which that station cannot detect neutrons. The value of this cutoff rigidity is dependent mainly on the NM stations's latitude, longitude, and (somewhat negligibly) on its altitude. 
Occasional dips in the counts/sec data from these neutron monitors are observed, many of them around the same timeline as an approaching geomagnetic storm caused by an Earth-directed ICME. There are various theoretical models explaining how the magnetic cloud of the ICME traps a majority of the cosmic rays, thus blocking them from reaching the Earth and getting detected by NM stations. Such dips in the cosmic ray data are called "Forbush Decreases" (FDs).

In this project, I define a magnitude for quantifying the dip observed in NM data (explained in the Jupyter notebooks), use the definition to extract the dip sizes, and plot them with various ICME parameters to look for correlations.

## Sources of Data 
### Neutron Monitor Stations
Since this is part of a **data-driven approach** to building theoretical frameworks to model (and hopefully predict) ICMEs, it is important to use reliable data sources to analyze existing data and find patterns/correlations in it. 13 NM stations were identified for their low cutoff rigidity values (<1 GV), all located in the Arctic and Antarctic regions (maintained by Bartol Research Institute, University of Delaware), and their neutron monitor time series data was smoothed and analyzed to look for and quantify Forbush Decreases. The _Neutron Monitor Database's_ NEST interface was used to extract .csv files containing counts/sec NM data for ~4 days before-and-after the shock arrival and magnetic cloud passing times respectively, smoothed and searched for dips in the relevant time interval. Data source - https://www.nmdb.eu/nest/

### Space-based satellites
Space-based satellites such as NASA's WIND or ISRO's Aditya L1, located at Lagrange points in between the Earth and Sun, have instruments to carry out _in-situ_ observations of ICMEs, geomagnetic storms, etc. The WIND satellite detects and records data for various properties of ICMEs, and its catalogue was used to get the numbers for these ICME properties to study their correlations with FD magnitudes. Data source - https://wind.nasa.gov/ICME_catalog/ICME_catalog_viewer.php 

## Code written & plots generated 
I smoothed NM counts/sec data from 13 chosen NM stations corresponding to 11 ICME events (in 2015, 2014) and quantified the dip sizes in the NM data. The code for doing this and the time-series plots generated (along with marking shock arrival, start, and end of magnetic cloud) can be found in the folder - "**Plotting data & finding dip-size**" in this repo. I wrote event-based and station-based functions to generate time series plots and the relevant FD magnitudes (dip sizes). The exact methodology for smoothening data and quantifying the dip size is explained clearly in the Jupyter Notebooks. Chosen NM stations: OULU, SNAE, APTY, FSMT, INVK, NAIN, PWNK, THUL, NEU3, SOPB, SOPO, MRNY, TERA

After generating numbers to quantify the dip sizes from my definition, I plotted them individually with the following ICME properties (data from WIND catalogue) - 
1. Mean Magnetic Field inside the magnetic cloud: $B$ (in nT)
2. Mean Solar Wind Bulk Velocity: $V_{sw}$ (in km/s)
3. Mean Expansion velocity: $V_{exp}$ (in km/s)
4. Disturbance Storm Time (DST) index (in nT)
5. Mean Turbulence in Magnetic Field inside the magnetic cloud: $\delta B/B$ (data obtained from Debesh Bhattacharjee's PhD thesis at IISER, Pune)
6. Mean Turbulence in Net Proton flux: $\delta n_{p}/n_{p}$ (data obtained from Debesh Bhattacharjee's PhD thesis at IISER, Pune)

I also plotted this data into NM station-wise subplots and plotted the best-fit 3-degree polynomial curves to every dataset. I also generated numbers quantifying 4 kinds of **statistical correlations** for each ICME event's, each NM station's data set. These 4 are - Pearson R, Spearman R, Kendall Tau, and Linear Regression. All these numbers can be found above the respective station-wise subplots in the relevant Jupyter Notebooks.
Another different kind of graph I plotted was to find correlations between the _cutoff rigidity_ of NM stations (13 of them, with ~9 unique values from 0.01-1GV) and FD magnitudes (dip sizes).
The code for generating all these plots and finding out correlation coefficients, along with the plots themselves, can be found in the folder - "**Correlation plots**" in this repo. 

**Notably, the highest average statistical correlation was found between _Mean Solar Wind Bulk Velocity_ and FD magnitude: 0.72** (even with just 11 ICME events).

Finally, the "**Correlation coefficients table**" lists all 4 types of correlation coefficients found for all 6 ICME properties in a table. _If I were asked to show the outcome of 2 months of data analysis work in a single glance, I would show this table._

## Scope for future work/extensions
Some immediate actionable extensions I can identify that will add value to this project and/or be relevant to developing a theoretical model -
1. Analyzing many more ICME events (this project only has results from 11 out of 151 events filtered by Debesh Bhattacharjee) for better statistical results.
2. Generating correlation coefficients that are more relevant for this kind of data and using their results.
3. Plotting best-fit polynomial curves for all degrees from 1-5, finding correlation coefficients corresponding to every curve, and finding out which degree curve(s) give the highest correlation. I believe this would be a very relevant step towards developing theoretical models for ICMEs, by giving us a sense of what powers (indices) are involved, given that sufficiently large number of events are analyzed).
5. Testing goodness of fit ($\chi^2&) of data with theoretical predictions of multiple existing theories.
6. Implementing a mechanized method to filter out clean dip and/or recovery profiles of NM data.
7. Like FD magnitude (dip size), defining and generating numbers for "Recovery times" of NM data after Forbush Decrease and doing all the above-mentioned analysis for that quantity too. (correlating recover times with ICME properties)

## Acknowledgements & Learnings
I thank Prof. Prasad Subramanian for introducing me to this project at the intersection of Space Weather and Solar Physics and guiding me for the ~2 months that I worked on this problem under him. I also thank Dr. Debesh Bhattacharjee for his turbulence in magnetic field and proton flux data that I used to find 2 more kinds of correlations, in addition to the ICME properties's data from the WIND catalogue. Apart from a basic understanding of the physical processes influencing ICMEs and near-Earth space weather, working on this project also added a good number of transferable and widely used skills of data analysis and plotting in Python to my arsenal.

