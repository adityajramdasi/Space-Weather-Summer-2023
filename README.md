# Correlating Forbush Decrease Magnitudes and ICME properties
This public repository houses the data analysis work I did in analyzing Neutron Monitor time series data for my Summer 2023 research assistantship under Prof. Prasad Subramanian at IISER Pune. Includes the code I wrote, plots I generated, and statistical correlations I found between Forbush Decrease magnitudes and various ICME properties. The following is an overview of the context of this project, what I did, and my key learnings - 

![ICME Richardson](https://github.com/adityajramdasi/IISERP-Summer-2023/assets/94242073/9a91f42c-6033-454a-983c-a4766205a1a2)

## ICMEs and Space Weather 
The solar surface and atmosphere is a region of constant activity. The sun often ejects outbursts of plasma and magnetic fields from its corona, which are known as Coronal Mass Ejections (CMEs). Some of these ejections become big enough to escape the solar atmosphere and travel through interplanetary space. These are known as Interplanetary CMEs (ICMEs). A fraction of these ICMEs are directed towards the Earth, where they travel the Earth-Sun distance and collide with the Earth's magnetosphere and ionosphere. This fills up energy in the Earth's magnetic field (like a stretched rubber band) by bending and stretching it, initiating a geomagnetic storm. A geomagnetic storm causes major disruptions in the near-Earth space weather, including exposing our satellites and astronauts to harmful radiation. Geomagnetic storms caused by ICMEs can disrupt all radio communication and overload electric power grids, causing widespread blackouts (see [Carrington event](https://en.wikipedia.org/wiki/Carrington_Event) for more). Thus, having an in-depth understanding of the dynamics of ICMEs and their effects on space weather is extremely crucial to protect our satellites, communication, and astronauts. 

## Cosmic rays and Forbush Decreases
Unlike the sun's occasional bombardment of the Earth by high-energy plasma walls and magnetic fields, it also experiences a constant shower of cosmic rays (streams of high-energy particles originating from the sun as well as from other extra-solar sources) in various energy bands. Neutron Monitor (NM) stations located at various locations and altitudes on the Earth's surface capture and record this cosmic ray shower (in counts/sec) in a particular energy bandwidth. Each NM station has its own "cutoff rigidity" (momentum per unit charge), which can be roughly thought of as "cutoff energy", below which that station cannot detect neutrons. The value of this cutoff rigidity is dependent mainly on the NM stations's latitude, longitude, and (somewhat negligibly) on its altitude. 
Occasional dips in the counts/sec data from these neutron monitors are observed, many of them around the same timeline as an approaching geomagnetic storm caused by an Earth-directed ICME. There are various theoretical models explaining how the magnetic cloud of the ICME traps a majority of the cosmic rays, thus blocking them from reaching the Earth and getting detected by NM stations. Such dips in the cosmic ray data are called "Forbush Decreases" (FDs).

In this project, I define a magnitude for quantifying the dip observed in NM data (explained in the Jupyter notebooks), use the definition to extract the dip sizes, and plot them with various ICME parameters to look for correlations.

## Sources of Data 
Since this is part of a **data-driven approach** to building theoretical frameworks to model (and hopefully predict) ICMEs, it is important to analyze existing data and find patterns/correlations in it. 13 NM stations were identified for their low cutoff rigidity values (<1 GV), all located in the Arctic and Antarctic regions (maintained by Bartol Research Institute, University of Delaware), and their neutron monitor time series data was smoothed and analyzed to look for and quantify Forbush Decreases. The _Neutron Monitor Database's_ NEST interface was used to extract .csv files containing counts/sec NM data for ~4 days before-and-after the shock arrival and magnetic cloud passing times respectively, smoothed and searched for dips in the relevant time interval. Data source - https://www.nmdb.eu/nest/


### Neutron Monitor Stations

### _In-situ_ satellites

## What I did 

## Acknowledgements


