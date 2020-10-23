The results of table 3 come from this subfolder.

Each file in all subfolder has following structure:
---------------------------------------------------------
'algo': ML algorithm used

'case': Type of case. Discussed below.

'mean of MAEs': mean of the MAEs for the 100 runs. This is also the mean of the absolute errors for all the runs
                as each run has same number of prediction points.

'SD of MAEs' or 'std of MAEs': standard deviation of the MAEs of 100 runs.

'SD of AEs': standard deviation of the absolute errors of all the 100 runs.

'mean of Stds': Gaussian Process (GP) specific. GP returns a prediction variance for each prediction point.
                Square root of that variance gives standard deviation around that point. This column contains
                the mean of all the predicted standard deviations for GP.

'SD of Stds' or 'std of Stds': Gaussian Process (GP) specific. GP returns a prediction variance for each prediction point.
                               Square root of that variance gives standard deviation around that point. This column contains
                               the standard deviation of all the predicted standard deviations for GP.



Calculation Process:
-------------------------------
For each input file in folder 'InputFiles_CM_BoB_with_BondCounts' and for each case do the following:
    For each ML algorithm in {GP,KRR,SVR,Ridge,Lasso,Elastic} do the following: 
        For 100 times
            Read the input file (it contains one row for each metal and each species)
            Read relevant columns based on the current case.
            Shuffle data randomly and then split into train and test sets.
            Use 5 fold cross-validation on training data to obtain best hyperparameters for the current algorithm.
            Generate predictions for test set using optimum hyperparameters. 
            Absolute errors for this run are saved temporarily.
        Mean and SD of all the absolute errors for all metals is calculated and stored.
    Save results in an output file.


Subfolder 'BondCount_predictions':
=============================================
Rows 1,2,9,14 of table 3 come from this subfolder.

predictions of random points across species and metals using Bond counts along with metal descriptors.

Cases: 
'2metdesc' means metal descriptors (CHCHCO, OH) was used.
'3metdesc' means metal descriptors (CHCHCO, OH, C) was used.
'fullbondcnt' means all bond counts were used (C-C, C-H, C-O, O-H, C-M, O-M).
'spcbondcnt' means only species bond counts were used (C-M, O-M).



Subfolder 'CM_BoB_predictions_ExcludeMetals':
==================================================
Rows 5,6,7,8,12,13 of table 3 come from this subfolder.

predictions of random points across species and metals using CM, BoB, Bond counts along with metal descriptors.
Different combinations of these descriptors were used. CM, BoB calculations were done excluding metal surface atoms.

For each input file in the folder 'InputFiles_CM_BoB_with_BondCounts/CM_BoB_with_MetalExcluded', 
6 output files are generated covering different cases.
cases are: 1. CM/BoB with 2 metal descriptors (CHCHCO, OH)
           2. CM/BoB with 3 metal descriptors (CHCHCO, OH, C)
           3. CM/BoB + Full bond count with 2 metal descriptors (CHCHCO, OH)
           4. CM/BoB + Metal bond count with 2 metal descriptors (CHCHCO, OH)
           5. CM/BoB + Full bond count with 3 metal descriptors (CHCHCO, OH, C)
           6. CM/BoB + Metal bond count with 3 metal descriptors (CHCHCO, OH, C) 



Subfolder 'CM_BoB_predictions_IncludeMetals':
==================================================
Rows 3,4,11 of table 3 come from this subfolder.

predictions of random points across species and metals using CM, BoB, Bond counts along with metal descriptors.
Different combinations of these descriptors were used. CM, BoB calculations were done including metal surface 
atoms along with the species atoms.

For each input file in the folder 'InputFiles_CM_BoB_with_BondCounts/CM_BoB_predictions_IncludeMetals', 
6 output files are generated covering different cases. (For 160 input files, total 160*6 = 960 files are generated)
cases are: 1. CM/BoB with 2 metal descriptors (CHCHCO, OH)
           2. CM/BoB with 3 metal descriptors (CHCHCO, OH, C)
           3. CM/BoB + Full bond count with 2 metal descriptors (CHCHCO, OH)
           4. CM/BoB + Metal bond count with 2 metal descriptors (CHCHCO, OH)
           5. CM/BoB + Full bond count with 3 metal descriptors (CHCHCO, OH, C)
           6. CM/BoB + Metal bond count with 3 metal descriptors (CHCHCO, OH, C) 


