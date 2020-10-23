subfolder 'LeaveOneMetalOut_using_MetalDescriptors':
========================================================
predictions across metals using only metal descriptors.
All descriptor combinations of size 1, 2 and 3 from the set {C, H, O, CO, OH, CHCHCO} are presented.

The file 'PredictionsFor_ALL_Descs_Ridge.csv' is the Linear Scaling.
First row of table 1 and all rows of table 2 comes from this file.

The file 'PredictionsFor_ALL_Descs_KRR.csv' is the prediction when applying Kernel Ridge Regression (KRR)
with different metal descriptors. 3rd row of table 1 comes from this file.

The file 'PredictionsFor_ALL_Descs_SVR.csv' is the prediction when applying Support Vector Regression (SVR)
with different metal descriptors. 2nd row of table 1 comes from this file.


Calculation Process:
----------------------------
For each descriptor combination do the following:
    For each metal do the following:
        For each species of the metal get the predicted energy using 7 other energies for that species for all other metals.
        Absolute error for each prediction stored.
        Mean absolute error for that metal and for that descriptor combination is saved.
    Mean and standard deviation of all the absolute errors is calculated for the descriptor combination.


Each of the file has this structure:
----------------------------------------
'DescriptorCombination': the set of metal descriptors.

Then 8 columns for 8 metals' mean-absolute-error.

'Mean of MAE': Mean of the MAEs of 8 metals for the descriptor combination. This is also the mean of all the absolute errors
               for that descriptor combination. This is because for each metal there are same number of prediction points.

'Std of MAEs of metals': standard deviation of the Mean-Absolute-Errors for 8 metals for this descriptor combination.

'Std of AE': standard deviation of all the absolute errors for this descriptor combination.



subfolder 'LeaveOneMetalOut_using_CM_BoB_BondCounts':
==========================================================
predictions across metals using CM, BoB, Bond counts along with metal descriptors.
Different combinations of these descriptors were used.

For each input file in the root folder 'InputFiles_CM_BoB_with_BondCounts', 
6 output files are generated covering different cases.
cases are: 1. CM/BoB with 2 metal descriptors (CHCHCO, OH)
           2. CM/BoB with 3 metal descriptors (CHCHCO, OH, C)
           3. CM/BoB + Full bond count with 2 metal descriptors (CHCHCO, OH)
           4. CM/BoB + Metal bond count with 2 metal descriptors (CHCHCO, OH)
           5. CM/BoB + Full bond count with 3 metal descriptors (CHCHCO, OH, C)
           6. CM/BoB + Metal bond count with 3 metal descriptors (CHCHCO, OH, C) 

Bottom 3 rows of table 1 comes from some better results among all the files in this subfolder.


Calculation Process:
-------------------------------
For each input file in folder 'InputFiles_CM_BoB_with_BondCounts' and for each case do the following:
    For each ML algorithm in {GP,KRR,SVR,Ridge,Lasso,Elastic} do the following: 
        For each metal do the following:
            Read the input file (it contains one row for each metal and each species)
            Train on other 7 metals' data (total 7*26 = 182 data points) and predict 26 species energy for the current metal.
            Mean and SD of Absolute errors for this metal and this algorithm is stored.
        Mean and SD of all the absolute errors for all metals is calculated and stored.
        SD of the MAEs of all the metals for this algorithm is calculated and stored.
    Save results in an output file.


Each of the file has this structure:
----------------------------------------
'case': the case covered by the input file

'subcase': One of the 6 cases mentioned above

'algo': ML algorithm used

Then 8*2 = 16 columns with 2 columns for each metal containing the MAE and SD of AE for that metal.

'MAE combined': Mean of the MAEs of 8 metals for the descriptor combination. This is also the mean of all the absolute errors
               for that algorithm. This is because for each metal there are same number of prediction points.

SD of AE combined': standard deviation of all the absolute errors for this algorithm.

SD of MAEs of Metals': standard deviation of the Mean-Absolute-Errors for 8 metals for this algorithm.
