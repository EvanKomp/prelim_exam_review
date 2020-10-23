There are 160 files in this folder. 80 of them for Coulomb matrix (CM) and 80 of them for Bag-of-bonds (BoB).
In paper, equation (4) contains 'power' and 'cutoff' parameters. In addition, we converted the 'Z' values
for the metal atoms using either natural log or square root. 
Set of 'Power' values used are: {1,2,3,4,5} (5 values)
Set of 'cutoff' values (in angstrom) used are: {2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5, 6.0} (8 values).
In addition, there is either the application of natural log or square root.
So, for each of CM and BoB we have (5*8*2) = 80 different setups. And hence 80 input files.

Each csv file in this folder has similar column structure:

column header '0': metal name
column header '1': species
column header '2': adsorption energy of CHCHCO for the metal in column '0'. (first metal descriptor)
column header '3': adsorption energy of OH for the metal in column '0'. (second metal descriptor)
column header '4': adsorption energy of C for the metal in column '0'. (third metal descriptor)
column header 'c_m': bond count for carbon-metal (c_m and o_m together form the 'metal bond count')
column header 'o_m': bond count for oxygen-metal (c_m and o_m together form the 'metal bond count')
column header 'c_c': bond count for carbon-carbon (c_c, c_h, c_o, o_h together form the 'species bond count')
column header 'c_h': bond count for carbon-hydrogen (c_c, c_h, c_o, o_h together form the 'species bond count')
column header 'c_o': bond count for carbon-oxygen (c_c, c_h, c_o, o_h together form the 'species bond count')
column header 'o_h': bond count for oxygen-oxygen (c_c, c_h, c_o, o_h together form the 'species bond count')

Rest of the columns: CM or BoB entries
for example:

1) for the file 'propionic_CM_power_1_cutoff_2.5_Log.csv', entries with column header '5' to '39' contains the
35 floating point numbers corresponding to the 35 eigenvectors of the Coulomb matrix (CM). CM contains
all pairwise distance information between the atoms, and for this folder we are dealing with both the species
atoms and the metal atoms. Maximum number of atoms in the species for our dataset is 11. We considered top two
layers of metal surface. Each surface for PW91 calculations contained 12 metal atoms. So, in total (2*12) = 24
metal atoms are considered. And so, total number of atoms for the CM is (11+24) = 35. Pairwise distance measures
between these atoms give a 35 by 35 matrix. 35 sorted eigenvalues of this matrix appear in the columns '5' to '39'.
Pairwise entries were calculated using equation (4) of the paper and for this particular file, 'power' was 1 and
cutoff value was 2.5 angstrom and natural logarithm was applied to the metal atomic numbers.

2) for the file 'propionic_BoB_power_2_cutoff_5.0_Sqrt.csv', entries with column header '5' to '164' contains the
160 floating point numbers corresponding to the Bag-of-bonds (BoB). Maximum number of atoms in a species in
propionic acid reaction mechansim is 11 (max number of C, H, and O are 3, 6, and 2, respectively). Here we are
including the metal surface also (the top two layers). Each layer has 12 metal atoms. 
In total there are 11 + (12*2) = 35 atoms. So we have 35*(35-1)/2 = 595 pairwise distance measures. 
Out of these, all H-H, H-M, and M-M entries are removed. 
Number of H-H entries = 6*(6-1)/2 = 15. 
Number of H-M entries = 6*24 = 144.
Number of M-M entries = 24*(24-1)/2 = 276.
So, total number of entries for BoB = 595 - 15 - 144 - 276 = 160.
These 160 values appear in the columns '5' to '164'.
Pairwise entries were calculated using equation (4) of the paper and for this particular file, 'power' was 2 and
cutoff value was 5.0 angstrom and square root was applied to the metal atomic numbers.