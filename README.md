# metabolomeQTLSelection
The java code "getQTLs1R1c" is going to provide a selection of QTLs based on r2 values between associated polymorphisms. This analysis is performed independently by chromosome and it would be done by rounds "int variable round." You need to provide
a threshold value as well "double variable r2Threshold." By default this value is set to 0.4; The variable chr (String) represent the chromosome number to be analyzed. the variable path (string) stablishes the folder location for input files, where files are
available by chromosome.

Input files for chromosome 14:

finalMetaboliteDataPlot14.txt

Format:

MZ146.0599044_1.1096294_all	14:31850702	19200.69348	9.43	1.63	185

MZ146.0599044_1.1096294_all	14:31856073	19200.747190000002	10.17	1.75	185 

MZ385.3462964_6.300724_all	14:31856174	19200.7482	10.21	1.76	185

MZ385.3462964_6.300724_all	14:31859071	19200.77717	10.48	1.81	185

MZ146.0599044_1.1096294_all	14:31872935	19200.915810000002	11.15	1.92	185

MZ425.3410787_7.000614_all	14:31875543	19200.941890000002	11.15	1.92	185

finalMetaboliteDataPlot14.txt includes six columns: metabolite name (MZ146.0599044_1.1096294_all); polymorphism (14:31850702); -log10 (9.43). All other coulumns are used for plotting results. This file contains only significant markers across across
all phenotypes.

vcfLeadingMarkers14.txt

Format:

#CHROM	POS	ID	REF	ALT	QUAL	FILTER	INFO	FORMAT	rat1	rat2	rat3	

14	7044818	14:7044818	G	A	.	.	PR	GT	0/0	0/0	0/0	

14	7045169	14:7045169	A	T	.	.	PR	GT	0/0	1/1	0/0	

14	7048611	14:7048611	C	A	.	.	PR	GT	1/1	0/0	1/1	


vcfLeadingMarkers14.txt correspond to the standard vcf format. A file by chromosome needs to be provided.

getQTLs1R1c is going to create as output the following files after running the first round of analysis:

correlation14Round1.txt, which format is:

14:19819917

14:19819917 vs 14:7044818 Correlation: 0.21473880191570696; r2: 0.046112753048193234

14:19819917 vs 14:7045169 Correlation: 0.21473880191570696; r2: 0.046112753048193234

14:19819917 vs 14:7048611 Correlation: 0.21473880191570696; r2: 0.046112753048193234

14:19819917 vs 14:7049308 Correlation: 0.21850732829970657; r2: 0.047745452520675746

being 14:19819917 the leading marker for chr 14 selected from the first round of analysis and used to determine correlation values with all other remaining associated polymorphysms present on chromosome 14. the last column respresents the r2 value between
14:19819917 vs 14:7044818 (second row). 

From the first round of analysis, three files are created from finalMetaboliteDataPlot14.txt. 1) finalMetaboliteDataPlot14_aRound1, which includes the same information from finalMetaboliteDataPlot14.txt plus r2 value with the leading marker from the first round. 
2) finalMetaboliteDataPlot14_bRound1, ehich includes all markers from finalMetaboliteDataPlot14_aRound1 with r2 lower than the threshold and 3) finalMetaboliteDataPlot14_cRound1, which includes all markers from finalMetaboliteDataPlot14.txt which r2 values
were higher than the r2 theshold. finalMetaboliteDataPlot14_bRound1 is then relabled as finalMetaboliteDataPlot14.txt and made available for the next round of analysis. finalMetaboliteDataPlot14_c files will include all markers belonging to each associated
loci. Therefore final selected QTLs will be defined by the most downstream and upstream markers and can overlap based on location of the boundries of each loci by round.



