Directory structure:
=======================================

Energies
   |        ____ AllEnergies_propionic.csv:  Contains all energies for each species and metal in a list.
   |        |
   |________|
            |
            |___ Energies_in_TableFormat.csv: All energies in a table (2D matrix) format. Transpose of
                                              this was used for descriptor discovery using PCA, varimax.
                                              Contains 26 species that we want to predict + (C,H,O).




InputFiles_CM_BoB_with_BondCounts
    |
    |            _________ CM_BoB_with_MetalExcluded:
    |            |            Coulomb matrix (CM) and Bag-of-bonds (BoB) calculated without considering 
    |            |            the metal surface atoms.
    |            |            Contains 5 files (for powers 1 to 5. ref: eq 4 in paper) each
    |____________|            for Bag-of Bonds (BoB) with bond counts and metal descriptors  
                 |            and for Coulomb Matrix (CM) with bond counts and metal descriptors.
                 |            For details on the files, please read the readme txt inside that folder.
                 |
                 |
                 |________ CM_BoB_with_MetalIncluded:
                              Coulomb matrix (CM) and Bag-of-bonds (BoB) calculated considering both the
                              species and metal surface atoms.
                              Contains 80 files (for all combinations for power 1 to 5, cutoff values 
                              from 2.5 angstrom to 6.0 angstrom with 0.5 angstrom intervals, and either 
                              natural log or Sqrt applied to the metal atomic numbers; ref: eq 4 in paper)
                              for Bag-of-Bonds (BoB) and Coulomb matrix (CM) each. In addition to the CM
                              or BoB entries, bond counts and metal descriptors are also included.
                              For details on the files, please read the readme txt inside that folder.
                            


LinearScalingPlots_for_singleDescriptors
    |
    |
    |____________ 6 subfolders for 6 descriptors (C, H, O, CO, OH, CHCHCO).
                  Each subfolder contains 29 png file in name format: plot_{speciesName}.png.
                                  Each png file is a plot of that species' energy for different metals
                                  against the descriptor energies for the metals.


OutputFiles
   |              ______ Prediction_across_metals (LeaveOneOut): 
   |              |      please see readMe txt inside the folder for details.
   |______________|
                  |
                  |_____ Prediction_across_species_and_metals (random_predictions):
                         please see readMe txt inside the folder for details.