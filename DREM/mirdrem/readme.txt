-------------------------------------------------------------------------------
mirDREM (version 0.1.1)
-------------------------------------------------------------------------------
This software was developed by Marcel Schulz in collaboration with Ziv Bar-Joseph. 
Any questions about the software or bugs found should be emailed to mschulz@mmci.uni-saarland.de or zivbj@cs.cmu.edu.

We are currently porting mirDREM to the DREM 2.0 version (http://sb.cs.cmu.edu/drem/, reference 2) to use the improved visualization and output features and hope that it will be soon available.

-------------------------------------------------------------------------------
Version log
-------------------------------------------------------------------------------
0.1.1 - bugfix release
		- crash fixed due to missing Regulator IDs
		- removed hardcoded file paths for intermediate files which led to display errors
		- fixed bug where human microRNA ids were not properly recognized
0.1 - initial release version


-------------------------------------------------------------------------------
Requirements
-------------------------------------------------------------------------------

mirDREM requires Java 1.5 or later to be installed.  Java can be downloaded from
http://www.java.com.

-------------------------------------------------------------------------------
Usage
-------------------------------------------------------------------------------
Once Java is installed, to start mirDREM in Microsoft Windows double click on mirdrem.cmd.  
Otherwise to start mirDREM, from a command line while in the mirdrem directory enter the 
command

java -mx1024M  -jar mirdrem.jar 

The default settings for mirdrem are loaded when you start. Containing   
miRNA and TF-gene interactions and  processed mouse time series expression data of genes and 
miRNAs that can be used to reconstruct the model described in reference 1).  

This opens the main dialog and in order to start the computation hit the Execute button on the bottom.
A search dialog should open now and after a few minutes (depending on your processor) the complete network should be displayed in a new window.

-------------------------------------------------------------------------------
Input Data:
-------------------------------------------------------------------------------

IMPORTANT! Currently the Expression data file needs to have the lines sorted 
such that  protein coding genes are before microRNA genes. 
For example expression ratios for four days of N protein coding genes and M microRNAs should look like this (example mouse):

Probe   day1    day2   day3   day4
gene_1  0.186544087     0.201794721     0.337250975     0.155902261
gene_2  0.252819998     -0.224561579    -0.228685766    0.13545836
gene_3  0.19636612      -0.379317446    0.06386158      0.332412469
gene_4  0.204072371     0.894635513     -0.566359024    -0.73968395
..
gene_N  0.252819998     -0.224561579    -0.228685766    0.13545836
mmu-mir_1  0.19636612      -0.379317446    0.06386158      0.332412469
mmu-mir_2  0.19636612      -0.379317446    0.06386158      0.332412469
..
mmu-mir_M  0.19636612      -0.379317446    0.06386158      0.332412469


mirDREM comes with two sets of predicted interaction datasets which can be found in the RegInput folder:
mouse-TF-miRNA-interactions.dat
human-TF-miRNA-interactions.dat
Both contain TF and miRNA predicted interactions one for human and one for mouse, 
if expression data should be used with these interactions the IDs need to agree.

In addition to the interaction file in the RegInput folder, mirDREM needs an additional file that has to be selected under Options->mirDREM Options->Regulator Type File. Hit the "update miRNA parameters" button when you changed this file in the Options dialog.
For both interaction datasets the corresponding regulator type files can be found in the main mirDREM folder (mouse-RegulatorType.dat,human-RegulatorType.dat).

The origin of TF interactions is explained in reference 2).

The miRNA-gene interactions are taken from the microcosm database (http://www.ebi.ac.uk/enright-srv/microcosm/) 
which uses the miRanda prediction algorithm (reference 3), all predictions are taken if p-value <= 0.01.

The interactions are contained in the RegInput directory.
If a user adds their own files to this directory they will automatically
appear on the menu of available regulator-gene association files.  

-------------------------------------------------------------------------------
GUI
-------------------------------------------------------------------------------
Use the small help buttons in the GUI to learn more about the different input fields and parameters.

Currently, miRNAs associated with split nodes are displayed with a "/\" or "\/" prefix depending 
on the direction of expression between consecutive timepoints, meaning upregulated and downregulated respectively. 

Alternatively consult the Manual of the DREM software for more details about the display (http://sb.cs.cmu.edu/drem/DREMmanual.pdf).

-------------------------------------------------------------------------------
External packages and sources
-------------------------------------------------------------------------------

mirDREM makes use of the Piccolo toolkit which is distributed under a BSD license.  
More information about Piccolo can be found at www.cs.umd.edu/hcil/piccolo

mirDREM makes use of the Batik software which is distributed under an Apache license
More information about Batik can be found at http://xmlgraphics.apache.org/batik/.


mirDREM makes use of the Gene Ontology and gene annotations provided by Gene Ontology
Consortium members.  More information about the Gene Ontology can be found at
www.geneontology.org.

-------------------------------------------------------------------------------
References
-------------------------------------------------------------------------------
1) Marcel H  Schulz, Kusum V Pandit, Christian L Lino Cardenas, Ambalavanan Namasivayam, Naftali Kaminski, Ziv Bar-Joseph
Reconstructing dynamic miRNA regulated interaction networks
PNAS, August 28, 2013, doi: 10.1073/pnas.1303236110 
2) MH Schulz, WE Devanny, A Gitter, S Zhong, J Ernst and Z Bar-Joseph 
DREM 2.0: Improved reconstruction of dynamic regulatory networks from time-series expression data 
BMC Systems Biology 2012
3) Enright AJ, John B, Gaul U, Tuschl T, Sander C and Marks DS.
 MicroRNA targets in Drosophila. Genome Biology (2003) 5;R1
