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

1) for the file 'propionic_CM_exclMetals_power_1.csv', entries with column header '5' to '15' contains the
11 floating point numbers corresponding to the 11 eigenvectors of the Coulomb matrix (CM). As CM contains
all pairwise distance information between the atoms, and for this folder we are dealing with only the species
atoms (excluding the metal surface atoms), we have an 11 by 11 matrix (as maximum number of atoms in a species
in propionic acid reaction mechanism is 11).

2) for the file 'propionic_BoB_exclMetals_power_1.csv', entries with column header '5' to '44' contains the
40 floating point numbers corresponding to the Bag-of-bonds (BoB). Maximum number of atoms in a species in
propionic acid reaction mechansim is 11 (max number of C, H, and O are 3, 6, and 2, respectively). 
So we have 11*(11-1)/2 = 55 pairwise distance measures. Out of these, all H-H entries are removed. Number of
H-H entries are 6*(6-1)/2 = 15. So, at the end, we have (55-15) = 40 long vector for BoB.