OpenSWATH DIA analysis
DIA analysis using OpenSWATH workflow for analysis of DIA data using Spectral Library generated from assay DDA data. 
Data used for analysis taken from the following study [1]. 
This study provides comparison in proteome changes associated with reduced gene dosage using Ebf1 transcription factor affecting modulation of pro B lymphocytes in WT and Heterozygous genotypes. Both DIA and DDA samples were taken. 

Part I - iRT library generation
iRT library generation  was done using Skyline desktop tool [2] according to the following tutorial [3] and instructions found on OpenSWATH webpage [4]. 
Creation method:
DDA measurements were imported into Skyline tool. iRT peptides with highest quality scores were selected from all the identified peptides and calibration was performed using Skylines built in calibration method. The results were exported to Galaxy. 

Part II - Peptide and protein analysis using OpenSwath WF (Galaxy WF)
Section 1 - Spectral library generation
 (1) Analysis of DDA data (MaxQuant)
 (2) Generation of a spectral library using iRT libraries obtained in Part I (diapysef)
 (3) Spectral library optimization and refinement (OpenSwathAssayGenerator)
 (4) Adding decoy sequences (OpenSwathDecoyGenerator)
 (5) Converting final spectral library to appropriate (from .tsv to .pqplite) format (TargetedFileConverter)
 
Section 2 - OpenSWATH analysis (Galaxy WF)
 (1) DIA analysis using OpenSwath methodology for DIA measurements of both genotypes (OpenSwathWorkflow)
 (2) Combining osw results from different inputs (PyProphet merge)
 (3) FDR estimation (PyProphet score)
 (4) Conduct peptide inference (PyProphet peptide Peptide error-rate estimation)
 (5) Conduct protein inference (PyProphet protein Protein error-rate estimation)
 (6) Exporting pyprophet scored OSW results (PyProphet export Export tabular files, optional swath2stats export)

Part III - limma differential analysis of protein expression (R script)
 (1) Upload .osw databases from OSW analysis (Het and WT)
 (2) Extract relevant fields from the two databases (RSQLite)
 (3) Join results
 (4) Reshape matrix into form suitable for limma analysis (limma)
 (5) Create design matrix
 (6) Create contrasts 
 (7) Run limma 
 (8) Process results 
 (9) Create plots
 (10) Run GO enrichment (clusterProfiler)

References
[1] A comprehensive Proteomic Investigation of Ebf1 Heterozygosity in pro B lymphocytes utilizing Data Independent Acquisition (DIA) and Data Dependent Acquisition (DDA) Approaches, https://www.ebi.ac.uk/pride/archive/projects/PXD006620
[2] Skyline, https://skyline.ms/project/home/software/skyline/begin.view
[3] iRT retention time prediction, https://skyline.ms/wiki/home/software/Skyline/page.view?name=tutorial_irt
[4] Spectral library generation, https://openswath.org/en/latest/docs/skyline.html
